---
title: "vista corrupted"
date: 2007-11-20
forum: General Help
---

### Post by ishanmahajan on 2007-11-20
Hi
Im a first time linux user...installed fiesty fawn yesterday on my hp laptop. after installing ubuntu vista was workin fine untill the scan disk was run...the scanning process hung up and i turned the power off. now when i start vista a black screen appears after the screen showing 'microsoft          windows' and it hungs up.
Now the main concern is that even the recovery process hangs up!!!. How can i recover vista? Ubuntu is workin fine and i can access the other windows partitions through ubuntu.  
I would really appreciate any help.
Thank you

---

### Post by l33t_3lv3n_g33k on 2007-11-20
That sounds like a corrupted filesystem (probably just the Vista partition).  I haven't played with Vista yet, so I'm not exactly sure what the "recovery process" you mentioned is.  
 
For WinXP, I would try something like this:
[LIST=1]
[*]Boot to Windows XP OS disk
[*]Start the Recovery Console
[*]Run "chkdsk /r" (pretty much the scandisk that hung up on you the first time.  Very import to let it finish.  I've seen these scans take 12+ hours, so it's best to leave it overnight if you have no patience.)
[*]Run "chkdsk /r" again (makes sure everything is cleaned up.  Repeated errors that are "fixed" may indicate a physical problem with your hard drive)
[*]Reboot and start Windows.[/LIST]Again, I'm not sure what this process is like for Vista, but I'm sure it's something hauntingly similar...
 
Good luck!

---

### Post by taurus on 2007-11-20
You are NOT supposed to have Linux scan ntfs/vfat filesystem with fsck!  Look in /etc/fstab and make sure the last two numbers are 0's for your ntfs partition.

```
gksudo gedit /etc/fstab
```

---

### Post by Bablefish on 2007-11-20
I am also on another board and from what I seen it happens a lot. If you want to try Ubuntu on a Vista machine why don't you try Lubi.

---

