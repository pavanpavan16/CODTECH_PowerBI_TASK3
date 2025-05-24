🔹 TASK 3: Real-Time Dashboard
📌 Project Title:
Real-Time Sales and Activity Dashboard


*COMPANY* : CODTECH IT SOLUTIONS

*NAME* : PAVAN MANUMARRI

*INTERN ID* : CT04DK572

*DOMAIN* : POWER BI

*DURATION* : 4 WEEKS

*MENTOR* : NEELA SANTOSH


📄 Description:
This dashboard is designed to update in real-time using streaming data from a simulated API feed. It displays metrics such as live order tracking, product inventory status, and user activity, updating every few seconds.

📈 Summary:
Real-time monitoring of Temperature and Humidity from Lab1 using a streaming dataset. Updates live on dashboard visuals.

## Why Used: To showcase real-time IoT data ingestion and visualization using Power BI Streaming Dataset.
## Visuals Used: Card KPIs, Line Chart, Gauge, Bar Chart.
## Key Insights: Live environmental metrics for quick monitoring and anomaly detection.

📌 STEP-BY-STEP PROCESS:
🔹 Step 1: Set Up Your Environment
Make sure you have the following:

✅ A Microsoft Power BI account (Pro or higher recommended)

✅ Access to Power BI Service: https://app.powerbi.com

✅ Azure account (if you're using Azure Event Hub / IoT Hub)

✅ Python or Node.js environment (for simulating real-time data)

✅ Postman (for manual API testing if needed)

🔹 Step 2: Create a Streaming Dataset in Power BI
Go to Power BI Service (not Power BI Desktop).

Click on Workspace > Choose your workspace.

Click “+ New” > Streaming dataset.

Select API as the source and click Next.

Define dataset schema, e.g.:

json
Copy
Edit
{
  "timestamp": "DateTime",
  "temperature": "Number",
  "humidity": "Number",
  "location": "Text"
}
Turn “Historic data analysis” to ON (if you want to use report visuals).

Click Create and note the Push URL provided.

🔹 Step 3: Send Streaming Data to Power BI
You have 2 options:

Option A: Use Azure Stream Analytics
Set up an Azure Stream Analytics job.

Input: Azure Event Hub / IoT Hub / Blob

Output: Power BI

Authenticate Power BI when configuring output.

Map fields from Stream Analytics to Power BI dataset.

Option B: Simulate Data using Python (Example)
python
Copy
Edit
import requests
import json
import time
import random
from datetime import datetime

url = 'https://api.powerbi.com/beta/YOUR_WORKSPACE_ID/datasets/YOUR_DATASET_ID/rows?key=YOUR_API_KEY'

while True:
    data = [{
        "timestamp": datetime.utcnow().isoformat(),
        "temperature": round(random.uniform(20.0, 30.0), 2),
        "humidity": round(random.uniform(40.0, 60.0), 2),
        "location": "Lab1"
    }]
    
    response = requests.post(url, headers={'Content-Type': 'application/json'}, data=json.dumps(data))
    print(response.status_code, response.text)
    time.sleep(2)
Make sure to replace the url with the one Power BI gave you.

🔹 Step 4: Build a Live Dashboard in Power BI
Go back to your workspace in Power BI Service.

Click + New Dashboard.

Use the “Add a tile” option.

Choose Custom streaming data as source.

Select the dataset you created earlier.

Pick visual types (line chart, card, gauge, etc.).

Configure fields (e.g., temperature as Y-axis, timestamp as X-axis).

Your dashboard will start updating live as data comes in from your API or stream.

🔹 Step 5: Customize and Format Your Dashboard
Add filters or slicers if you enabled historic analysis.

Use time-based visuals like:

Line charts for trends

Cards for current value

Gauges for threshold alerts

Title and format your visuals to make the dashboard user-friendly.

In Power BI Service, if your report is connected to streaming data (such as via a Streaming Dataset or Push Dataset), downloading a PBIX file is typically not supported. This limitation exists because:
Streaming datasets do not store historical data.
Power BI does not retain the report definition in a format that can be exported as a PBIX when using certain types of streaming data sources.

🛠️ Tools & Technologies Used:
Power BI

Simulated API / Azure Streaming

DAX

Push Datasets

