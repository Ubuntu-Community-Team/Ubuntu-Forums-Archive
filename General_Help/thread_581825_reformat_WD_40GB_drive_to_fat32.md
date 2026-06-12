---
title: "reformat WD 40GB drive to fat32"
date: 2007-10-19
forum: General Help
---

### Post by kditty on 2007-10-19
i have an external 40GB WD HDD. i need to reformat the drive to fat32. before you ask why ill tell you. i have a pioneer dv-400v dvd player that has a USB port, it will play divx files from the usb drive but it has to be fat32 and not ntfs or ext3.

my drive is auto mounted on plugin, and system says its fat32 but it was 'converted' from ntfs to fat32 in windows with partition magic instead of formatted. what should i use to wipe the drive clean and make it fat32 in ubuntu feisty?

---

### Post by cmnorton on 2007-10-19
If this is FAT32, it should show up in Ubuntu by mounting the drive. If you power on the drive after booting, the drive should automount. I formatted a USB pen drive on Windows, and I can read/write it in Ubuntu.

---

### Post by Ek0nomik on 2007-10-19
> **kditty said:**
> i have an external 40GB WD HDD. i need to reformat the drive to fat32. before you ask why ill tell you. i have a pioneer dv-400v dvd player that has a USB port, it will play divx files from the usb drive but it has to be fat32 and not ntfs or ext3.

my drive is auto mounted on plugin, and system says its fat32 but it was 'converted' from ntfs to fat32 in windows with partition magic instead of formatted. what should i use to wipe the drive clean and make it fat32 in ubuntu feisty?

You can use the GNOME Partition Editor.

```
sudo apt-get install gparted
```

---

### Post by kditty on 2007-10-19
> **Ek0nomik said:**
> You can use the GNOME Partition Editor.

```
sudo apt-get install gparted
```

gparted doesnt give any option to format, all the drives are locked

---

### Post by cendant on 2007-10-24
Right-click and "Unmount"

Then you can format as you wish

---

