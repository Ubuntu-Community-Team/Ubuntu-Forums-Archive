---
title: "restore package defaults using dpkg-reconfigure and debconf"
date: 2007-02-27
forum: General Help
---

### Post by The_Boss on 2007-02-27
Is there any way to force a package back to it's default configuration settings using dpkg-reconfigure?  I recently changed the priority in debconf to "medium" and started messing around with some package configurations to see what questions have been bypassed with a "high" priority setting.  I'd like to be able to mess around with a packages settings, but have the ability to fall back on the defaults if I change my mind about something later.  Is there a way to do this, without completely reinstalling the package?

---

### Post by Jimmey on 2007-02-27
Usually a program's configuration files are kept it /home/user/.programname - If you rename this folder, the next time you run the program, the defaults should be reset.

---

### Post by The_Boss on 2007-02-27
Thanks.  That works nicely for user apps, but I'm mainly concerned with system wide apps.  

For example, it looks like the default when I first configured the "console-setup" package" using dpkg-reconfigure was to used "Fixed" fonts.  I've changed this to "VGA" fonts.  Later on, I might decide I've screwed something up but forgotten what the original settings were.  I'd like to be able to do something like change my debconf priority to "high" or even "urgent", and then execute a command like "dpkg-reconfigure -a --use-defaults" to reconfigure all packages to their default settings.

---

### Post by The_Boss on 2007-03-07
Perhaps the better question to ask is this:  How does debconf determine what the default answers are for each packages configurations, based on the priority level you set, and does it "stomp" over these values when the user changes them for a package?  

If I knew that, it wouldn't be too difficult to implement a sort of "package config reset" if one doesn't already exist.

---

