---
title: "No updates available until &quot;apt-get update&quot;"
date: 2008-04-15
forum: General Help
---

### Post by ivansf92 on 2008-04-15
I think this might be because I disabled a service that deals with this, but, as the title states, the system tray icon that tells how many updates are available never shows up anymore until I enter the command "sudo apt-get update" in the terminal.

Does anyone know how I can fix this problem?

---

### Post by cm.squared on 2008-04-15
Open up System > Preferences > Sessions.  The program "Update Notifier" should have the box checked to enable that service.

If there is no entry listed as update notifier, you can make your own by clicking the "Add" button, titling it update notifier and adding "update-notifier" (without quotes) to the "Command" field.

---

