---
title: "Help with MySql in Ubuntu 18.04 with zoneminder"
date: 2020-05-27
forum: General Help
---

### Post by cancunmanny on 2020-05-27
This is the second time I run into the issue, and last time I had to start with a fresh install of everything so hoping this time I can fix it without having to start all over.

So I have ubuntu desktop 18.04 running zoneminder on the background.  Well here in Mexico we often get power outages.  More often than not the pc reboots without an issue, but twice after a power outage mysql has broken.

I've tried a few generic instructions but can't seem to get anywhere.  When I try to purge mysql I get an error because of zoneminder.  When I install mysql again, i get an error because of zoneminder.  I can't seem to stop zoneminder since I don't think it is running because mysql is not running.

I checked, and I do seem to have the database files.

Any ideas on how I can fix the problem?

---

### Post by cancunmanny on 2020-06-01
bump

---

### Post by The Cog on 2020-06-01
because of zoneminder is rather vague. Can you tell us what the error messages were?

Although, I think the most likely problem is corruption of the database.

---

### Post by cancunmanny on 2020-06-01
I am pretty sure zoneminder itself is not the issue.  I don't think it is a corrupt database.  At this point if I wanted to start a new database I wouldn't be able to.  I can't stop or start mysql.

---

### Post by yancek on 2020-06-02
Well, what happens when you try to start mysql?  Do you get any warning/error messages?  If so, what are they?  Your posts are prettty vague.

---

### Post by cancunmanny on 2020-06-02
manny@MannyMainPC:~$ sudo systemctl status mysql
&#9679; mysql.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)
manny@MannyMainPC:~$ 


manny@MannyMainPC:~$ sudo service mysql start
Failed to start mysql.service: Unit mysql.service is masked.

---

### Post by matigo on 2020-06-03
Yeah, this doesn’t need a reinstallation or anything like that. Try this:

```

sudo rm /lib/systemd/system/mysql.service 
sudo systemctl enable mysql.service
sudo service mysql start

```

The main problem is that masked file in the systemd directory. Once that’s cleared out, you’ll be golden.

---

