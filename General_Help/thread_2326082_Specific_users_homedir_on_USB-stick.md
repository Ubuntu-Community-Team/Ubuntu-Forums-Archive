---
title: "Specific users homedir on USB-stick?"
date: 2016-05-28
forum: General Help
---

### Post by henrik10 on 2016-05-28
I have a number of Ubuntu-installations: On a desktop computer at work, on a laptop at work and on my private laptop. For a number of (non-technical) reasons I can't avoid using the desktop and the work laptop is to sucky, for me to use it in private. So basically I have to use all three with frequent intervals. Since I'm running Ubuntu (LTS 15.04 to be specific, but I don't think that matters much?) on all three, I would like to have my home-directory available at all three. Basically I see a number of different options:
Using an app like Dropbox to sync it (not to fond of that). Set up my own server, where /home/henrik is syncronized to. Or have my home-directory on an USB-stick I carry around anyway. My immediate preference is towards the latter. But either my search skills suck, or people don't really do that, so I'm asking here, if anyone has some pointers on the best way to do so or some things to watch out for (or alternative suggestions).

Specifically I would like to:
a) be able to mount /home/henrik upon login and unmount it at logout, and
b) have it on an encrypted ext3 or ext4 partition.

Any form help and ideas will be greatly appreciated :)

---

### Post by sudodus on 2016-05-28
At first I intended to suggest a persistent live drive, than I saw that you want an encrypted home, and then I think the best option is an installed system in a portable drive, a fast USB 3 pendrive or an SSD in an external box (with eSATA and/or USB 3 connection).

It is also possible to have a home partiiton like you suggest, but the computers would be crippled without the pendrive. So if you want to run the internal systems in the computers, I would rather suggest that you have a separate **data** partition with the files you want to carry between the computers. That would also make it easy to backup (the files you want to carry between the computers).

You can try an installed system in a fast USB 3 pendrive according to the following links,

[Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Portable installed system booting from UEFI & BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

-o-

Finally, I have to help you with exactly what you ask for ;-)

- Create an ext4 partition on the USB pendrive, that you intend to use. It is best to use a fast USB 3 pendrive with at least 16 GB, even if you have only USB 2 ports on the computers.

- Copy the directory tree in /home from the computer, where it is 'best', to the ext4 partition on the USB pendrive. I would do it with rsync when booted from another system (a live drive) to avoid problems with files that are written to during the process.

```
sudo rsync -Havn /mountpoint/home/ /mountpoint/usb-target
``` dry run, and if it seems correct you run the real thing

```
sudo rsync -Hav /mountpoint/home/ /mountpoint/usb-target
```

with the actual paths. The trailing slash (...home**[COLOR="#FF0000"]/[/COLOR]**) is important as described in ```
man rsync
```

- Run ```
sudo blkid
``` with the USB pendrive inserted to get the UUID of your new home partition

- Edit the file /etc/fstab in each of these computers to add a line specifying how to mount your new home partition. See ```
man fstab
``` for details, something like this but with the correct UUID from **sudo blkid** (without quotes).

```
UUID=2160f8ed-4ab3-4242-b5d6-f87c1967e253 /home           ext4    errors=remount-ro 0       2
```

I did this from memory, I hope I did not forget anything important.

---

### Post by sudodus on 2016-05-28
If you want encryption, I think the easiest and most reliable way is to ***install an encrypted system with encrypted disk, LVM with encryption***.

You can install such a system into a fast USB 3 pendrive.

Encrypted home with cryptswap is tricky, because it wants to hijack existing swap partitions from the installed system. It is bad, if it uses uncrypted swap, and it is bad if it encrypts the swap (and leaves it encrypted) in the host system, which will not be able to use it without the pendrive.

---

