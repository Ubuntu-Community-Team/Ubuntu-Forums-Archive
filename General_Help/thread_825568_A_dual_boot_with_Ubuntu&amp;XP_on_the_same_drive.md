---
title: "A dual boot with Ubuntu&amp;XP on the same drive"
date: 2008-06-11
forum: General Help
---

### Post by Aukikco on 2008-06-11
I just managed to get Ubuntu working for the first time.

I have 3 HD's. They are divided as follows:

1) Four partitions: First Ubuntu, second Ubuntu-swap, third Windows XP, fourth NTFS data partition
2) NTFS data partition
3) NTFS data partition (with a temporary installation of XP)

After some tuning, I got the GRUB working so that I can start Ubuntu. However, the option to start XP runs the XP installation on the third HD. I would like it to run the XP installation on the first HD.


My menu.lst file includes the following:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa76497a-3de1-49c7-b0ad-bac89e45f574 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa76497a-3de1-49c7-b0ad-bac89e45f574 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Xiong Chiamiov on 2008-06-11
Currently, your main Ubuntu option is booting off of the first hard drive, and the other two Ubuntu options are booting off the 3rd.  Windows is booting off of the 2nd.

Can you please post the output of 
```

sudo fdisk -l

```

---

### Post by Aukikco on 2008-06-11
> **Xiong Chiamiov said:**
> Currently, your main Ubuntu option is booting off of the first hard drive, and the other two Ubuntu options are booting off the 3rd.  Windows is booting off of the 2nd.
Yeah, the two other ubuntus boot from the third 'cause I just manually edited the normal Ubuntu boot options, hadn't gotten to the other two yet.

Also, the HD order I gave before probably wansn't correct, due to my confusion of the order - BIOS sees the order different from the fdisk -l command, and also GRUB seems to think that the linux HD is 0 while fdisk now sees it as the third one. Very confusing :D

> 
Can you please post the output of 
```

sudo fdisk -l

```

```
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ad9c8c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15017   120624021   42  SFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80b4ab48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde9ede9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1669    13406211   83  Linux
/dev/sdc2            1670        1912     1951897+  82  Linux swap / Solaris
/dev/sdc3   *        1913        3824    15358140    7  HPFS/NTFS
/dev/sdc4            3825       30401   213479752+   7  HPFS/NTFS

```
Very strange... the device sda1 shouldn't have the boot * at all. Also, sdc1 had it before but apparently no longer. Originally, I manually edited sdc1 to have the *, but now it's apparently moved to sdc3 (which is the windows partition I want to use in the GRUB loader).

---

### Post by neilneil2000 on 2008-06-11
As I recall, grub doesn't neccesarily see the hard drives in the same order as fdisk does.  This is why sometimes even fresh installations look to the wrong disk at boot time.

I would suggest the following:

1. When the grub menu loads select the windows menu item
2. Go into edit mode (the key to press is listed at the bottom of the screen)
3. Remove the map (hdx) (hdy) lines
4. Alter the root(hd1,0) to be something else (hd3,0)
5. hit b (i think) to boot
6. If it doesn't work, try another address.
7. Once you know which commands work, edit /boot/grub/menu.lst with the new info.

Let me know how you get on

---

### Post by didac on 2008-06-11
If your Ubuntu partition can boot with root (hd0,0), which is odd, Ubuntu being in (hd2,0), just try changing the Windows line in menu.lst to root (hd0,2) The two map lines shouldn't then be there.

---

### Post by Aukikco on 2008-06-11
> **neilneil2000 said:**
> 
1. When the grub menu loads select the windows menu item
2. Go into edit mode (the key to press is listed at the bottom of the screen)
3. Remove the map (hdx) (hdy) lines
4. Alter the root(hd1,0) to be something else (hd3,0)

Am I misunderstanding something when I think that it should be 0,x since the linux partition is 0,0?

Well, I'll try.

---

### Post by Aukikco on 2008-06-11
hd0,2 seems to be correct, but I end up with this error: "NTLDR is missing, press ctrl+alt+del to reboot".

---

