---
title: "Back in Time Non Root Doesn't Start"
date: 2013-11-07
forum: General Help
---

### Post by dannymichel on 2013-11-07
I can run the root version just fine.

---

### Post by TheFu on 2013-11-07
Looks like you ran it as root, but with YOUR $HOME set, so all the B-i-T config files are owned by root under your  ~/.config area.  You have 2 choices.  
a) cd ~ ; chown -R {your-user-id}.{your-user-id} ~/.config ;
b) find the back-in-time settings under ~/.config/ and delete them.

Which you should do depends on the settings.

Personally, I like B-i-T only for individual HOME directories, NOT for backing up a system.

---

### Post by dannymichel on 2013-11-07
I've repaired the permissions, but it still uses root's setting when in the non root app. i even completely removed back in time then did a find / -name backintime* and deleted everything then reinstalled back in time and the same thing. root's settings are used by back in time non root. i remember even running both instances at the same time when i was on mint. is this a Ubuntu 13.10 isse?

---

### Post by TheFu on 2013-11-07
Doubtful.
I haven't used B-i-T since July and when I setup to use it as root, I was extremely careful to NEVER, NEVER, NEVER use sudo.
Using any GUI tools with sudo is asking for trouble later.

You are on your own.  Check the environment and file ownerships VERY carefully.  Is B-i-T running from the root crontab?  Does that reset the ownership and permissions?

---

### Post by dannymichel on 2013-11-07
so if i want to run back in time as root from the terminal use 'su'?

---

### Post by dannymichel on 2013-11-07
> **TheFu said:**
> Doubtful.
I haven't used B-i-T since July and when I setup to use it as root, I was extremely careful to NEVER, NEVER, NEVER use sudo.
Using any GUI tools with sudo is asking for trouble later.

You are on your own.  Check the environment and file ownerships VERY carefully.  Is B-i-T running from the root crontab?  Does that reset the ownership and permissions?

Enabling the root account by doing ```
sudo passwd root
```
then loging in to root with ```
su - root
```
and running ```
backintime-gnome
``` as root worked.
By default, when you click back in time (root) in ubuntu 13.10, it opens a terminal and runs it as 'sudo' which was the problem.

---

### Post by TheFu on 2013-11-08
Came across this article today [http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html](http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html) about Timeshift - a similar tool to B-i-T, but designed for the system files and settings. Never used it myself.

---

