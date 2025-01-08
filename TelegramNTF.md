### 🛠 How to Set Up Telegram Notifications for Upptime

Get notified instantly via Telegram whenever your monitored sites go down or when everything is running smoothly. Here's how to set it up:

---

### **Step 1: Create a Telegram Bot**

1. Open Telegram and search for [@BotFather](https://t.me/BotFather).
2. Start a chat with BotFather and send the command `/newbot`.
3. Follow the prompts to:
   - Choose a **name** for your bot.
   - Set a **username** (must end with `bot`, e.g., `MyStatusBot`).
4. Once created, BotFather will send you an **API token**. Save it for later use.

---

### **Step 2: Add Your Bot to a Chat**

1. If you want to receive notifications in a group:
   - Create a new Telegram group or use an existing one.
   - Add your bot to the group.
2. Retrieve the **Chat ID**:
   - Send a message to your bot or group.
   - Use this URL to retrieve the Chat ID (replace `<TOKEN>` with your bot’s API token):
     ```
     https://api.telegram.org/bot<TOKEN>/getUpdates
     ```
   - Look for `"chat":{"id":` in the response. This is your Chat ID.

---

### **Step 3: Add Telegram Secrets to GitHub**

1. Go to your repository’s **Settings** → **Secrets and variables** → **Actions**.
2. Add the following secrets:
   - **`TELEGRAM_TOKEN`**: The API token from BotFather.
   - **`TELEGRAM_CHAT_ID`**: The Chat ID where notifications will be sent.

---

### **Step 4: Configure Upptime for Telegram Notifications**

1. Open your `.upptimerc.yml` file.
2. Add the Telegram notification configuration:

   ```yaml
   notifications:
     - type: telegram
       token: ${{ secrets.TELEGRAM_TOKEN }}
       chat_id: ${{ secrets.TELEGRAM_CHAT_ID }}
   ```

---

### **Step 5: Test the Notifications**

1. Push the updated `.upptimerc.yml` file to your repository.
2. Trigger an incident or manually test notifications by running the `Uptime CI` workflow in **GitHub Actions**.

---

### **Example Weekly Report Notification**

Want a weekly status update? Here’s how it looks when configured:

- Add the [Weekly Report Workflow](https://github.com/ruslanlap/upptime_monitoring/blob/main/.github/workflows/weekly-report.yml).
- The bot will send you a summary like this:

  ```
  ✅ Weekly Status Report:
  - Total Monitored Websites: 2
  - Average Uptime: 100%
  - Average Response Time: 72 ms

  👍 All systems are operational. Everything is good!
  ```

---

### **Quick Links**

- **Telegram BotFather**: [Create Your Bot](https://t.me/BotFather)
- **Weekly Report Workflow**: [weekly-report.yml](https://github.com/ruslanlap/upptime_monitoring/blob/main/.github/workflows/weekly-report.yml)
- ![Bot Image](https://github.com/ruslanlap/upptime_monitoring/blob/master/image.png)

Now you’re ready to get real-time updates about your monitored sites directly in Telegram! 🚀
