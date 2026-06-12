---
title: "Growisofs halts system"
date: 2007-11-19
forum: General Help
---

### Post by wiz561 on 2007-11-19
Hi!

I'm running Ubuntu Gutsy on an AMD64 box.  I just got a new DVD burner, and when I try to burn a DVD, it halts the system.  I have to physically unplug it for about 30 seconds, plug it back in, and it pops back up.  Here is the command that I'm using...

root@scooby:/data/burn# growisofs -dvd-compat -Z /dev/dvd=filename.iso 
Executing 'builtin_dd if=filename.iso of=/dev/dvd obs=32k seek=0'
/dev/dvd: pre-formatting blank DVD+RW...
/dev/dvd: "Current Write Speed" is 4.1x1352KBps.

----

After that, the machine just halts.  No panic info or nothing in the logs at all that would give a clue on what's going on.  The only thing I could find is this...

[http://www.linuxquestions.org/questions/linux-software-2/growisofs-cause-system-crash-on-debian-sarge-kernel-2.6.8-377959/](http://www.linuxquestions.org/questions/linux-software-2/growisofs-cause-system-crash-on-debian-sarge-kernel-2.6.8-377959/)

But I don't know if I'm using the scsi or cd version of the ide driver.

Just wondering if anybody has an idea.  I thought it was strange that it wouldn't even give an error!

Thanks!

---

### Post by wiz561 on 2007-11-19
Well, it turns out that if I had mythtv backend running, it caused this crash.  Very strange though...I'm guessing that it locks the dvd drive or something like that.  

Now, to try to figure out why mythtv is doing this and how to prevent this from happening!

EDIT: I thought this fixed it, but it didn't.  :-(  Still is happening....

---

