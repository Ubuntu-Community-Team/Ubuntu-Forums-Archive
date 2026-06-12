---
title: "Need Help! Problem with MySQL"
date: 2008-02-29
forum: General Help
---

### Post by varunrai on 2008-02-29
Hi everyone,

I recently installed the MySqlServer 5.0 and also downloaded the mysql-gui-tools_5.0,mysql-administrator_5.0,mysql-query-browser. All these files were downloaded from mysql.com and the format was rpm.

I then used alien to convert the rpm files to deb. And installed them. I am able to install all of them. Able to see the icons under Development. But when I click on it to open. A small label comes on the task bar with a timer and then disappears after few seconds. But does not run either the MySql Administrator tools or Query Browser.

I am using Kubuntu 7.10.

Need help!

Thanks

Varun

---

### Post by kesman on 2008-02-29
Why didn't you install mysql from add/remove programs?

---

### Post by varunrai on 2008-02-29
I didn realise it was there. But since i checked in add/remove the option is checked but still to be sure I uninstalled it and reinstalling it again.

---

### Post by kesman on 2008-02-29
That may not solve the problem. Go to synaptic package manager, it's somewhere under system menu. In there, find all mysql packages and mark them as "completely removed". This way all the configuration files are removed also, and the package manager's cache cleared so that when you reinstall the packages, they really are downloaded from the ubuntu repository and replace the malicious ones you created with alien.

---

