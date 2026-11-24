DAY 5 ASSIGNMENT

TECHNICAL WRITING LAB

STUDENT NAME: HUSSEIN TARAR

EXERCISE A: USER MANUAL PROCEDURE

TASK: SETTING UP A GITHUB REPOSITORY FROM SCRATCH AND MAKING A FIRST COMMIT

1. Introduction

GitHub is an online platform that allows developers to store, manage, and share their programming projects. This procedure explains how beginners can create a GitHub repository, upload project files, and make their first commit.

2. Prerequisites

Before starting, the user needs:

1. A computer with Windows, macOS, or Linux.
2. An active internet connection.
3. A GitHub account.
4. Git installed on the computer.
5. A project folder containing at least one file.
6. Basic knowledge of using Git Bash or a terminal.

3. Step by Step Procedure

Step 1: Open GitHub

Action: Open a web browser and visit https://github.com.

Expected Result: The GitHub homepage appears.

Step 2: Sign in to GitHub

Action: Enter your GitHub username and password.

Expected Result: Your GitHub dashboard appears.

Step 3: Create a New Repository

Action: Click the New Repository button.

Expected Result: The repository creation page appears.

Step 4: Enter the Repository Name

Action: Type my-first-project into the repository name field.

Expected Result: The repository name appears in the form.

Step 5: Create the Repository

Action: Click Create Repository.

Expected Result: A new empty repository is created.

Step 6: Open Git Bash

Action: Open Git Bash on your computer.

Expected Result: A terminal window appears.

Step 7: Navigate to Your Project Folder

Action: Enter the following command.

cd Desktop/my-first-project

Expected Result: Git Bash opens the project directory.

Step 8: Initialize Git

Action: Run the following command.

git init

Expected Result: Git initializes a new local repository.

Step 9: Add Project Files

Action: Run the following command.

git add .

Expected Result: All project files are staged for committing.

Step 10: Make the First Commit

Action: Run the following command.

git commit -m "Initial commit"

Expected Result: Git creates the first commit.

Step 11: Connect the GitHub Repository

Action: Run the following command and replace USERNAME with your GitHub username.

git remote add origin https://github.com/USERNAME/my-first-project.git

Expected Result: Your local repository is connected to GitHub.

Step 12: Push Files to GitHub

Action: Run the following commands.

git branch -M main

git push -u origin main

Expected Result: Your project files appear in your GitHub repository.

4. Screenshot Description

Screenshot 1: GitHub Repository Dashboard

The screenshot should show the repository name, main branch, uploaded project files, and the initial commit message.

5. Troubleshooting

Common Error: Authentication Failed

Problem: GitHub rejects the user's authentication when pushing files.

Solution:

1. Check that the repository URL is correct.
2. Confirm that you are using the correct GitHub account.
3. Authenticate using a browser or Personal Access Token when prompted.

6. Conclusion

Creating a GitHub repository and making the first commit helps developers manage their source code, track changes, and collaborate with other developers. Following these steps allows beginners to upload their first project successfully.


EXERCISE B: API REFERENCE ENTRY

API NAME: CREATE A NEW TASK

1. Overview

The Create Task API allows an authenticated user to create a new task inside a project management application.

Users can provide a task title, description, assignee, due date, and priority level. After successful creation, the API returns the task details and a unique task ID.

2. HTTP Method and Endpoint

HTTP Method: POST

Endpoint: /api/v1/projects/{projectId}/tasks

Content Type: application/json

Authentication: Bearer Token

3. Request Parameters

Path Parameters

Parameter: projectId

Data Type: Integer

Required: Yes

Description: Unique ID of the project where the task will be created.

Query Parameters

No query parameters are required for this endpoint.

Body Parameters

Parameter: title

Data Type: String

Required: Yes

Description: Name of the task.

Parameter: description

Data Type: String

Required: No

Description: Detailed explanation of the task.

Parameter: assigneeId

Data Type: Integer

Required: Yes

Description: ID of the user assigned to the task.

Parameter: dueDate

Data Type: String (Date)

Required: Yes

Description: Task deadline in YYYY-MM-DD format.

Parameter: priority

Data Type: String

Required: Yes

Description: Priority level, which can be low, medium, or high.

4. Required Request Headers

Authorization: Bearer YOUR_ACCESS_TOKEN

Content-Type: application/json

Accept: application/json

The Authorization header contains the user's access token. The Content-Type header specifies that the request body is JSON. The Accept header specifies that the client expects a JSON response.

5. Example Request Body

{
  "title": "Complete Website Design",
  "description": "Design the homepage and dashboard for the project.",
  "assigneeId": 102,
  "dueDate": "2026-12-15",
  "priority": "high"
}

