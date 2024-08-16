function addTask() {
    const taskInput = document.getElementById('taskInput');
    const taskText = taskInput.value.trim();
    if (taskText === '') {
        alert('Please enter a task.');
        return;
    }

    const taskItem = document.createElement('li');
    taskItem.textContent = taskText;
    taskItem.addEventListener('click', function() {
        moveTask(taskItem);
    });

    document.getElementById('pendingList').appendChild(taskItem);
    taskInput.value = '';
}

function moveTask(taskItem) {
    const taskText = taskItem.textContent;
    const newStatus = prompt('Move task to (Pending, In Progress, Completed):').toLowerCase();
    
    if (['pending', 'in progress', 'completed'].includes(newStatus)) {
        taskItem.remove();
        document.getElementById(`${newStatus.replace(' ', '')}List`).appendChild(taskItem);
    } else {
        alert('Invalid status.');
    }
}
