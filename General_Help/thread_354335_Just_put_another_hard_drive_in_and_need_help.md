---
title: "Just put another hard drive in and need help"
date: 2007-02-05
forum: General Help
---

### Post by jesus5511 on 2007-02-05
Okay, so I bought a new hard drive a couple days ago thinking I wasn't going to use the one that was already in their (which has ubuntu which I am currently am on,) so I did a fresh installation of windows on it, so far everything is working fine, the only problem is due to the size restrains of my case, and the fact that this hard drive was mounted on by the factory and is nearly impossible to get off, I can only get this one to boot first.

All I want to do is make Windows show up on the Grub menu so I can boot it, it's located on my second hard drive (/dev/hdb/.) I thought about just going into the Grub list and adding it in, but than I remembered about the Windows Boot.ini, will that cause any problem? And if so how can I change it?

I was having major problems with getting windows to boot, but now that their on totally different drives and were installed at different times (when they both weren't connected,) I'm pretty positive about it...

Thanks,

---

### Post by comfurtn on 2007-02-05
You can edit the grub menu.lst file by hand, or you can use the method in [this]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub") thread to reinstall grub the easy way.  Reinstalling should automatically detect your separate ubuntu and windows installations and create the menu for you.

give it a try and let us know if you need further instructions.

---

### Post by jesus5511 on 2007-02-05
Ah thanks a lot, FINALLY I get Windows and Ubuntu to coexist peacefully.

The only problem is now that I have to push the exit key about 2 seconds right after I turn in my computer, but I'm sure their is a way to change this?

---

### Post by taurus on 2007-02-05
> **jesus5511 said:**
> 
The only problem is now that I have to push the exit key about 2 seconds right after I turn in my computer, but I'm sure their is a way to change this?

Edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the 
```
timeout      3
```
to
```
timeout     10
```
And you may also want to put a # sign in front of

```
hiddenmenu
```
so you don't have to press the Esc key to see the menu.

---

### Post by jesus5511 on 2007-02-05
Thanks a lot, it worked perfectly. The only problem now is that I cannot access my new hard drive through ubuntu (it doesn't show up on the desktop,) how would I go about being able to view it?

---

### Post by taurus on 2007-02-05
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by jesus5511 on 2007-02-05
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9602    77128033+  83  Linux
/dev/hda2   *        9603        9729     1020127+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       20673   156287848+   7  HPFS/NTFS

---

### Post by taurus on 2007-02-05
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save the change, create a mount point, and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
hd -h
```

---

