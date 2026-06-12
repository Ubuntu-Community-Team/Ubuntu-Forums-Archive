---
title: "How to diagnose a crash ?"
date: 2008-02-26
forum: General Help
---

### Post by linuxvacuum on 2008-02-26
I now have a problem with MythTv. When the server starts a transcode job, my whole system is busy and I can only mouve the mouse cursor, but nothing responds (even ctrl+alt+f1 for a console).
After a couple of minutes, my system is either available or crashes!

What is the location of Ubuntu's important log files to know why a crash happened?

---

### Post by Het Irv on 2008-02-26
I think Log files are stored in /var/crash... but I don't know exactly where the files you are looking for would be in there.

---

### Post by TeoBigusGeekus on 2008-02-26
Make it /var/crash...

---

### Post by azadpanchi on 2008-02-26
Another good place to look is /var/log/ one of the more important one being /var/log/messages

I would try to pinpoint possible programs causing this, once you know that you can look at the log files for the program(s) that maybe having an issue.

---

### Post by Crafty Kisses on 2008-02-26
> **linuxvacuum said:**
> I now have a problem with MythTv. When the server starts a transcode job, my whole system is busy and I can only mouve the mouse cursor, but nothing responds (even ctrl+alt+f1 for a console).
After a couple of minutes, my system is either available or crashes!

What is the location of Ubuntu's important log files to know why a crash happened?

There's a bunch of ways you can diagnose a crash. One of the ways I diagnose a crash is look at my .xorg log file, and to do this, you simply open up your Terminal and enter the following:
```
nano /var/log/Xorg.0.log
```

---

