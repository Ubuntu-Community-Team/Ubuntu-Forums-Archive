---
title: "Windows Installation/Grub Failure"
date: 2007-11-27
forum: General Help
---

### Post by Zinc on 2007-11-27
So, I've never really double booted before. I'm currently running Gutsy , and I've been trying to install Windows XP into a FAT32 partition. I've never had problems installing windows on this machine before I installed Ubuntu, but now I can't even complete Windows installation because the grub fails when the installation reaches the point where I have to reboot. Any ideas how to prevent that from happening?

---

### Post by Craigus on 2007-11-27
What is the specific error message that you are seeing ?

This is unusual, because the expected behaviour is that the XP installer should overwrite the MBR and there will be no GRUB. You normally have to then take extra steps to be able to boot linux:

[http://ubuntuforums.org/showthread.php?t=620826]("http://ubuntuforums.org/showthread.php?t=620826")

---

### Post by teryowen on 2007-11-27
Ya windows useally like to sit in the first parttion... But try booting of the XP CD and trying something along the lines of fixmbr and fixboot.

then only XP will be booting and then you will have to boot up using a live CD, and restore the GRUB and then of course edit it so that it has both the Linux option and the XP one.

EDIT: oh you might try to look into superGRUB

---

### Post by Irony on 2007-11-27
You are not making sense because windows installs it own thing to the mbr, also I doubt XP will install to a fat32 partition it would need to format it first to ntfs.

Once you install windows you will then have to use a live cd to install grub.

---

### Post by Zinc on 2007-11-27
> **Craigus said:**
> What is the specific error message that you are seeing ?

This is unusual, because the expected behaviour is that the XP installer should overwrite the MBR and there will be no GRUB. You normally have to then take extra steps to be able to boot linux:

[http://ubuntuforums.org/showthread.php?t=620826]("http://ubuntuforums.org/showthread.php?t=620826")

I've read about that, but my problem is the fact that I can't really boot either one. GRUB fails before Windows installation even starts so I'm assuming MRB won't be able to overwrite GRUB at that point. When my pc tries to load GRUB after reboot I normally get either "Disk Failure" or "Operating system not detected".

---

### Post by meierfra on 2007-11-27
How many hard drives do you have? 

If you have a ubuntu LiveCD, boot from it.Open a terminal (Application->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```
(l is lower case L)

---

### Post by Zinc on 2007-11-27
> **meierfra said:**
> How many hard drives do you have? 

If you have a ubuntu LiveCD, boot from it.Open a terminal (Application->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```
(l is lower case L)

sda is the one I want to use, sdb is my external.

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6570    52773493+  83  Linux
/dev/sda2   *        6571       14219    61440592+   b  W95 FAT32
/dev/sda3           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)
```

---

### Post by meierfra on 2007-11-27
Did you have  the Fat 32 partition before you tried to  install  Windows? Did you resize the Ubuntu partition recently?

Try this: 

```
sudo grub
root (hd0,0)
setup (hd0)
quit

```

Reboot.  Hopefully this allows you to  boot in Ubuntu (we'll worry about Windows later)

---

### Post by teryowen on 2007-11-27
do exactly what meierfra suggested.

---

### Post by Zinc on 2007-11-27
> **meierfra said:**
> Did you have  the Fat 32 partition before you tried to  install  Windows? Did you resize the Ubuntu partition recently?

Try this: 

```
sudo grub
root (hd0,0)
setup (hd0)
quit

```

Reboot.  Hopefully this allows you to  boot in Ubuntu (we'll worry about Windows later)

Thanks, I've managed to restore GRUB and got Ubuntu working. Though if I try installing Windows again I'm pretty sure it's going to cause the same problem.
And yes, the Fat32 partition was created about a month ago when I resized my Ubuntu partition and turned it into two.

---

### Post by meierfra on 2007-11-27
Well, Windows might already be installed. Try this in a terminal in ubuntu:

```
gksudo gedit  /boot/grub/menu.lst 
```

This opens the file "menu.lst"

change 

"timeout 3" to "timeout 10"

and 

"hiddenmenu" to "#hiddenmenu"

Add this to the end of the file:

title Windows XP
root (hd0,1)
makeactive
chainloader +1

Save the file and reboot. You will get a "grub-menu". Select Windows XP and see that happens.

---

### Post by Zinc on 2007-11-27
I get "Disk Error" when I try doing that. I never really managed to complete Windows installation - it only got as far as copying the files.

---

### Post by midhunpp on 2007-11-27
try installation after formatting C( you primary partition)

---

### Post by teryowen on 2007-11-27
Heres what i would do personally seems like your going in circles.

Format your hard drive, obviously back up anything you need.

Install XP on first half, finish with that make sure it works.
Install Ubuntu.

And your done.

---

### Post by Zinc on 2007-11-27
> **midhunpp said:**
> try installation after formatting C( you primary partition)

Well, my primary partition contains Ubuntu. And while your suggestion would probably work, getting rid of Ubuntu and installing it again after I install Windows is not really something I want to do.

---

### Post by teryowen on 2007-11-27
In that case, i guess what ur going to have to do is just pop that windows CD in, start the installation select the correct partition you dont want it to format the ubuntu one.

During the installation windows will take over the MBR, and then you wont be able to boot to ubuntu.

but then once the windows installation is done, boot of a live CD and run the same commands as previously stated:

sudo grub
root (hd0,0)
setup (hd0)
quit

(do you see why im saying this is going in circles?)

---

### Post by Zinc on 2007-11-27
> **teryowen said:**
> Heres what i would do personally seems like your going in circles.

Format your hard drive, obviously back up anything you need.

Install XP on first half, finish with that make sure it works.
Install Ubuntu.

And your done.

I'm actually hoping there is another solution, though I haven't found anything as of yet. If worst comes to worst I'll just go without windows because reinstalling Ubuntu at this point is not really an option.

---

### Post by meierfra on 2007-11-27
What kind of  Windows CD are you using ? Is it a  Restore Disk?  
Did you ever try to use NTFS in place of Fat32?

---

### Post by Zinc on 2007-11-27
> **meierfra said:**
> What kind of  Windows CD are you using ? Is it a  Restore Disk?  
Did you ever try to use NTFS in place of Fat32?

It's not a restore CD. My laptop came with Vista so I just downloaded XP image instead. I thought there might be something wrong with my copy of Windows XP, so I tried another one and it still causes the same problem. I haven't tried using ntfs, though I'll probably try it out tomorrow if you think it might help.

---

### Post by meierfra on 2007-11-27
> just downloaded XP image instead.
I'm done with this case.

---

