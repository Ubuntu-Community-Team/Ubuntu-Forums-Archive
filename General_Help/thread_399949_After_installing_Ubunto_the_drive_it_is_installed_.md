---
title: "After installing Ubunto the drive it is installed on is not recognized by Windows"
date: 2007-04-02
forum: General Help
---

### Post by darylikt on 2007-04-02
I Installed Ubunto on my system on my second hard drive, setting GRUB to boot from the first drive, which windows is installed on. When I am in Linux(Ubunto) I can see all of the files on the Windows partition that Ubunto is installed on, but when I boot into windows it does not show the drive or windows partition on the drive Ubunto is installed on. There are programs and files on that drive I would still like to use while in windows. Is there a way to regain access and use of these files, and still have Linux installed on that drive?

---

### Post by ebozzz on 2007-04-02
I'm not sure about going from Windows to Ubuntu but it is possible to read/write to a NTFS or FAT32 from Ubuntu.

---

### Post by dcstar on 2007-04-03
> **darylikt said:**
> I Installed Ubunto on my system on my second hard drive, setting GRUB to boot from the first drive, which windows is installed on. When I am in Linux(Ubunto) I can see all of the files on the Windows partition that Ubunto is installed on, but when I boot into windows it does not show the drive or windows partition on the drive Ubunto is installed on. There are programs and files on that drive I would still like to use while in windows. Is there a way to regain access and use of these files, and still have Linux installed on that drive?

You would need to install a Windows EXT2/3 driver to access the Linux drive (I seem to recall something like this mentioned before, do a search for it).

---

### Post by darylikt on 2007-04-03
Thank you very much dcstar. That solved the problem and quickly and much easier than I expected. You reply is much appreciated.

---

