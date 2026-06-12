---
title: "Default file permissions"
date: 2013-12-23
forum: General Help
---

### Post by entropy1 on 2013-12-23
What controls the default file permissions that a file is created with?  For example, in .bashrc I have the command umask 077, and when I create files in the terminal with vi, the permissions are -rw------- which is what I want.  But when I create a file with leafpad, or in firefox print to pdf, the files have permissions -rw-r--r--.  How do I make all created files have default permissions -rw------- ?  I am using unity.

---

### Post by bab1 on 2013-12-23
> **entropy1 said:**
> What controls the default file permissions that a file is created with?  For example, in .bashrc I have the command umask 077, and when I create files in the terminal with vi, the permissions are -rw------- which is what I want.  But when I create a file with leafpad, or in firefox print to pdf, the files have permissions -rw-r--r--.  How do I make all created files have default permissions -rw------- ?  I am using unity.

By default all Linux files are created with the default permissions of 666 and all directories are created the default permissions of 777.  As you saw the umask then sets the users preferences.  In Ubuntu 13.10 there is bug in the Upstart script that starts Gnome Nautilus jobs. It sets the umask to 022.  Since any GUI based program in a Unity environment lives with the erroneous settings. You get the permissions 664 even if you set the umask in .bashrc as you have.  The last umask set is the one used.  Since the Upstart job is run when you open the Gui to start Leafpad you get this action.

As an experiment you can try this from the CLI to open Leafpad ```
umask 077;leafpad
```Create a file named umasktest.txt in your home directory.  What are the permissions now?  The last umask always wins.

Luckily there is a repair already available.  See [here]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686") for the answer at post#25 and on.  The package is for Trusty (14.04) and is backwards compatible to 13.10, which is the only version that has this problem.

---

### Post by entropy1 on 2013-12-23
BAB1, when I invoke leafpad from the terminal (which already processed my .bashrc file with the umask 077 command), text files are created with the correct permissions.  Then I installed the repair that you suggested, rebooted, and now when I invoke leafpad from the launcher, it creates files with the permissions I want.  Thank you!

---

### Post by bab1 on 2013-12-23
> **entropy1 said:**
> BAB1, when I invoke leafpad from the terminal (which already processed my .bashrc file with the umask 077 command), text files are created with the correct permissions.  Then I installed the repair that you suggested, rebooted, and now when I invoke leafpad from the launcher, it creates files with the permissions I want.  Thank you!
Glad to hear it worked for you.  Remember that this is only for 13.10.  When you update to 14.04 the routines are part of the regular Upstart package.

---

### Post by entropy1 on 2013-12-24
Thanks for the reminder.

---

