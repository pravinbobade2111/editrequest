<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Appointments</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/axios/0.19.2/axios.min.js"></script>
</head>
<body>

<div id="appointmentsList">
    <!-- Appointments will be displayed here -->
</div>

<script>
    // Function to fetch and display appointments
    function fetchAndDisplayAppointments() {
        axios.get('https://crudcrud.com/api/YOUR_CRUDCRUD_API_KEY/appointments')
            .then(response => {
                const appointments = response.data;
                const appointmentsList = document.getElementById('appointmentsList');

                // Clear existing content
                appointmentsList.innerHTML = '';

                // Display appointments
                appointments.forEach(appointment => {
                    const appointmentItem = document.createElement('div');
                    appointmentItem.textContent = `Name: ${appointment.name}, Date: ${appointment.date}`;
                    appointmentsList.appendChild(appointmentItem);
                });
            })
            .catch(error => {
                console.error('Error:', error);
            });
    }

    // Event listener for DOMContentLoaded
    document.addEventListener('DOMContentLoaded', fetchAndDisplayAppointments);
</script>

</body>
</html>
