---
title: "how to stop partitions from mounting automatically?"
date: 2007-06-17
forum: General Help
---

### Post by Serguei_89 on 2007-06-17
Hi, 

I'm trying to speed up my boot time and one of the things it hangs for some time on is mounting and checking my hda1 and hda2 partitions, which are Acer diagnostics and Windows ntfs partitions respectively. I never use them when I'm in ubuntu. Can I command ubuntu to stop worrying about them?

Thank you.

---

### Post by raja on 2007-06-17
I dont think that should be a major factor in your boot time. The disks are only checked once in a while.
Anyway - you can do a couple of things - open /etc/fstab.

Now in the lines corresponding to those drives, you can disable file checking by changing the 6th (usually last) column to '0'. 
But if you dont want them mounted at all - just comment out the lines in fstab and they will not be mounted.

---

### Post by Serguei_89 on 2007-06-17
Thank you. 

I commented out the lines and the effect was noticeable. Ubuntu seems to boot slow.

Before your solution it took 1 minute and 57 seconds to get to the login screen(assuming I press enter in GRUB immideately). Now it takes 1 minute and 36 seconds.
And 2 minutes and 26 seconds to fully load the desktop.

Is that slow? How fast should ubuntu boot on this:?
Acer 5100-5328 Turion X2 TL50 1.6GHZ 1GB Ram 120GB HDD

---

### Post by Fungyo on 2007-06-17
I have a Centrino 2.13ghz (single core), 1gb ram, 80gb 5400rpm hdd

from grub menu to fully loaded desktop in roughly 50secs, 30secs to get to login.

---

### Post by raja on 2007-06-17
Serguei,
Your boot up time does seem to be too long. On my thinkpad with a pentium M and 768 MB RAM, it gets to log in about 50 secs and I have a working desktop in another 10 seconds. I cant see offhand what the problem is for you.

---

