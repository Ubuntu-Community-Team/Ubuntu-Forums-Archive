---
title: "BUG: soft lockup detected on CPU#0"
date: 2008-03-13
forum: General Help
---

### Post by pbatt on 2008-03-13
I have a problem with ubuntu server 6.06 on a Pentium III desktop system. During fsck of one of the disks there is a 

BUG: soft lockup detected on CPU#0

and the the OS stops. Only Ctrl-Alt-Del will bring it back to life. From what I fount on the internet others seem to have had something similar, related to a wireless device on notebooks. However, I have no wireless, and it's a desktop machine. And it's only happening durung fsck, be it forced during startup or done from the tty. 

Could someone tell me where to look for a patch or a workaround? 

Thank you, Paul

---

### Post by kevinfarrugia on 2008-04-12
Same thing happens to me.  I log in and everything is fine, then after a minute or even a bit less the mouse and system lock up, then when it comes back the mouse will lag around the screen.  The graphs on the system monitor don't update during the lock up either.  When I restart and the system is shutting down I get an error that says:
```
1899.031147 BUG: Soft lockup - CPU #0 stuck for 11s! [swapper: (*didn't get this part down*)]
```

I'm using a desktop, it has an AMD Athlon 64 and I am using a wireless card (Linksys WUSB54G v4 -- I'm using the rt2x00 drivers since the default drivers didn't work very well at all).  This is on Hardy, it works perfectly fine with the kernel 2.6.24-12-generic, but it does this with the 2.6.24-15-generic kernel that it upgraded too.  I haven't yet rebooted to try the -16 that it just updated to.

Oh, and the driver version if it has anything to do with it: rt2570-cvs-2008040719.  It might not necessarily be this driver that causes it because it happened with th default drivers it used.

This stuff should've been in [here]("http://ubuntuforums.org/forumdisplay.php?f=305"), but too late and I can't delete this... oops

---

