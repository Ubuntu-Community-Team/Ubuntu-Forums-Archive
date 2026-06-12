---
title: "Grub Showing V17.04 for Booting but 17.10 Installed"
date: 2018-01-12
forum: General Help
---

### Post by Kerry Lange on 2018-01-12
I installed a new BOIS version and when the computer rebooted, grub shows only version 17.04 and I can't log in. This is despite the fact I have been running version 17.10. 17.04 was previously installed on another drive. 

I've tried loading earlier kernels and have also downgraded the BIOS to the earlier version but nothing changes. When I try to log in I enter my password, the screen changes slightly and I'm presented the logon screen again. It loops like that for as many times as I try logging in.

Is there a way to edit the grub options so I might be able to point it at a different drive. It appears to me grub points at the wrong drive (though I may be wrong about that).

Any suggestions?

---

### Post by deadflowr on 2018-01-12
so two different Ubuntu's on two different hard drives?
At the boot screen do you see any other choices beside the 17.04 version?

With the new BIOS it might have just reset the disk order of the hard drives and now has set to load the disk with the 17.04 install on it.
You might double check that the BIOS boot order is set proper so that the disk with 17.10 boots first.

But I'm just randomly spit-balling here, so

---

### Post by Kerry Lange on 2018-01-12
Thanks Deadflowr,

I've tried booting directly to specific disks but I end up looking at exactly the same grub screen. Only when I try booting directly to the old install (17.04) do I end up with an operating system I can use. Unfortunately, everything is setup on 17.10. I don't want to reinstall and end up having to reconfigure and reinstall everything.

I'm about to try the Boot Repair Disk.

I forgot to add that only 17.04 shows in grub.

---

### Post by deadflowr on 2018-01-12
Can you boot into 17.04 but at the login change tty to tty1(or 2, or 3) by invoking the ctrl + alt + F1 to get the console screen?
If you can do that maybe try logging in there and then try running
```
sudo update-grub
```
and see if it finds the 17.10 install.
If it does then try rebooting and see if the 17.10 install shows in grub.

Again, just spit-balling here.

---

### Post by Kerry Lange on 2018-01-12
I will give that a try.

---

### Post by Kerry Lange on 2018-01-12
Weird! When I log into the console, I see it's for version 17.10.

---

### Post by Kerry Lange on 2018-01-12
Weird again! When I try updating grub, it only sees version 17.04.

---

