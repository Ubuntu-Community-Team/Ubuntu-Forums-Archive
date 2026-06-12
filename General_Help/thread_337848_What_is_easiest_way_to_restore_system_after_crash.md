---
title: "What is easiest way to restore system after crash?"
date: 2007-01-13
forum: General Help
---

### Post by tc101 on 2007-01-13
I have a friend who is having trouble with his video drivers.  We are both new at this. 

His problem is that in experimenting with the xconfig and other system files to try to fix the video drivers he crashes the system again and again.  Each time he crashes it he has to reinstall if from the DVD.   When it crashes it always goes back to the command prompt.  What is the quickest way to restore the system from that command prompt to its state before he made the changes that caused the crash?  Restoring it from DVD is very time consuming.

---

### Post by milton1 on 2007-01-13
If he can get back to a command line after modifications, you might be able to simply back up any files before changing them, then restore the backup if X goes haywire.

For example:

cp xorg.conf xorg.old

then if you need to restore:

sudo mv xorg.old xorg.conf

---

### Post by Jussi Kukkonen on 2007-01-13
A suggestion for you tc101: Learn to do the changes in command line (like editing xorg.conf with nano). That way, if you get dropped into the console you can just edit xorg.conf like you did while you were in X/Gnome, and undo the modifications. Doing backups like milton1 suggests is a really good idea too.

---

### Post by Stochastic on 2007-01-13
Not sure if your system is broken right now, but if you've forgotten to or didn't backup your xorg.cof file, while you're in the live DVD/CD you can look at the temporary xorg.conf that it is running (the path should be /etc/X11/xorg.conf), mount your broken ubuntu system and copy the temporary xorg.conf into the broken system.  This isn't the best way to go about things but it should work in a pinch.

Here is a guide to working with basic commands in the Terminal:
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

---

### Post by tc101 on 2007-01-13
After moving the backed up file to replace the broken  xorg.conf with this command:

sudo mv xorg.old xorg.conf

Is it then necessary to do anything to get the system to read, load and execute the xorg.conf file, or is that done automatically?

---

### Post by tc101 on 2007-01-13
I am reading the note inside the xorg.conf and it says this, which I don't understand:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Stochastic on 2007-01-13
I always simply reboot ```
sudo init 6
``` after editing my xorg.conf file although that may not be needed.  You could try simply starting gdm ```
gdm
``` as it should look at xorg.conf when it starts its X system.

---

