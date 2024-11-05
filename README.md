<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To-Do List with Remove All</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: linear-gradient(135deg, #6e8efb, #a777e3);
    }
    .todo-container {
      width: 350px;
      background: #d0c4c4;
      border-radius: 12px;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
      padding: 20px;
      text-align: center;
    }
    .add-task-btn {
      width: 100%;
      padding: 10px;
      font-size: 18px;
      color: #fff;
      background-color: #6e8efb;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-bottom: 10px;
      transition: background-color 0.3s;
    }
    .add-task-btn:hover {
      background-color: #5b77d4;
    }
    .task-form {
      display: none;
      margin-bottom: 15px;
      padding: 15px;
      background: #f5f5f5;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    .task-form input,
    .task-form textarea {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border: 1px solid #ddd;
      border-radius: 4px;
      resize: none;
    }
    .task-form button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      font-size: 16px;
      color: #fff;
      background-color: #28a745;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .task-form button:hover {
      background-color: #0c140e;
    }

    .todo-list {
      list-style: none;
      padding: 0;
      margin-top: 15px;
      max-height: 300px;
      overflow-y: auto;
    }
    .todo-item {
      padding: 10px;
      background: #f9f9f9;
      border: 1px solid #ddd;
      border-radius: 8px;
      margin-top: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .remove-btn {
      background-color: #7d2f37;
      color: #fff;
      border: none;
      padding: 6px 10px;
      border-radius: 6px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .remove-btn:hover {
      background-color: #6d4448;
    }

    .remove-all-btn {
      width: 100%;
      padding: 10px;
      font-size: 16px;
      color: #cabebe;
      background-color: #ff4d4d;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 10px;
      transition: background-color 0.3s;
    }
    .remove-all-btn:hover {
      background-color: #e64545;
    }
  </style>
</head>
<body>

  <div class="todo-container">

    <button class="add-task-btn">Add Task</button>

    <div class="task-form">
      <input type="text" id="taskTitle" placeholder="Task Title">
      <textarea id="taskDescription" rows="3" placeholder="Task Description (optional)"></textarea>
      <button onclick="saveTask()">Save Task</button>
    </div>
 
    <ul class="todo-list"></ul>

    <button class="remove-all-btn" onclick="removeAllTasks()">Remove All</button>
  </div>

  <script>
    const addTaskBtn = document.querySelector('.add-task-btn');
    const taskForm = document.querySelector('.task-form');
    const todoList = document.querySelector('.todo-list');
    const removeAllBtn = document.querySelector('.remove-all-btn');


    addTaskBtn.addEventListener('click', () => {
      taskForm.style.display = 'block';
      addTaskBtn.style.display = 'none';
    });
    function saveTask() {
      const taskTitle = document.getElementById('taskTitle').value.trim();
      const taskDescription = document.getElementById('taskDescription').value.trim();

      if (taskTitle) {
        const taskItem = document.createElement('li');
        taskItem.className = 'todo-item';
        taskItem.innerHTML = `
          <div>
            <strong>${taskTitle}</strong>
            <p>${taskDescription}</p>
          </div>
          <button class="remove-btn" onclick="removeTask(this)">Remove</button>
        `;

        todoList.appendChild(taskItem);

        document.getElementById('taskTitle').value = '';
        document.getElementById('taskDescription').value = '';
  
        taskForm.style.display = 'none';
        addTaskBtn.style.display = 'block';
      }
    }

    function removeTask(button) {
      button.parentElement.remove();
    }

    function removeAllTasks() {
      todoList.innerHTML = '';
    }
  </script>

</body>
</html>
