---
title: "Problem with Kubuntu mounting the HDDs"
date: 2006-08-23
forum: General Help
---

### Post by Saoshyant on 2006-08-23
Hello everyone,

I've run into a problem while testing the Kubuntu LiveCD (the Daper Drake). It seems unable to mount any of my hard drives, though it has no problem doing so with my flash disks.

The error is as follows:

Could not mount device.
The reported error was:
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

I'm no Linux wiz, so I don't know exactly what that means. I suppose it's because it's running from CD, and not from the hard drive, but I might be wrong as well, as I've run other LiveCDs before (like SLAX), and they have never caused this problem before. And I'm not going to install Kubuntu until I'm sure that would solve the problem.

My HDDs are both from Seagate, normal ATA, 40 GB each. One of them has a NFTS partition (with Windows), and the other has a FAT32 for normal files.

While I do wish to use Kubuntu as my main OS from now on, I can't take the dive yet if I can't even access my own files. Help is, of course, much appreciated.

---

### Post by Saoshyant on 2006-08-23
Well, it's been three hours now, and while I wouldn't like to be annoying, it's kind of sad no one bothered to even try guessing what happened to me. So, I am bumping the thread before it goes into oblivion, and I hope no one will mind that.

I do know people here aren't my employees, or anything, but I've always heard good things about the Ubuntu community, so don't break my expectations :).

---

### Post by nericreed on 2006-08-24
I am having the same problem exactly,,,hope to see a solution posted

---

### Post by aysiu on 2006-08-24
Assuming /dev/hda1 is the partition in question and that it's NTFS, paste these commands into the terminal: ```
sudo umount /dev/hda1
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```

---

