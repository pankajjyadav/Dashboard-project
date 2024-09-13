<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        .container {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            grid-gap: 20px;
            margin: 20px;
        }
        .card {
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        h2 {
            margin-bottom: 20px;
            font-size: 20px;
            color: #333;
        }
        .value {
            font-size: 24px;
            font-weight: bold;
            color: #555;
        }
        .info {
            color: #999;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="card">
            <h2>Children Overview</h2>
            <div>Total: <span id="children-total" class="value"></span></div>
            <div>Active: <span id="children-active" class="value"></span></div>
            <div>Inactive: <span id="children-inactive" class="value"></span></div>
        </div>
        <div class="card">
            <h2>Caregiver Overview</h2>
            <div>Total: <span id="caregiver-total" class="value"></span></div>
            <div>Active: <span id="caregiver-active" class="value"></span></div>
            <div>Inactive: <span id="caregiver-inactive" class="value"></span></div>
        </div>
        <div class="card">
            <h2>Financial Overview</h2>
            <div>Revenue: $<span id="financial-revenue" class="value"></span></div>
            <div>Profit Margin: <span id="financial-profit" class="value"></span></div>
            <div>Expenses: $<span id="financial-expenses" class="value"></span></div>
        </div>
        <div class="card">
            <h2>Attendance</h2>
            <div>Present: <span id="attendance-total" class="value"></span></div>
            <div>On Time: <span id="attendance-on-time" class="value"></span></div>
            <div>Late: <span id="attendance-late" class="value"></span></div>
        </div>
        <div class="card">
            <h2>Enrollments Record</h2>
            <canvas id="enrollmentChart" width="400" height="200"></canvas>
        </div>
    </div>

    <script>
        // Fetching data from the backend
        async function fetchData() {
            // Children Overview
            const childrenOverview = await fetch('/api/children_overview').then(res => res.json());
            document.getElementById('children-total').innerText = childrenOverview.total;
            document.getElementById('children-active').innerText = childrenOverview.active;
            document.getElementById('children-inactive').innerText = childrenOverview.inactive;

            // Caregiver Overview
            const caregiverOverview = await fetch('/api/caregiver_overview').then(res => res.json());
            document.getElementById('caregiver-total').innerText = caregiverOverview.total;
            document.getElementById('caregiver-active').innerText = caregiverOverview.active;
            document.getElementById('caregiver-inactive').innerText = caregiverOverview.inactive;

            // Financial Overview
            const financialOverview = await fetch('/api/financial_overview').then(res => res.json());
            document.getElementById('financial-revenue').innerText = financialOverview.total_revenue;
            document.getElementById('financial-profit').innerText = financialOverview.profit_margin;
            document.getElementById('financial-expenses').innerText = financialOverview.expenses;

            // Attendance Overview
            const attendanceOverview = await fetch('/api/attendance').then(res => res.json());
            document.getElementById('attendance-total').innerText = attendanceOverview.total;
            document.getElementById('attendance-on-time').innerText = attendanceOverview.on_time;
            document.getElementById('attendance-late').innerText = attendanceOverview.late;

            // Enrollments Record (using chart)
            const enrollmentsRecord = await fetch('/api/enrollments_record').then(res => res.json());
            const enrollmentData = enrollmentsRecord.new_enrolls;

            // Draw the chart
            const ctx = document.getElementById('enrollmentChart').getContext('2d');
            const chart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: enrollmentsRecord.months,
                    datasets: [{
                        label: 'Enrollments',
                        data: enrollmentData,
                        backgroundColor: 'rgba(75, 192, 192, 0.2)',
                        borderColor: 'rgba(75, 192, 192, 1)',
                        borderWidth: 1
                    }]
                },
                options: {
                    scales: {
                        y: {
                            beginAtZero: true
                        }
                    }
                }
            });
        }

        fetchData();  // Call the function when the page loads
    </script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</body>
</html>
