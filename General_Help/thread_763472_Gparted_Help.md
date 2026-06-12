---
title: "Gparted Help"
date: 2008-04-23
forum: General Help
---

### Post by Mr.Zim on 2008-04-23
I have a secondary hard drive that is ~40 GiB in size. My library of almost three thousand songs is on that drive. It was originally a full ext3 partition; however, I need to transfer my library to my other Windows PC. I figured I would use Gparted to resize the ext3 partition then make an NTFS partition in the remaining space and copy the music over.

I have managed to get the EXT3 partition sized down and moved to the beginning of the hard drive, but when I right-click and choose New, the option to add an NTFS filesystem is "greyed out" and not clickable. Any help?

---

### Post by Rocket2DMn on 2008-04-23
You may need to go to Application->System Tools->NTFS Configuration Tool and enable writing to external devices.
Alternatively, you can save some trouble and install the driver from [http://fs-driver.org/](http://fs-driver.org/) on your windows machine so you can read/write ext2/3 partitions.  You may need to have the drive plugged in when you install the driver so it will recognize it and assign it a drive letter.

---

### Post by Herman on 2008-04-23
```
sudo apt-get install ntfsprogs
```

---

