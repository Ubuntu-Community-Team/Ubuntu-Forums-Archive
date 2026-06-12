---
title: "Shell Scripts"
date: 2008-05-30
forum: General Help
---

### Post by bunoire14 on 2008-05-30
Hey Guys,

Just been reading up on terminal commands and as a practice/tester wrote myself a very simple shell script to automatically update my anti virus definitions. I know the script works because i can manually execute it however i want to acheive 2 things;

1. At the moment i still have to use chmod to be able to run the script is there a way of making this a permanent alteration?

2. Ideally i want the script to run every time i boot, is this possible?

Many thanks for an help,

---

### Post by Monicker on 2008-05-30
I'm not sure what you mean about chmod.  Once you have altered the permissions with chmod they are usually permanent until you change them again.  Where is this script located?

You can use cron to schedule the running of the script.

[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by RATM_Owns on 2008-05-30
For the first, right click, Properties, Permissions and check the box.

For the second, System->Preferences->Sessions and add your script in there.

---

### Post by Monicker on 2008-05-31
If you only need to have it run when you log in, sessions would work.  If it needs to run while the computer is on, whether or not you are actually logged in, crontab is the way to go.

---

