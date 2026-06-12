---
title: "Black screen now every time!"
date: 2008-01-12
forum: General Help
---

### Post by Mark Phelps on 2008-01-12
I double-boot a system with V ista and Ubuntu 7.10.  I've been having problems getting black screens after the login prompt appears, but I've been able to work around those by booting in recovery mode, seeing Ubuntun run fscks on the Linux disks, and then, when I went back to normal boot, everything was OK.

But now, none of that is working.  I've booted into recovery mode several times, and it says the file systems are clean.  But then, when I boot back into normal, I get the login screen for a second, the screen goes black, and nothing happens after that.

So, I'm disgusted -- both because Ubuntu has crapped out on me now, and because I have to resort to going back to Vista to do anything.

I've tried changing the boot parms in menu.lst to noquiet, but there are no error messages produced, and turning off splash.  But nothing works.

I've not changed video drivers or installed anything in months!

I've tried booting from a SystemRescue CD and running fsck on all the Linux drives, but none of them generate any errors, and that doesn't seem to fix the problem anymore.

I read thatn resolution errors in the splash config file can cause problems, but I checked that and it's correct, and I set nosplash in the boot command but it fixed nothing.

Is there anything I can check? If so, how do I do that from a console?

---

### Post by livestockPimp on 2008-01-12
So to clarify it all boots and about the splash screen time/logging into the system the screen goes black.

when you get the black screen can you change to the console via "ctrl + alt + F1" or F2, ect?
if so, can you start x from here? maybe check some error logs in /var/log/syslog...

I have once had a problem where x loads on screen 7 or something and it stays on the first console so i needed to use "ctrl + alt + F7" to get into x...

---

### Post by Mark Phelps on 2008-01-17
Problem appeared to fix itself -- which is why I haven't replied.  Then, last night, it came back!

Three times, the login window appeared, only to vanish before I could enter anything.  Then, I sat with a black screen for several minutes with no apparent disk activity.  I pressed the RESET button each time.  I even rebooted using the Recovery entry, which found no problems in the volumes, and which also did not fix anything.

Then, I remembered what you wrote about using Ctl-Alt-F7, and the next time, I watched the black screen for a few seconds, and pressed Crtl-Alt.  But before I could press F7, the login window suddenly appeared again! Gnome desktop was back and everything was working!  I'm sure this happened before I pressed the F7 key -- which is weird!!

Once back in, I checked the system logs and the Xorg logs, and there were no Errors in either. Their was a Warning about the kernel being tainted, but I've been getting that ever since I've been using the ATI restricted drivers.  And, I've booted hundreds of times without any problems.

I don't want to have to Ctl-Alt-F7 every time I boot Ubuntu, so I will have to go back to googling on Xorg problems to see what else I can do.

This is very frustrating!! At least when Vista crashed, it was a simple process to recover it.  In this case, even booting the recovery version of the kernel does no good.

---

