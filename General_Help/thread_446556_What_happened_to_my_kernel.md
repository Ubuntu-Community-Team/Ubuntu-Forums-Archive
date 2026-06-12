---
title: "What happened to my kernel?"
date: 2007-05-17
forum: General Help
---

### Post by stealthisuser on 2007-05-17
Yesterday I connected to the internet with Linux (Ubuntu 6.06) for the first time. I was happily installing a few applications that I needed when the Software Updater popped up with a list of updates for software. Fine, I thought, might as well get the system up to date, so I started the downloads. 

Didn't quite bargain for how long the process was going to take...

It was just coming to an end when the screen saver kicked in. That's annoying. I want to see what's happening, so I gave the mouse a wiggle to get back to the desktop... but the screen saver just froze. Hmmm. Well, it might still be doing it's thing in the background. Better leave it a few minutes and see if anything's happened. Nope. (Bear in mind that this is late at night and I really should be sleeping) Well, what else can I do but switch the machine off and boot up again?

Now my GRUB has new options (before there was the kernel, recovery and mem test):

kernel 2.6.15-28-386
kernel 2.6.15-28-386 (recovery mode)
kernel 2.6.15-23-386
kernel 2.6.15-23-386 (recovery mode)
(and memory test)

Sadly trying to click any of them comes up with the message:

root (hd1,0)
Error 21: selected disk does not exist

I tried running Ubuntu from the live disk but couldn't seem to access any hard drive partitions (first it said it couldn't mount, then after i tried to mount drives in disk manager, the folders never seemed to open).

Does anyone have any ideas about 1) what's happened, 2) whether it can be sorted out without reinstallation, and if not, 3) whether the disk can be accessed to backup a few files before reinstalling?

Thanks in anticipation!

---

### Post by hyperair on 2007-05-17
Next time, switch to a console screen (Ctrl+Alt+Fn where n is an integer from 1 to 6 :p), log in, and type: ```
killall -KILL gnome-screensaver
```

Then switch back to your GUI, using Ctrl + Alt + F7.

If that didn't work, try restarting your X server (Ctrl+Alt+Backspace)

As for your current condition, it seems that your hard disks have been corrupted by the hard off. Try checking your BIOS to see if your hard disk is detected, If it isn't, then, well... I'm not sure what to do at that point, but there was once my DVD Drive acted up. I powered it down completely, waited, and booted back up (cold boot.. I think) and it worked.If that doesn't work, keep restarting and doing whatever you think might help until it comes back xD (or send your machine to a comp shop for repair)

If your hard disks are detected, chances are your file systems are corrupted. In that case, you may have to run fsck on the file systems, from the LiveCD.

---

### Post by stealthisuser on 2007-05-17
thanks for the advice hyperair, will try tonight

---

### Post by stealthisuser on 2007-05-21
It seemed that the GRUB had changed to try to boot from hd(1,0) instead of hd(0,0) and hdb1 instead of hda1. Bizarre! Anyway, should be fixed now.

---

