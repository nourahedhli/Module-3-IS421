# Module-3-IS421
swagger: "2.0"
info:
  description: "This is a sample server School server.  You can find out more about     Swagger at [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).      For this sample, you can use the api key `special-key` to test the authorization     filters."
  version: "1.0.0"
  title: "School"
  termsOfService: "http://swagger.io/terms/"
  contact:
    email: "apiteam@swagger.io"
  license:
    name: "Apache 2.0"
    url: "http://www.apache.org/licenses/LICENSE-2.0.html"
host: "petstore.swagger.io"
basePath: "/v2"
tags:
- name: "User"
  description: "Everything about your User"
  externalDocs:
    description: "Find out more"
    url: "http://swagger.io"
- name: "School"
  description: "Access to School and Students"
- name: "user"
  description: "Operations about user"
  externalDocs:
    description: "Find out more about the School"
    url: "http://swagger.io"
schemes:
- "https"
- "http"
paths:
  /User_management:
    get:
      tags:
      - "user_management"
      summary: "Get Users"
      description: ""
      operationId: "getUser"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - in: "body"
        name: "User"
        description: " A Student in school"
        required: true
        schema:
          type: string
      responses:
        "400":
          description: "Invalid input"
          
  /user_management/put:      
    put:
      tags:
      - "user_management"
      summary: "Update User"
      description: "Updating Users"
      operationId: "updateUser"
      consumes:
      - "application/json"
      - "application/xml"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - in: "body"
        name: "User"
        description: "Student in school"
        required: true
        schema:
          type: string 
      responses:
        "400":
          description: "Invalid User"
     
  /user_management/delete:
    delete:
      tags:
      - "user_management"
      summary: "Delets the (user)"
      description: "Delete one user"
      operationId: "deleteUser"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "User"
        in: "query"
        description: " Part of the school"
        required: true
        type: "string"
        
        
      responses:
        "200":
          description: "successful operation"
          schema:
            type: "string"
            items:
              $ref: "#/definitions/User"
        "400":
          description: "Invalid User"
      
     
  /course_management/course_management:
    get:
      tags:
      - "course_management"
      summary: "Getting the courses"
      description: "Getting all course or only one course"
      operationId: "getCourse"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Course"
        in: "query"
        description: "Courses for Students"
        required: true
        type: "array"
        items:
          type: "string"
        collectionFormat: "multi"
      responses:
        
        "400":
          description: "Invalid Course"
          content: {}
  /course_management/:
    put:
      tags:
      - "course_management"
      summary: "Edditing the Course"
      description: "Edit only one course"
      operationId: "putCourse"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Course"
        in: "query"
        description: "Courses Students take at school"
        required: true
       
      responses:
        "400":
          description: "Invalid Course"
        "404":
          description: "Course not found"
          content: {}
  /course_management/delete:        
    delete:
      tags:
      - "course_management"
      summary: "deleting course"
      description: "delete course"
      operationId: "deleteCourse"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Course"
        in: "query"
        description: "the course at school"
        schema:
        type: "string"
      responses:
        "405":
          description: "Invalid course"
        content: {}
        
     
  /school/course_assignment_management:
    get:
      tags:
      - "course_assignment_management"
      summary: "Get Assignments"
      description: "Getting all the assigements or only one"
      operationId: "getAssignment"
      produces:
      - "application/xml"
      - "application/json"
      parameters: 
      - name: Assignment
        in: query
        description: "Adding he assignment"
        schema:
        type: string
      responses:
        "400":
          description: "Invalid assignment"
          
  /school/:
    put:
      tags:
      - "course_assignment_management"
      summary: "Edditing the assignment"
      description: "Edditing an assignment"
      operationId: "putAssignment"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - in: "query"
        name: "Assignment"
        description: "Assignment putting in a course"
        
        schema:
          type: string
      responses:
       
        "400":
          description: "Invalid assignment"
          content: {}
  /course_assignment_management/delete:
    delete:
      tags:
      - "course_assignment_management"
      summary: "Deleting assignment"
      description: "Deleting an assignment"
      operationId: "deleteAssignment"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Assignment"
        in: "query"
        description: "Deleting an assignment"
        schema:
        type: "integer"
      responses:
       
        "400":
          description: "Invalid ID supplied"
          content: {}
          
  /course_section_management/:
    put:
      tags:
      - "course_section_management"
      summary: "Putting a section"
      description: "edditing a section"
      operationId: "putSection"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - in: "query"
        name: "Section"
        description: "Section where teacher and students enroll in"
        required: true
        schema:
          $ref: "#/definitions/User"
      responses:
      "400":
          description: "Invalid ID supplied"
          content: {}
       
  /course_section_management/delete:
    delete:
      tags:
      - "course_section_management"
      summary: "delelting the section"
      description: "delelting the section"
      operationId: "deleteSection"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - in: "query"
        name: "delete"
        description: "deleting sections"
        required: true
        schema:
          type: "string"
          
      responses:
      "400":
          description: "Invalid Section"
          content: {}
          
  /section_enrollment_management/:
    put:
      tags:
      - "section_enrollment_management"
      summary: "Edditing a section"
      description: "edit section"
      operationId: "putSectionEnrollment"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - in: "query"
        name: "Section"
        description: "A section to assign teachers and students to"
        required: true
        schema:
          type: "string"
          
      responses:
        "400":
          description: "Invalid Section"
          
  /section_enrollment_management:
    delete:
      tags:
      - "section_enrollment_management"
      summary: "Delete Section"
      description: "deleting sections"
      operationId: "deleteSectionEnrollment"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Section"
        in: "query"
        description: "Section to assign teachers and students to "
        required: true
        schema:
        type: "string"
     
      responses:
        "400":
          description: "Invalid section"
          content: {}
          
  /section_assignment_submission_management/:
    get:
      tags:
      - "section_assignment_submission_management"
      summary: "Get Assignment submissions"
      description: "Browse all assignments or getting one "
      operationId: "getAssignementSubmission"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
       - name: "Assignment"
         in: "query"
      responses:
      "400":
          description: "Invalid Submission"
          content: {}
        
  /section_assignment_submission_management/:
    put:
      tags:
      - "section_assignment_submission_management"
      summary: "Edit assignment submission"
      description: "Edit assignment submission"
      operationId: "putAssignmentSubmission"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Assigment"
        in: "query"
        description: "an assignement submission"
        required: true
        type: "string"
      responses:
        
        "400":
          description: "Invalid assignment submission"
          content: {}
   /section_assignment_submission_management/delete:
    delete:
      tags:
      - "section_assignment_submission_management"
      summary: "Delete assignement submission"
      description: "delete submission"
      operationId: "deleteSubmission"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "Assignment"
        in: "query"
        description: "assignment submission"
        required: true
        schema:
         type: "string"
      responses:
        "400":
          description: "Invalid username supplied"
          content: {}
