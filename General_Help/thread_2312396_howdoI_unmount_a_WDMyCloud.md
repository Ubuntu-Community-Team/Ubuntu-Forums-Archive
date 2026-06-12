---
title: "howdoI unmount a WDMyCloud?"
date: 2016-02-04
forum: General Help
---

### Post by Old Jimma on 2016-02-04
Hi Community:

I followed the instructions at [http://ubuntuforums.org/showthread.php?t=2247237]("http://ubuntuforums.org/showthread.php?t=2247237") to mount a WDMyCloud. They worked very nicely.

Then, I think I made a mistake to mount it at boot. 

I created private and public mountpoints at /   
> 
/mntWD/me
/mntWD/Public


and then added the following lines to my /etc/fstab file
> 
192.168.1.79:/me/me /mntWD/me nfs auto 0 0
192.168.1.79:/me/Public /mntWD/Public nfs auto 0 0


I wanted to stop using the WDMyCloud and removed those lines in my /etc/fstab file..... **BUT IT STILL MOUNTS**.

When I open a command window and ississue a mouunt command, I don't see the mount points.

How do I get that WDMyClound unmounted sto that I can stop using it?

Thanks,
Old Jimma from the Old Country

---

### Post by steeldriver on 2016-02-04
If it's not showing up in the output of the `mount` command, what exactly are you referring to when you say it still mounts? Are you referring to it showing up when you "Browse Network" in the nautilus file manager? If so, my guess would be that the device is advertising itself as a samba or afp share

---

### Post by Old Jimma on 2016-02-04
It shows up in Nautilus and I can still write to the WD device.

For example, in Nautilus compter > WD > me

That's one way I can get to get. Also, the book mark in Nautilus is still there and I can get to it that way, too.

Thanks for your help,
Old Jimma

---

### Post by Vladlenin5000 on 2016-02-04
The bookmark will stay there whether or not it is actually mounted and even if the network share is offline. A bookmark is something that you, the user, explicitly defined and can be delete at any time by you (and only you). Also you still can see it because > the device is advertising itself as a samba or afp share.
Nautilus cannot guess what you want to see or not and magically override what it was designed/programed to do.

---

### Post by Old Jimma on 2016-02-04
Yes, that's right. But I can access the WDMyCloud from the bookmarks.

How do I stop access and safely disconnect the device?

Thanks
Very old wizzened Jimma from the Oldest of the very old Countries

---

### Post by Vladlenin5000 on 2016-02-04
Well, you simply don't click there. Otherwise Nautilus will automatically mount it, by design and for users' convenience.
And - again - if you don't want it there you can remove that bookmark.

---

### Post by Old Jimma on 2016-02-04
Thanks!!!  :d

---

