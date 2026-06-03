Step 1: Open Google Sheets

Go to:

Google Sheets

Sign in with your Google account if needed.

Step 2: Create a New Sheet

Click:

Blank Spreadsheet (+)

A new spreadsheet will open.

Step 3: Name the Spreadsheet

At the top-left, click:

Untitled spreadsheet

Rename it to:

Personal Data

or any name you want.

Step 4: Add Column Headers

In Row 1 enter:

A1	B1	C1
Name	Email	Date

Example:

A1 = Name
B1 = Email
C1 = Date
Step 5: Create Apps Script

From the spreadsheet menu:

Extensions
   ↓
Apps Script

A new tab opens where you'll paste the script code.

function doPost(e) {

  const sheet = SpreadsheetApp.getActiveSpreadsheet()
    .getSheetByName("Personal Data");

  const data = JSON.parse(e.postData.contents);

  sheet.appendRow([
    data.name,
    data.email,
    new Date()
  ]);

  return ContentService
    .createTextOutput(
      JSON.stringify({
        success: true
      })
    )
    .setMimeType(ContentService.MimeType.JSON);
}

Step 6: Verify Sheet Name

At the bottom of the spreadsheet you'll see a tab named:

Sheet1

You can either:

Keep it as Sheet1 and use:
.getSheetByName("Sheet1")

or

Rename it to:
Personal Data

and use:

.getSheetByName("Personal Data")

To rename:

Right-click Sheet1
Click Rename
Enter Personal Data


Deploy Web App

Click:

Deploy
→ New Deployment
→ Web App

Settings:

Execute as: Me

Who has access:
Anyone

Deploy.

Copy the URL:

https://script.google.com/macros/s/XXXXXXXXXXXX/exec
