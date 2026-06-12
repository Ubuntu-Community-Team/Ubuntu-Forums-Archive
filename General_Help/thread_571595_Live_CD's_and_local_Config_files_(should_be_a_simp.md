---
title: "Live CD's and local Config files (should be a simple question)"
date: 2007-10-09
forum: General Help
---

### Post by uncleclinto on 2007-10-09
Okay,

I want to fix my screen res.  915resolution doesn't work.  I need to edit my xorg.conf file (scary yes), and I'm afraid of the bouncing "input not supported" message on my monitor.  I don't really want to have to re-build my whole system if that happens.  

Simple Question:  If I need to, can I enter through a live CD and change the copy of Xorg.conf on my local hd??  If the answer is "yes", is there a tricky process I need to know or do I just use nautilus?

Thanks in advance,
Clint

---

### Post by nikhilk on 2007-10-09
If your current xorg.conf file is OK, just make a backup copy of that file and do whatever changes you want to. If the X server gets hosed you can use the backup copy to restore your X.
To answer your question> **uncleclinto said:**
> Simple Question:  If I need to, can I enter through a live CD and change the copy of Xorg.conf on my local hd??  If the answer is "yes", is there a tricky process I need to know or do I just use nautilus?
Yes, you can do it through nautilus. You just need to be aware of the device names of your partitions.

---

### Post by uncleclinto on 2007-10-09
HELP!

Okay, apparently I don't have permission to change this crap from the live cd. I tried it... the x-server won't open, I can't get into my local install.   I can get to a command line on my actual install, but how do I replace my screwed up xorg.conf file with my backup???  Obviously, I can't open gedit. 

Can anyone give me the CLi voodoo to replace my xorg.conf with backup_xorg.conf ---or--- hot to get permission to do this graphically from the live cd.  

Thanks,
Clint

---

### Post by nikhilk on 2007-10-10
Assuming you want to replace "xorg.conf" with "backup_xorg.conf" which are both under "/etc/X11" run
```
cd /etc/X11; rm -f xorg.conf; cp backup_xorg.conf xorg.conf
```

---

### Post by jocko on 2007-10-10
If you want to do it graphically:
```
gksudo nautilus /etc/X11
```will open up a nautilus window with root permissions.

Edit: you say the xserver won't open?
You mean the live cd does not start xorg?
In that case you can't do it graphically...
Or have you by some reason chrooted into your install instead of just mounting the disk?
In that case you can probably not do it graphically...

---

