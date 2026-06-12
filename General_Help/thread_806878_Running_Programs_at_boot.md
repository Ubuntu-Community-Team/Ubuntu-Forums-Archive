---
title: "Running Programs at boot"
date: 2008-05-25
forum: General Help
---

### Post by neilneil2000 on 2008-05-25
I have been having a nightmare trying to get programs to run on boot on my Ubuntu boxes, I am beginning to tear out my hair!

I am currently trying to get Folding@home to start when I boot the machine but to no avail.

I have followed the steps on this site:

[http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux#Running_as_an_Init_Script](http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux#Running_as_an_Init_Script)

When I reboot, I run the following command:

ps -A | grep -i fah

and still nothing

:( :confused:

Please help!

---

### Post by Cerberu2 on 2008-05-25
hi, im new to linux , but when i installed emerald, to make my windows more beutifull.LOL.it dont run at startup, so i went to >>System-preferences-sessions" and added the command to laucnh the app corrctly,and was solved =)

Keep posting.

---

### Post by neilneil2000 on 2008-05-25
I am looking to run the process before log in though.  I have a headless server and so no X session is started and logins only occur via SSH.

I want Folding at home to start as soon as the computer comes to life, not reliant on a log in

---

### Post by neilneil2000 on 2008-05-25
SOLVED!

When I pasted the script into the terminal window it had added some carriage returns which were causing the script to fail.

All done now and happily working!

Yey!

---

