---
title: "System Restore?"
date: 2005-06-04
forum: General Help
---

### Post by 1337sithlord on 2005-06-04
U all know that little thing winxp can do, where u restore ur system to a previous date?  I could use something like that in ubuntu right about now.  Does hoary hedgehog have a system restore program?  I cant find one but if anyone else can, could they say where it is pl0z? thx

---

### Post by pseudonym on 2005-06-04
Check out this thread - [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087) . Right below yours as I'm typing this ;-) .

You can also try partimage, which basically does the same as what's detailed in the above thread - [www.partimage.org](www.partimage.org) for info . 

If you want to backup your main hard drive it won't make much sense to install partimage on it, as it has to be unmounted when you do the backup. Instead, boot up a live CD which contains it - Knoppix ([www.knoppix.net](www.knoppix.net)) or Linux System Rescue CD ([www.sysrescuecd.org](www.sysrescuecd.org)) are two that come to mind. As far as I know, the Ubuntulive CD doesn't have it.

These methods aren't exactly the same as windows system restore, but they achieve the same purpose - backing up your system (like Norton Ghost, for example). Partimage is excellent, in my opinion. It says that the NTFS support is experimental but I have successfully backed up and restored a winxp partition without problem. I haven't done that with Ubuntu yet, but I guess that says more about Windows than it does Ubuntu. ;-)

---

### Post by poofyhairguy on 2005-06-04
Please don't post questions in howto forum.

---

### Post by 1337sithlord on 2005-06-05
O that was in how-to?  Wow am i absent minded lol.  If its not moved already, plz move it, and do u know if ubuntu has a type of system restore?

---

### Post by Gtaylor on 2005-06-05
> **pseudonym]Check out this thread - [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087) . Right below yours as I'm typing this  said:**
> www.partimage.org[/url] for info . 

If you want to backup your main hard drive it won't make much sense to install partimage on it, as it has to be unmounted when you do the backup. Instead, boot up a live CD which contains it - Knoppix ([www.knoppix.net](www.knoppix.net)) or Linux System Rescue CD ([www.sysrescuecd.org](www.sysrescuecd.org)) are two that come to mind. As far as I know, the Ubuntulive CD doesn't have it.

These methods aren't exactly the same as windows system restore, but they achieve the same purpose - backing up your system (like Norton Ghost, for example). Partimage is excellent, in my opinion. It says that the NTFS support is experimental but I have successfully backed up and restored a winxp partition without problem. I haven't done that with Ubuntu yet, but I guess that says more about Windows than it does Ubuntu. ;-)

This is good advice, do some homework and see if these will work for you.

---

