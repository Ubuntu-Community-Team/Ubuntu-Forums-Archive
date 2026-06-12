---
title: "Gparted does not recognize my hard drive? Trying to format."
date: 2013-05-02
forum: General Help
---

### Post by dazapper on 2013-05-02
Hello guys I am trying to format my locked HDD on my laptop, so i am running ubuntu off a USB. So When I got to the disk utility it shows my 160gb hitachi hdd but I have an error formatting it so it does not let me, there is also no option to unmount the drive. I went to gparted to see if I can delete the partitions if there is any (i have no idea since trying to use dban on it didnt work either) and gparted recognizes the 2gb usb but not the Hitachi hard drive.... I am so confused as to why it will not see it. and how I am going to format my hard drive it is just unusable right now....  any help appreciated thanks!

---

### Post by Stonecold1995 on 2013-05-02
Try using cfdisk instead.  Does cfdisk detect the drive?

```
sudo cfdisk
```

---

### Post by oldfred on 2013-05-02
Could be a variety of issues.

Some BIOS have settings to prevent some activity on drive.
If drive was every RAID or Intel SRT.
If you used Windows to create more than 4 partitions it converts to dynamic which does not work with Linux.
If Windows converted a gpt partitioned drive to MBR(msdos) that can cause issues.
If Windows is hibernated, Windows 8 is always hibernated.
If NTFS partition needs chkdsk.

---

