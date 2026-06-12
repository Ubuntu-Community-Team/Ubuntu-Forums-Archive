---
title: "What's the proper procedure for finding errors?"
date: 2007-11-08
forum: General Help
---

### Post by whatisdot on 2007-11-08
Hello everyone,

I have been wrestling with some errors in Ubuntu which led me to this question:
What is the 'best' procedure for finding/detecting errors?  Let's assume I have a basic knowledge about how this system works, and I want to see if everything is working correctly.  I know that one of the strengths of Linux is the logging ability.  What logs do I want to check?

Some areas I might want to check for errors are:
-Hardware setup/recognition
-Startup
-video and sound

For example, on startup I see at the top of the screen "PCI error: somethingorother not allocated ..." but I can't freeze the screen to see what it says.  How may of these types of messages might I be missing?  If I wanted to iron out all of the wrinkles in my system, how would I go about doing that?

Thanks in advance!  :)

---

### Post by Maestro23 on 2007-11-08
Here's a great doc on System Logs to get you started: [https://help.ubuntu.com/community/LinuxLogFiles?highlight=%28Log%29%7C%28files%29](https://help.ubuntu.com/community/LinuxLogFiles?highlight=%28Log%29%7C%28files%29)

---

### Post by PointyWombat on 2007-11-08
**/var/log/messages** is where to initially look for error,  then log files which may relate to specific software you have. Check /etc/syslog.conf for other system facility related log files.

PointyWombat

---

