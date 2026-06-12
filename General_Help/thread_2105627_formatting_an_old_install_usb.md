---
title: "formatting an old install usb"
date: 2013-01-16
forum: General Help
---

### Post by MasterJimmy on 2013-01-16
i have an old CLEAR internet installation usb drive that i no longer need after uprgading to better equipment. i dont want to throw away the usb as it is a 1gb and would make a good extra thumb drive. how can i do this? ive tried gparted but no luck. i keep getting an error message about the autorun setup not allowing it

---

### Post by Rex Bouwense on 2013-01-16
Just make sure that you umount the flash drive before you try to format.  GParted will not allow you to perform any operation on a mounted partition or device.

---

### Post by MasterJimmy on 2013-04-12
i tried gparted and disc utilities. i keep getting a "cannot perform selected action" message because it is a read only file system. turns out its not that important because the drive is apparently only 65 mb but i still want to do it just because the skill will be useful and its one more thing to learn

---

### Post by Rex Bouwense on 2013-04-12
Master Jimmy, I forgot all about you.  As it turns out I have a very old 64 MB flash drive on hand.
1.  Plug it in.
2.  Open in File Manager (default)
3.  Start Gparted
4.  Select /dev/sdb
5.  Right click on the device and select unmount
6.  Right click on the device again and select format (to the format desired)

Works like a charm.

---

### Post by MasterJimmy on 2013-04-20
i tried it but it will not work. the error message says it is a read only filesystem

---

### Post by CrusaderAD on 2013-04-20
Use startup disk creator to simply format the drive for you.

---

### Post by Rex Bouwense on 2013-04-20
I found this post.  It is ancient and it is talking about KDE system, but I imagine the procedure is the same.  Of course substitute your text editor in lieu of Kate.  Good luck.

Turned on the computer this morning and discovered that I had not posted the web site.  
[http://ubuntuforums.org/showthread.php?p=616396#post616396](http://ubuntuforums.org/showthread.php?p=616396#post616396)
Not sure if this will work because it is with KDE.

---

### Post by fantab on 2013-04-21
Some older USB's had "Write-Protect" switch externally. See if you have one.
What happens if you delete the 'Partition Table' from Gparted?
You can also use a Windows Machine to help yourself if you want to format it as FAT32.

---

