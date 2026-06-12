---
title: "Adding a SATA HDD With Existing Data"
date: 2007-12-25
forum: General Help
---

### Post by NerfSmurf on 2007-12-25
Hello, 

Um, I myself am a Windows XP person but something happened and well, my XP is not working at all, so I decided to dig up my old Bigfoot HDD, (a huge (physically) hardrive) and put Linux on it, So i went to download Linux and what i find out is that there are different versions or "Distros" So I just downloaded Ubuntu. Anyway, the only operating system on this PC is Ubuntu. I had a second 250GB WD SATA hard drive that i used with my XP to add all my major files and It is in NTFS and by what I hear, Linux uses FAT32. Is there a way i can "downgrade" to fat32 without data loss? So far, when i try to mount my sata (by right clicking on the icon), i get an error message like," Cannot mount..." or something along those line. Anyway, my goal is to access the info on my sata hdd without losing any of it. I am highly experienced with the windows line on operating systems, but this is my first time using a operating system without a start menu! I dont understand anything, not even the basic directory structure!

Any help would be great!

---

### Post by LaRoza on 2007-12-25
> **NerfSmurf said:**
> Hello, 

Um, I myself am a Windows XP person but something happened and well, my XP is not working at all, so I decided to dig up my old Bigfoot HDD, (a huge (physically) hardrive) and put Linux on it, So i went to download Linux and what i find out is that there are different versions or "Distros" So I just downloaded Ubuntu. Anyway, the only operating system on this PC is Ubuntu. I had a second 250GB WD SATA hard drive that i used with my XP to add all my major files and It is in NTFS and by what I hear, Linux uses FAT32. Is there a way i can "downgrade" to fat32 without data loss? So far, when i try to mount my sata (by right clicking on the icon), i get an error message like," Cannot mount..." or something along those line. Anyway, my goal is to access the info on my sata hdd without losing any of it. I am highly experienced with the windows line on operating systems, but this is my first time using a operating system without a start menu! I dont understand anything, not even the basic directory structure!

Any help would be great!

Ubuntu can read and write to NTFS.

Linux doesn't use FAT32, but can use it. FAT32 is a bad filesystem, but it is well supported by everything.

KDE uses a "start" menu like menu.

To explain briefly, Linux uses the EXT3 file system usually, and has a simple file hierarchy.

In *nix systems, everything is a file and everything is a file under root "/". If you type ```
ls /
``` (similar to Windows ```
dir c:
```) you will see what is in root.

/  == root
/home == your home directories are in here, you will only have write access to yours, which is /home/username
/media == anything in here is a device or disk, it is a **mountpoint**, where the devices are added to the directory structure
/dev == devices, don't do anything in here!

Unlike Windows, there are no drive letters, and drives are mounted as directories. They can be mounted anywhere, but the usually place is /media and anything mounted (like a flash drive) will appear in your Places menu and on the desktop (in GNOME) although that can be changed.

---

### Post by NerfSmurf on 2007-12-25
Ok thanks, I understand that, and I am glad that you said that linux can understand ntfs. I see my sata HDD under the "Places" left side bar, labled "SATA" (i named it that). but i cant access it. The error says "Unable to mount the volume 'SATA'."

---

### Post by taurus on 2007-12-25
See if you can mount it from a terminal?  Open it and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L, not number 1.

---

### Post by NerfSmurf on 2007-12-25
Thanks for that,
Oh, i found a tutorial on how to do so and in the lines for me to type, they look like:

        # ls /proc/ide

Is the # supposed to be replaced by sudo? I tried it and now I am going places.. BTW, whats sudo? let me see where i can get myself now.

---

### Post by NerfSmurf on 2007-12-25
Hey guys, I got it workin now! Now to get WINE working right, thanks you guys!

---

