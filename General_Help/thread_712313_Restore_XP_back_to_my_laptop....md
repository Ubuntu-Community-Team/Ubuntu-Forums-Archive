---
title: "Restore XP back to my laptop..."
date: 2008-03-01
forum: General Help
---

### Post by dabr- on 2008-03-01
Ok,
When I first got Ubuntu (maybe 6 months ago) I didn't know what I was getting in to.
I forgot to create a partition, so I lost the XP part of my laptop. 
I am very happy with Ubuntu, but I would really like to switch back to XP.
I have a copy of XP Professional (Service Pack 1) and I also have an XP Pro Upgrade disk that's SP2.

When I try and enter the disks, they load up, and as soon as I get anywhere the disk tells me my hard drives are not properly installed. I know they are, as Ubuntu runs fine. I really need some help getting this problem solved. 
Thanks,
-dabr-

---

### Post by HuntTheShunt on 2008-03-01
I you had partition magic you could create another partition and dual boot xp or ubuntu.

---

### Post by dabr- on 2008-03-01
where can i get this partition magic?
is it an app for Ubuntu?

---

### Post by ajgreeny on 2008-03-01
I don't know for certain, but I think you could make space on your ubuntu partition using gparted.  Fire up the live CD and go to partition manager and then Resize/Move on the toolbar. Here you can reduce the ubuntu partition size easily.  Don't bother to format the free space, leave that to the XP installer.  Your biggest problem, however will be that grub will be overwritten and you will also have to add windows to the grub menu manually, as it will not be there in your current /boot/grub/menu.lst file.  That is easiest to worry about later once you have grub back on the MBR.  I suspect, however that you may also have problems of UUID changes to your partitions which could mean that the menu.lst file is now incorrect.  Therevmay also be problems if windows is not on the first partition of the disk (not sure about that!)

If you can bear it the best way could in fact be to reinstall windows first on a smaller partition than the whole disk, and get it running OK, then reinstall ubuntu again, but make sure you leave windows on disk this time.

---

### Post by wh33t on 2008-03-01
That's so weird. I've never heard of the windows install reporting that it can't read your harddisks. Usually it just reports there is a disk that has unpartitioned space or something similar because it can't read the Linux File system.

It should give you an option to Delete the linux partition and then you should be left with a bunch of  unpartitioned space.

---

