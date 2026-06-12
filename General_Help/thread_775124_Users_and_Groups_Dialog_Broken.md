---
title: "Users and Groups Dialog Broken"
date: 2008-04-29
forum: General Help
---

### Post by zedmartinez on 2008-04-29
Hello all, I've Googled this everyway I know how and haven't found an answer yet. Whenever I click on the unlock button in the Users and Groups dialog it freezes and tells me "Could not authenticate: An Unexpected error has occurred.

I did dig up enough to find the command line way of opening the dialog, so I tried:

sudo users-admin

which gave me this more detailed error:

** (users-admin:6956): CRITICAL **: Unable to lookup session information for process '6956'

For the sake of helping as much as I can, as near as I can tell it stopped working after installing ntfs-config and using that to have Ubuntu automount my NTFS partitions. I tried using Synaptic and reinstalled gnome-system-tools which I believe is the parent package for that dialog. I'm running Hardy with the x86 architecture. Anyone know what's breaking, or at least how to fix it?

---

### Post by happynix on 2008-05-08
If you are getting to the unlock buttions you might be having a problem with dbus.  ( a race condition w/ dbus and hal) see: [polkit hell]("http://ubuntuforums.org/showthread.php?p=4866207")

basically reschedule hal startup to be after dbus startup.

---

### Post by zedmartinez on 2008-05-08
OK, by running 'ls -al /etc/rc2.d' as suggested on that thread you posted, I can see that hal has a 13 and dbus a 14, so you were correct. However, when I try using bum as the other thread did, dbus reports as 12 and hal 24. How do I manually change the symlink for hal to, say, 15 so it doesn't start before dbus?

---

### Post by alanbrodbeck on 2009-11-04
I, got the same error message when attempting to unlock Users and Groups; and got very similar error with sudo users-admin (and was still unable to edit user settings).
The solution for me was 

Applications => Accessories => Terminal
When the terminal window appears type:
$ passwd

after being prompted to change my password I was able to properly unlock Users and Groups.

---

