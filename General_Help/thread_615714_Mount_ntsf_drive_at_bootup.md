---
title: "Mount ntsf drive at bootup"
date: 2007-11-17
forum: General Help
---

### Post by brad1138 on 2007-11-17
I have 2 IDE 40 gig drives, 1 for XP, 1 for Ubuntu and 1 SATA 500 gig for storage, pictures and MP3's etc. The 500 gig was formatted from XP and is NTFS. Gutsy will mount, read and wright fine but I have to click it to mount and enter my password every time I start up. Can I automate this?

Thanks,
Brad

---

### Post by taurus on 2007-11-17
All you need is to add an entry in /etc/fstab to mount it automatically each time you boot Ubuntu.

Edit /etc/fstab:
```
gksudo gedit /etc/fstab
```

An entry for that 500GB, assuming it's /dev/sda1:
```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
If not sure about which partition/drive, post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by brad1138 on 2007-11-17
Ok, I added that line and it was sda1, thank you. Can you tell me what this portion "-3g	defaults,locale=en_US.utf8" of the line means/does? I just like to understand what I am adding.

Thanks,
Brad

---

### Post by HokeyFry on 2007-11-18
defaults is the default set of mount options. i am not sure off the top of my head what this entails, but im sure a quick google of "fstab, defaults" will turn something up.

i am not entirely sure what a locale is, but to the best of my knowledge i think it sets the language for the drive.

ntfs-3g is the type of file system that is being mounted. i know that it is an NTFS filesystem, but ntfs-3g is what linux uses to be able to write as well as read it. basically mounting it as ntfs-3g instead of ntfs saves the hassle of adding "umask=0222" to the options parameter, plus it allows you to have write access to the ntfs partition.

---