### Post by didac on 2008-06-11
> **Aukikco said:**
> hd0,2 seems to be correct, but I end up with this error: "NTLDR is missing, press ctrl+alt+del to reboot".

We are on the right track now, but there have been a change in partition numbers and Windows is confused. Did you remove the map lines? If you did, put them back again and try. If you didn't, remove them.

---

### Post by Aukikco on 2008-06-11
> **didac said:**
> We are on the right track now, but there have been a change in partition numbers and Windows is confused. Did you remove the map lines? If you did, put them back again and try. If you didn't, remove them.
I think I have tried both ways, but I can try again... Probably it isn't that.

Windows was installed first - could it be that the Ubuntu installation has simply broken the Windows partition boot section? I read somewhere that Windows wants to be directly in the first part of a HD... is this true?

---

### Post by Aukikco on 2008-06-11
I tried root (hd0,2) with the map lines intact. It gave me "Starting up..." and got stuck there, without the NTLDR error. If I understand the map lines correctly, they switch hd's 0<->1? I think it also gave that same "Starting up"-error when I switched root to (hd2,0).

I checked from BIOS: The drive order there is
1) The drive with Ubuntu&Windows
2) The NTFS partition with the temporary XP
3) The NTFS data partition

I don't know if this is important, but it probably doesn't hurt to have the info...
edit: So BIOS seems to agree with GRUB, but fdisk disagrees.

---

### Post by MariusSilverwolf on 2008-06-11
> **Aukikco said:**
> hd0,2 seems to be correct, but I end up with this error: "NTLDR is missing, press ctrl+alt+del to reboot".

If you have your XP CD, that can be recovered.

First, visit [this site]("http://icrontic.com/articles/repair_windows_xp") and follow the procedure there.  You'll rebuild the boot configuration for XP through that process.

After you reboot, you may find that GRUB has been overwritten (not certain, I've not tested the procedure on multi-boot systems).  If you do, follow the procedure rajj lists in [this thread]("http://ubuntuforums.org/showthread.php?t=820706") and you should be golden.

---

### Post by didac on 2008-06-11
Windows believes it is the first partition and doesn't find NTLDR. Remove the map lines, open your Windows partition in Nautilus. You'll see a file called boot.ini Open it and check if you have a line like this:

```

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
```

Change it to:

```
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional"
```

Close and save changes. It should do the trick. If things come to the worst and you get fed up, boot from your windows installation CD. Go to console, not to installation and type "fixmbr" Now you have lost GRUB and you won't be able to boot into Ubuntu. With the LiveCD you should be able to reinstall GRUB.

For more information on this:

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)
[http://ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)
[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by Aukikco on 2008-06-11
I realized that the Windows installation was, for some reason, completely missing the file boot.ini, as well as the other files normally found in the root of a Windows partition. So, I copied the files from the other XP drive and edited the boot.ini file as proposed. Voila, it's working now.

Is there some problem with this method? It seemed to work fluently.

---

### Post by MariusSilverwolf on 2008-06-11
> **Aukikco said:**
> I realized that the Windows installation was, for some reason, completely missing the file boot.ini, as well as the other files normally found in the root of a Windows partition. So, I copied the files from the other XP drive and edited the boot.ini file as proposed. Voila, it's working now.

Is there some problem with this method? It seemed to work fluently.

No problems whatsoever.  You're up, aren't you?  Windows and Ubuntu both load?  Everybody's happy?

Glad you got it worked out.

---

### Post by Snorlaxxx on 2008-06-18
I'm having kind of the same problem, I want to remove my Windows installation, but it still kind of frightens me to push the button. I'm on a Laptop with two internal HD's, one of which is an entire NFTS disk, while the other has a partition NFTS and EXT3 on it, including the swap.

My ```
sudo fdisk -l
```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x6b828565

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        4852    38973658+   7  HPFS/NTFS
/dev/sda2            4853        9703    38965657+   f  W95 Uitgeb. (LBA)
/dev/sda4            9704        9729      208845   82  Linux wisselgeheugen
/dev/sda5            4853        7413    20571201    7  HPFS/NTFS
/dev/sda6            8536        9703     9381928+  83  Linux
```

What should I do?

---

