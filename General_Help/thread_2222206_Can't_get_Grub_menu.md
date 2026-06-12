---
title: "Can't get Grub menu"
date: 2014-05-05
forum: General Help
---

### Post by xeddog on 2014-05-05
I have recently done a fresh install of Ubuntu 14.04 and it is working "as advertised", EXCEPT for the trash.  As I said, this is a fresh install with no dual boot, but the /home directory has been relocated to a second disk in the system.  All that works fine.  But after a week, the trash suddenly displays a bunch of stuff that is months old if not even years old.  I'm guessing it has to be some stuff on the /home disk.  the problem is that I am unable to fix this.  If I select a single item and try to delete it, Ubuntu tells me it can't with no further information.  If I try to empty the trash, there is a dialog that opens and says "Preparing", but it hangs there.  I have left it for hours.

Which brings me to my current problem.  I have been trying to get the grub menu during boot so I can get to the recovery mode and a root prompt to hopefully fix this.  But I can't get the grub2 menu to display.  I have tried pressing several keys during boot including ctrl, esc, space bar, and SHIFT, but no boot menu.  I have tried press/hold the keys, and machine gunning them.   I have edited /etc/default/grub so that  GRUB_HIDDEN_TIMEOUT=5, GRUB_TIMEOUT=5 (and then set this one back to 0 later), and even uncommented GRUB_INIT_TUNE="480 440 1".   Still no grub menu and not even the tone.  Oh, and yes, I ran sudo update-grub after each change.

Any ideas how I can get the menu??

Thanks,

X

---

### Post by oldfred on 2014-05-05
If BIOS, you should be able to hold shift key from BIOS screen until menu appears.
With UEFI you use escape key, but I do not think you hold it.

I have had root trash with files and had to take ownership of that trash to even let me delete with sudo.

        How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by xeddog on 2014-05-05
Oldfred - I had to add a countdown timer "GRUB_HIDDEN_TIMEOUT_QUIET=false" along with GRUB_HIDDEN_TIMEOUT=10 and then update-grub one more time.  With that, I can press Esc when I see the timer and get my menu.  Interestingly, even with specifying a 10 second timer, the first I see it is at 7 seconds remaining.  What happened to my other three seconds?????  Oh well.

Now if I could just find the trash files . . . . .

Thanks,

X

Oh,  I did follow the link you provided regarding Trash files, etc. but it seems pretty old.  It started in 2008 and ended in 2012.  None of the "find" commands for finding trash files yielded any appropriate results.

---