6. Example API Request

POST /api/v1/projects/25/tasks HTTP/1.1

Host: api.example.com

Authorization: Bearer YOUR_ACCESS_TOKEN

Content-Type: application/json

Accept: application/json

Request Body:

{
  "title": "Complete Website Design",
  "description": "Design the homepage and dashboard for the project.",
  "assigneeId": 102,
  "dueDate": "2026-12-15",
  "priority": "high"
}

7. Successful Response

HTTP Status Code: 201 Created

Description: The task was successfully created.

Example Response:

{
  "success": true,
  "message": "Task created successfully.",
  "data": {
    "id": 501,
    "projectId": 25,
    "title": "Complete Website Design",
    "description": "Design the homepage and dashboard for the project.",
    "assigneeId": 102,
    "dueDate": "2026-12-15",
    "priority": "high",
    "status": "pending",
    "createdAt": "2026-11-24T10:30:00Z"
  }
}

8. HTTP Response Codes

201 Created

The task was successfully created.

400 Bad Request

The request contains invalid data or missing required fields.

401 Unauthorized

The authentication token is missing or invalid.

403 Forbidden

The user does not have permission to create tasks in the project.

404 Not Found

The project or assigned user does not exist.

409 Conflict

Task creation conflicts with an existing resource or project constraint.

415 Unsupported Media Type

The request does not use the supported JSON content type.

422 Unprocessable Entity

The request data fails validation, such as an invalid priority or date.

429 Too Many Requests

The user has exceeded the API request limit.

500 Internal Server Error

An unexpected server error occurred.

9. Validation Rules

1. The title must not be empty.
2. The description is optional.
3. The assignee ID must belong to an existing user.
4. The due date must use the YYYY-MM-DD format.
5. Priority must be low, medium, or high.
6. The project ID must belong to an existing project.
7. The user must be authenticated and authorized.

10. Example Error Response

HTTP Status Code: 400 Bad Request

{
  "success": false,
  "message": "Validation failed.",
  "errors": {
    "title": "The title field is required.",
    "priority": "Priority must be low, medium, or high."
  }
}

11. Conclusion

The Create Task API provides a simple and secure way for authenticated users to create tasks in a project management application. It accepts task information in JSON format, validates the submitted information, and returns an appropriate HTTP response.


EXERCISE C: BRIEF TECHNICAL REPORT SECTION

TITLE: TECHNICAL REPORT ON TASK MANAGEMENT API

1. Introduction

This technical report explains the design and functionality of a Task Management API developed for a project management application. The API allows authenticated users to create and manage tasks within their projects.

The main purpose of the API is to make task creation easier, improve project organization, and help users manage their responsibilities effectively.

2. System Design

The Task Management API uses REST architecture and communicates through HTTP requests and JSON data.

The API uses the following endpoint:

POST /api/v1/projects/{projectId}/tasks

Users must provide the required task information, including:

1. Task title.
2. Task description.
3. Assignee ID.
4. Due date.
5. Priority level.

The API supports three priority levels: low, medium, and high.

3. Implementation

The API accepts POST requests containing task information in JSON format.

Example:

{
  "title": "Complete Database Project",
  "description": "Finish the database design and documentation.",
  "assigneeId": 102,
  "dueDate": "2026-12-15",
  "priority": "high"
}

After receiving the request, the system validates the submitted information and checks whether the project and assigned user exist.

If all requirements are satisfied, the system creates the task and returns a successful HTTP 201 Created response.

4. Testing and Results

The API should be tested using different scenarios to ensure that it works correctly.

The following tests are recommended:

1. Submit a valid task and confirm successful creation.
2. Submit a request without a title and check the validation response.
3. Submit an invalid priority level and confirm that the API rejects it.
4. Submit a request without an authentication token and check the unauthorized response.
5. Submit a request using a project ID that does not exist and check the error response.

The expected result is that valid requests create tasks successfully while invalid requests return appropriate error messages.

5. Security Considerations

Security is important when developing a task management application.

The API should:

1. Require authentication using a Bearer Token.
2. Verify user permissions before allowing task creation.
3. Validate all submitted information.
4. Protect sensitive user information.
5. Return appropriate error messages.

These measures help protect project information and prevent unauthorized access.

6. Conclusion

The Task Management API provides an effective way to create and organize tasks in a project management application. Its use of REST architecture, JSON data, authentication, and input validation makes it a practical solution for managing project activities.

Further improvements could include task updates, task deletion, notifications, and progress tracking.


END OF DAY 5 ASSIGNMENT

STUDENT NAME:HUSSEIN TARAR
