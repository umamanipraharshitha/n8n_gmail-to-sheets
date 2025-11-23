
# 📧 Gmail → Google Sheets Automation (n8n)

This project automates the process of reading Gmail messages and saving them into a Google Sheet using **n8n Workflow Automation**.  
It filters emails based on keywords like **course**, **internship**, and **offer**, and then appends the details to Google Sheets.

---

## 🚀 Features

- ⏱️ Polls Gmail every minute  
- 🔍 Filters emails by subject (course, internship, offer)  
- 📄 Extracts:
  - From  
  - Subject  
  - Snippet  
  - Date (converted from Gmail internal timestamp)  
  - Unique Gmail message ID  
- 📝 Appends or updates rows in Google Sheets  
- 🔁 Prevents duplicate entries using Gmail message ID  
- 🔒 Secure — no credentials included in workflow file  

---

## 📂 Project Structure

```

n8n_gmail-to-sheets/
├── workflow.json       # n8n workflow export
└── README.md           # Project documentation

````

---

## 🖼️ Workflow Screenshot

![Workflow Screenshot](https://github.com/umamanipraharshitha/n8n_gmail-to-sheets/blob/main/Screenshot%202025-11-23%20153918.png)

---

## 🧠 How It Works

1. **Gmail Trigger Node**  
   - Checks Gmail every minute  
   - Fetches messages from Inbox  

2. **IF Node**  
   - Filters messages containing:  
     - "course"  
     - "internship"  
     - "offer"  

3. **Google Sheets Node**  
   - Appends or updates a row  
   - Uses **Gmail Message ID** as a unique identifier  
   - Inserts:
     - Sender  
     - Subject  
     - Snippet  
     - Converted date  
     - ID  

---

## 🛠️ How to Use This Workflow

### 1️⃣ Import the Workflow  
In n8n → **Import from file** → select `workflow.json`.

### 2️⃣ Set Up Credentials  
- Add Gmail OAuth2 credentials  
- Add Google Sheets OAuth2 credentials  

### 3️⃣ Update Your Google Sheet  
Update the spreadsheet URL in the Google Sheets node.

### 4️⃣ Activate Workflow  
Click **Activate** to start automation.

---

## 🗄️ Date Conversion Used

This expression converts Gmail's timestamp to readable format:

```js
{{ new Date(Number($json.internalDate)).toLocaleString("en-IN") }}
````

---

## 💡 Why This Automation?

This workflow helps collect important emails like internships, offers, or course-related messages and logs them neatly into a spreadsheet for tracking.

---

## 📌 Requirements

* n8n (cloud or local)
* A Google account with Gmail + Google Sheets access
* OAuth2 credentials for both services

