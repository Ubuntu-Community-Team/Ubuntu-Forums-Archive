---
title: "[Grub] unable to boot Windows XP"
date: 2007-05-02
forum: General Help
---

### Post by lode on 2007-05-02
Hi there. 

First off, sorry for my not-so-good English, I'll do my best being as understandable as possible.
Second off: I've got a problem with booting my Windows XP installation.

Yesterday I freshly installed Windows XP (pro) onto my computer, working perfectly. Later I installed Ubuntu (7.04). Windows was installed onto a SATA hard drive, Ubuntu onto another ATA hard drive.

Because Grub didn't seem to find the Windows installation, I manually edited Grub's menu.lst, and added (after many trials, more errors and lots of Googling) the following entry for Windows XP:

title      Windows XP
root      (hd1,0)
savedefault
makeactive
map     (hd0) (hd1)
map     (hd1) (hd0)
chainloader +1

Now Grub displays Windows, but when attempting to boot it, I get the following (Windows) error (I'm sure it's a Windows error, since it's originally displayed in the Windows OS language -- Dutch --, and Ubuntu and everything else is in English):

NTLDR is missing. Press CTRL+ALT+DELETE to restart.

Attempting to solve this NTLDR problem, I followed the steps found on this webpage: [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm) (assuming that `3. Corrupt NTLDR and/or NTDETECT.COM file.' was the problem I was coping with -- I do not think any other option could be the case here, since the Windows install was brand new and working perfectly before I installed Ubuntu), ergo, replacing the files ntldr and ntdetect.com on my C drive by those found on the Windows installation CD. With no effect, however: the prompt would tell me, on attempting to copy the files, that it wasn't able to do that (all the info I could get).

Anyone got an idea? It surely would help me a bunch, since I do need some Windows programs for school, rather sooner than later (and would rather not do the whole install again)...

Thanks beforehand.

---

### Post by Efwis on 2007-05-02
what do you get when you put the following command in Terminal?
```

sudo fdisk -l
```
this will tell you your designation for the windows install. I have a feeling that your entry in grub should 

```
title Windows XP
root (sd1,0)
savedefault
makeactive
map (sd0) (sd1)
map (sd1) (sd0)
chainloader +1
```

but I won't be sure until I see the output of the fdisk command.

---

### Post by lode on 2007-05-02
Hi, sudo fdisk -l prints the following output:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        9728    57167302+   f  W95 Ext'd (LBA)
/dev/sda5            2612        9728    57167271    7  HPFS/NTFS

Disk /dev/hdc: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1            3607        3737     1052257+  82  Linux swap / Solaris
/dev/hdc2   *           1        3606    28965163+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+   c  W95 FAT32 (LBA)

```

---

### Post by confused57 on 2007-05-02
You might also want to post the output of:
```
gedit /boot/grub/device.map
```

and

```
gedit /boot/grub/menu.lst
```

sometimes using "rootnoverify" instead of just "root" works:

```
title      Windows XP
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by lode on 2007-05-02
device.map gives

```
(hd0)	/dev/hdc
(hd1)	/dev/sda

```

menu.lst (excluding the commentary) (and so far without Efwis' advised adjustment)

```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=847ddb2a-e45f-4183-802f-8bed0e388e4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=847ddb2a-e45f-4183-802f-8bed0e388e4a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

```

That last drive in my previous post (with the fdisk output), Disk /dev/sdb: 250.0 GB, is, by the way, an external drive I just plugged in, which should have nothing to do with the problem.

Edit: changing "root" to "rootnoverify" gave the same NTLDR is missing error, Efwis' advise so far rendered the following Grub error: ```
Error 23: Error while parsing number
```.

---

### Post by confused57 on 2007-05-02
Try replacing your Windows entry with the one that I listed...your external drive could  "possibly"  affect booting, if it's connected when you boot up your system & it wasn't connected when you installed Ubuntu.

Added:  I assume you're able to boot your Window's drive, if it's selected to boot first in bios.

---

### Post by lode on 2007-05-02
That rendered the same NTLDR error, disconnecting the external drive didn't help either.

---

### Post by Efwis on 2007-05-02
according to your fdisk output your Windows drive boot sector is allocated as sda1.

did you try to replace the sd1 with sda1?

This is only speculation as I don't use SATA drives, I use ATA currently even though my machine is set up to accept up to 4 drives 2 of which are SATA and the other two ATA.

---

### Post by lode on 2007-05-02
That gave the 23 error:

```
Error 23: Error while parsing number
```

:(

---

### Post by Efwis on 2007-05-02
one last try,

change your windows section in Grub to the following:

```

title "Windows XP"
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1)
makeactive
chainloader +1
boot
```

*NOTE*
If this doesn't work, try changing all '0's to '1's

If it still doesn't work I am unsure what to do next, but hopefully someone who has a similar setup will be able to answer you.

---

### Post by confused57 on 2007-05-02
> **lode said:**
> That rendered the same NTLDR error, disconnecting the external drive didn't help either.

Can you boot your Window's drive when you select it to boot first in bios?  If you can't then it's not a grub issue, but a possible Window's boot problem.

Added:  If you can't boot your Window's drive, you might need to boot up your Window's install cd, press "r" for recovery & do a FIXMBR & FIXBOOT on your Window's drive...before you do this, it would probably be a good idea to set your Window's to boot before your Ubuntu drive in bios.

---

### Post by lode on 2007-05-02
I'm afraid it rendered the following message:

```
Error 12: Invalid device requested
```

Replacing 0's with 1's had the same (non) effect.

Thanks for sacrificing your time, nonetheless.

---

### Post by lode on 2007-05-02
> **confused57 said:**
> Can you boot your Window's drive when you select it to boot first in bios?  If you can't then it's not a grub issue, but a possible Window's boot problem.

Added:  If you can't boot your Window's drive, you might need to boot up your Window's install cd, press "r" for recovery & do a FIXMBR & FIXBOOT on your Window's drive...before you do this, it would probably be a good idea to set your Window's to boot before your Ubuntu drive in bios.

Booting from the Windows drive didn't work either, clearly showing that it was indeed a Windows problem. Hence, I tried fixing it via the Windows CD recovery. FIXMBR and FIXBOOT seemed to have worked, alas with no apparent succes at booting. I then tried replacing the NTLDR files once more, with the same result (the prompt telling me that it wasn't capable of doing so). In that same prompt I noticed that my Windows install looked pretty fubar (to me): the computer couldn't browse directories, find, nor logon, installed users, etc.

What's even worse: now I didn't seem able to boot up to Ubuntu, too (even after adjusting the drive boot order in the BIOS), I think Windows overwrote some Grub files or something.

Because of the fact that being able to work with some Windows-only programs (and that I'm not at all, as you've seen in this thread, a Linux guru and am still a little afraid of messing with stuff like WINE -- read: losing too much time messing with stuff like WINE) is, at the moment, more important than having the better computer experience (which I believe Ubuntu delivers), I'm currently completely reinstalling Windows XP.

I would like to know what I've done wrong, however. As far as I remember, I was never able to configure booting options during Ubuntu's installation, and, as far as I know, it shouldn't be the case that installing Ubuntu wrecks your Windows installation.

Anyone that sees something I've done wrong?

---

### Post by confused57 on 2007-05-02
Grub can be reinstalled to your Ubuntu drive mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You'll need to do this:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd0,1)"
you'll then enter:
```
root (hd0,1)
setup (hd0)
quit
```

I don't think installing Ubuntu messed up your Window's...I believe that maybe the entry I listed "may" have booted your Windows.  Your Windows was probably "corrupted" when you attempted to repair the "NTLDR missing" error, which you wouldn't have needed to do if your Window's drive boots when selected to boot first in bios.  I may be wrong about this, I've been wrong before and chances are I'll be wrong again in the future.
Good luck with getting everything set up...

---

### Post by Zorlin on 2007-05-02
Did you perhaps try copying a working NTDLR from another PC to a SAMBA (Windows) sharing folder, then mounting the windows hard drive with the ntfs-3g, then copying to the root of C:/?
A howto on ntfs-3g can be found here: [http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS](http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS)

---

### Post by telovoyagarcar on 2007-05-02
Im having problems too but with ubuntu, vista and xp at the same time.

Do this..
reinstall XP and let the installer overwritte the MBR.. so now XP works, but grub dissapears.. hence, the ubuntu boot option.
Now reinstall ubuntu, but pay a lot of attention at the grub installation stage of the setup, because it asks you if you want to include other operative systems, so then XP gets detected and automatically added to the grub menu.
The 3 times i installed ubuntu, i got the windows partitions recognized and addded automatically to the menu and they worked. This was done with Edgy and Feisty ALTERNATE installation cd, in text mode, because the normal live cd game a lot of headaches and didn't work for me.

you will ask me if i am giving you advice in something that i can not fix on my own computer yet, then why i do it...
My problem is something about the way my 6 partitions are arranged on the same drive, and because i screwed with the boot.ini file ntdetectc.com and ntldr. And reinstalling xp, then vista then ubuntu, would actually fix my problem, but i have too much important stuff in the vista installation that i dont want to risk by doing that. So if reinstalling XP is not a big problem in your case, then you can fix it with this...

Good luck

---

### Post by Herman on 2007-05-06
When you try to boot Windows with Grub and you get a grub error message you can normally fix it by editing Grub's /boot/grub/menu.lst file in Ubuntu.

When you try to boot Windows with Grub and Windows begins to boot but fails with a Windows error message it not a Grub problem, it is a problem that needs to be fixed in Windows.  

Most of the time it's just because the disk and/or partition number for Windows has been changed somehow so it no longer matches what is in Windows' boot.ini file, so Windows can't find the files it needs to boot up even if they are still there and they are okay.

All you need to do is edit boot.ini in Windows, but since you can't boot Windows to edit boot.ini file, it seems as if you are stuck. 

Here is what to do:
Go to this great website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldr"), and download one of the .iso files from the following link, [What if the computer doesn't have a floppy drive]("http://tinyempire.com/notes/ntldrismissing.htm#What_if_the_computer_doesn%27t_have_a_floppy_drive?").
  Burn it to disk (make a CD out of it). Boot that CD and try to boot Windows. 99% guaranteed it will boot! 

Then edit your boot.ini file so Windows with your new partition number or disk number so Windows will be able to boot by itself from now on.

Regards, Herman :)

---

