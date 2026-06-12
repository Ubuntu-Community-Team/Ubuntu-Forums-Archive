---
title: "New hard drive, grub, and error 17"
date: 2007-09-05
forum: General Help
---

### Post by roscowgo on 2007-09-05
Hey folks. I'm almost sure this has been beat to death but i can't seem to find a solution.

I'm a serious newbie, running a dual boot machine.    I'm trying to add a 3rd 20 gig hard drive into my system so I can have a sandbox to test things like vmware and the like without worrying about cooking my installations.

The only way I can get the 3rd drive recognized in my BIOS is using cable select, or making it the only drive.  When I do get it to recognize, it boots to the grub loader, if i select my ubuntu install I get error 17, can't mount this partition.   If i try to go into my xp part i get unsupported exe.

As soon as i unplug the drive it boots just fine.    Please help.     I have no idea what the heck I'm doing.

Oh, I did boot from the live cd  long enough to run gparted and formatted the thing as a fat32 drive.    It should be completely blank.

---

### Post by jamvegan on 2007-09-05
Perhaps when you plug in the new drive it becomes recognized as the first drive?  This is pure guesswork, but I would try connecting the new drive, booting the machine, and editing the grub command for Ubuntu.  These are the steps that I would follow, and I'll use the details of my actual drive layout as examples.  You should, of course, change them as appropriate.

1) Boot machine.

2) In GRUB menu, highlight the Ubuntu entry and type "e".

3) Change the root line from:
```
root  (hd0,7)
```
to:
```
root  (hd1,7)
```

4) Change the kernel line from:
```
kernel  /boot/vmlinuz-2.6.20-16-386 root=/dev/hda8 ...
```
to:
```
kernel  /boot/vmlinuz-2.6.20-16-386 root=/dev/hdb8 ...
```

5) Type "b"

If Ubuntu then booted I would use fdisk to determine what the current drive layout is, and edit /boot/grub/menu.lst appropriately.  If it didn't boot I would try the same steps again with hd2/hdc instead of hd1/hdb.

Hope this helps!

---

