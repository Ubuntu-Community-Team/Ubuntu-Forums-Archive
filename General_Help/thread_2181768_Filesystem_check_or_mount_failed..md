---
title: "Filesystem check or mount failed."
date: 2013-10-19
forum: General Help
---

### Post by revengeska on 2013-10-19
Hello. I've been running the latest version of Xubuntu(before the newest update), I recently had an issue where my update manager showed that I had one update to install, but when I would click "show updates", it would show there's none available. It may or may not have anything to do with my current problem, but I then was told that a new upgrade was available a couple of days later. I chose to upgrade, and it went through the process of downloading and installing. I closed my laptop for the night, but in the morning I looked and the program was frozen and unresponsive halfway through installation.

I killed the process and rebooted the computer. Now I'm getting "Filesystem check or mount failed. A maintenance shell will now be started. CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored", and then I get a root prompt. I'm not really new to Linux but I'm new to these types of issues, I did an fsck and the partitions came back clean. I don't really know where to go from here, would someone be able to help me out?

Thanks!

---

### Post by revengeska on 2013-10-19
Bump, still unresolved.

---

### Post by LIGIER on 2013-10-20
I have exactly the same issue...
And I haven't yet fixed it...

---

### Post by Brad1234 on 2013-10-20
I had a very similar problem:

I have a System76 Lemur Ultra Thin and in attempting to update to Ubuntu 13.10 I happened to (stupidly) close the lid while it was (I think) downloading files. I later shut it down and now it will not restart. I eventually get ...


Filesystem check or mount failed.
A maintenance shell will now be started.
Etc.


But nothing seems to happen.


If I choose the "Advanced options for Ubuntu" line from a "GNU Grub" list of choices, then choose to start in recovery mode and select the "fsck Check all file systems" option I get this error:


/lib/recovery-mode/recovery-menu: line 76: /etc/default/rcS: No such file or directory
fsck from util-linux 2.20.1


I'm kind of a newbie and don't have much clue what I'm doing. Can anyone help?

---

### Post by LIGIER on 2013-10-21
I'll try this w/ my personnal laptop tonight:

Run from maintenance shell one line at a time:
```

mount -o remount,rw /
dpkg --configure -a
mount -o remount,ro /
sync
reboot
```

It comes from this other forum
[http://askubuntu.com/questions/361332/ubuntu-13-04-to-13-10-filesystem-check-or-mount-failed](http://askubuntu.com/questions/361332/ubuntu-13-04-to-13-10-filesystem-check-or-mount-failed)

---

### Post by Brad1234 on 2013-10-21
@LIGIER - Your fix worked! ... pretty much. I completed the first two lines but the third line said that mount / was busy, or something like that, so I rebooted hoping to find / un-busy so I could run the line, but it just booted up fine! I don't know if failing to do the second mount and the sync will cause a problem later but seems to be working okay. Am I in danger of causing further problems if I don't do the last mount and the sync?

---

### Post by revengeska on 2013-10-21
Thanks, LIGIER! It worked for me too. I had the same problem with not being able to complete the second mount. My gut tells me that it may be mounted on the reboot anyways, so it could be unnecessary. As far as the sync goes, I have no idea. Everything appears to be in order, though.

---

### Post by LIGIER on 2013-10-22
You're lucky guys!
For me, it fixed the boot of my laptop but I still have network problem (the ethernet and wifi configuration have been deleted) :(
Anyway, I'm happy to hear that this helps you :)
Apparently, the second mount is unnecessary.

---

