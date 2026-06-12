---
title: "Unable to mount parition"
date: 2008-03-11
forum: General Help
---

### Post by SlickTheNick on 2008-03-11
I realize that I posted a similar thread earler, but when I tried the solutions given to me, it doesnt work.

Basically I cant mount one of my paritions, the one with all my data stored on it. This problem arrose after I let windows vista do a disk check, where it then proceeded to make terrible love to my data parition. Heres what I put in the terminal:

```
nick@nick-laptop:~$ sudo mount /media/sda5
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda5 ntfs-3g defaults,force 0 0
nick@nick-laptop:~$ sudo mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.

```

obviously, regular mount didnt work. Tried to do a forced mount, but that didnt work either. Tried it again for the hell of it, heres what I got:

```

nick@nick-laptop:~$ sudo mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
[sudo] password for nick:
fuse: mount failed: Device or resource busy


```

help?

---

### Post by mrsteveman1 on 2008-03-11
Don't mount it for the moment, and run this:

```
sudo ntfsfix /dev/sda5
```

This should set the drive to be checked when windows boots again, which SHOULD fix it.

---

### Post by Rocket2DMn on 2008-03-11
> **mrsteveman1 said:**
> Don't mount it for the moment, and run this:

```
sudo ntfsfix /dev/sda5
```

This should set the drive to be checked when windows boots again, which SHOULD fix it.

If you haven't already, you will need to install *ntfsprogs* to use this program.

```
sudo apt-get install ntfsprogs
```

---

### Post by Shazaam on 2008-03-11
You need to mount your device (sda5) to a mount-point (/media) for it to work.
Try it this way...
```
sudo mount /dev/sda5 /mnt
```
(you can use /media if you want to instead of /mnt).

---

