# Full Stack Trivia API Web App

This is a second project submission to Udacity's Full Stack Nanodegree Program. This app is a game to answer questions, it also let's a user to add a question and filter the questions by category.

## Getting Started

### Pre-requisites and Local Development

Developers using this project should already have Python3, pip and node installed on their local machines.

### Database Setup

With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:

```bash
psql trivia < trivia.psql
```

#### Backend

From the backend folder run `pip install requirements.txt`. All required packages are included in the requirements file.

To run the application run the following commands:

- For Windows users:

```
set FLASK_APP=flaskr
set FLASK_ENV=development
flask run
```

- For Mac users:

```
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

These commands put the application in development and directs our application to use the `__init__.py` file in our flaskr folder. Working in development mode shows an interactive debugger in the console and restarts the server whenever changes are made.

The application is run on `http://127.0.0.1:5000/` by default and is a proxy in the frontend
configuration.

#### Frontend

From the frontend folder, run the following commands to start the client:

```
npm install // only once to install dependencies
npm start
```

By default, the frontend will run on localhost:3000.

#### Tests

In order to run tests navigate to the backend folder and run the following commands:

```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```

The first time you run the tests, omit the dropdb command.

All tests are kept in that file and should be maintained as updates are made to app functionality.

## API Reference

### Getting Started

- Base URL: At present this app can only be run locally and is not hosted as a base URL. This app is hosted at the default, http://127.0.0.1:5000/
- Authentication: This version of the application does not require authentication or API keys

### Error handling

Errors are returned as JSON objects in the following format:

```
{
    "success": False,
    "error": 400,
    "message": "bad request"
}
```

The API will return three error types when requests fail:

- 400: Bad Request
- 404: Resource Not Found
- 422: Not Processable
- 405: Method Not Allowed

### Endpoint Library

#### GET /categories

General:

- Returns a success value and an object of categories with keys as ids and values as types.

Sample:
`curl http://127.0.0.1:5000/categories`

```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "success": true
}
```

#### GET /questions

General:

- Returns a success value, paginated questions, the length of total questions, current category and an object of categories.
- Results are paginated in groups of 10. Include a request argument to choose page number, starting from 1.

Sample:
`curl http://127.0.0.1:5000/questions`

```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "current_category": null,
  "questions": [
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    }
  ],
  "success": true,
  "total_questions": 18
}
```

#### DELETE /questions/{question_id}

General:

- Deletes the question of the given id if it exists. Returns the id of the deleted question, success value, total questions, and questions list based on current page number to update the frontend.

Sample:
`curl -X DELETE http://127.0.0.1:5000/questions/2`

```
{
  "deleted": 2,
  "questions": [
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    },
    {
      "answer": "Escher",
      "category": 2,
      "difficulty": 1,
      "id": 16,
      "question": "Which Dutch graphic artist–initials M C was a creator of optical illusions?"
    }
  ],
  "success": true,
  "total_questions": 17
}
```

#### POST /questions

General:

- Creates a new question using the submitted question, answer, category and difficulty. Returns the id of the created question, success value, total questions and questions list based on current page number to update the frontend.

Sample:
`curl http://127.0.0.1:5000/questions?page=3 -X POST -H "Content-Type: application/json" -d '{"question":"Who won the Football World Cup in 2018?", "answer":"France", "category": 6, "difficulty": 3}'`

```
{
  "created": 24,
  "questions": [],
  "success": true,
  "total_questions": 18
}

```

#### POST /questions/search

General:

- Searches the questions using the submitted search term. Returns the success value, questions, total questions and the current category.

Sample:
`curl http://127.0.0.1:5000/questions/search -X POST -H "Content-Type: application/json" -d '{"searchTerm": "name"}'`

```
{
  "current_category": null,
  "questions": [
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    }
  ],
  "success": true,
  "total_questions": 2
}
```

#### GET /categories/{category_id}/questions

General:

- Gets the questions based on category. Returns the success value, questions, total questions and category id.

Sample:
`curl http://127.0.0.1:5000/categories/6/questions`

```
{
  "category": 6,
  "questions": [
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "France",
      "category": 6,
      "difficulty": 3,
      "id": 24,
      "question": "Who won the Football World Cup in 2018?"
    }
  ],
  "success": true,
  "total_questions": 3
}
```

#### POST /questions/search

General:

- This request is for playing the quizz game. Using the submitted category and previous questions, returns a random next question and a success value. Note, category is optional, the user may choose to play with all categories.

Sample:
`curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"quiz_category": {"id": 6, "type": "sports"}, "previous_questions": []}'`

```
{
  "question": {
    "answer": "Uruguay",
    "category": 6,
    "difficulty": 4,
    "id": 11,
    "question": "Which country won the first ever soccer World Cup in 1930?"
  },
  "success": true
}
```

## Authors

Udacity project submission teachers.
Student Noyan Alimov
