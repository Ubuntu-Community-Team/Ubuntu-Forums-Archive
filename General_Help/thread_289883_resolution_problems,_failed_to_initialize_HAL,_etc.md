---
title: "resolution problems, failed to initialize HAL, etc. .. all after automatic update"
date: 2006-10-31
forum: General Help
---

### Post by Memnock on 2006-10-31
You know, I should learn my lesson.  This is the third time this has happened to me with Ubuntu.  Now I love Ubuntu, when it works, it works great, just don't update it. 

This is the third time that I select to update Ubuntu that everything goes haywire on me.  I don't even remember what the automatic updates I installed were, all I know is that my perfectly running system is now a sweet memory.  

After the latest automatic update, the first thing I noticed was that my screensavers were running about as fast as an ant through molasses.   First thing I do is reboot and all hell breaks loose. 

After rebooting, my resolution is shot to 640x480 @ 60hz and I can't change it via the gui.   I had to reconfigure xorg to fix that.  Next thing, when I log in, I get the following message:

"Power Manager

This program cannot start until you start the dbus system service.  It is strongly recommended you reboot your computer after starting messagebus"

Then I get:

"Internal Error

failed to initialize HAL!"

Next I check my services and my zimbra mail server, which had been running flawlessly up until the update all of the sudden will not function properly.  The logger and snmp services will not start.

Is there any way to rollback these miserable updates so I can get my system back to a functioning state?  I tried booting to a previous version of the kernel but the problems persist. 

DAMN UBUNTU AUTOMATIC UPDATES!!  NEVER AGAIN!! ](*,)

---

