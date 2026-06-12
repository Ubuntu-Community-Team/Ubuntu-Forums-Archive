---
title: "[SOLVED] Grub Doesn't Detect Vista"
date: 2008-06-04
forum: General Help
---

### Post by ExBuM on 2008-06-04
I'm supposed to have 3 OS's installed right now. Ubuntu, XP, and Vista. 

When Ubuntu first finished installing Grub detected a Windows Vista OS and no XP. When I clicked on Vista it went to XP though...
Where did Vista go? XD

on gparted the hard drive is partitioned like this:
/dev/sda1: VistaOS

->/dev/sda2: extended
/dev/sda5: linux-swap
/dev/sda6: Ubuntu
/dev/sda7: WindowsXP

In the menu.lst for grub, (hd0,0) boots to WindowsXP.

Does anyone know how to get my Vista? :/

---

### Post by meierfra. on 2008-06-04
Did you delete any partitions when you installed Ubuntu?
Did you move any partitions?
Did you resize Vista? And if yes what partioning tool did you use?

Post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)

---

### Post by ExBuM on 2008-06-04
I resized the Vista partition and made new partitions for XP and Ubuntu. 

that command gives this:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5969    47945961    7  HPFS/NTFS
/dev/sda2            5970       30401   196250040    f  W95 Ext'd (LBA)
/dev/sda5            5970        6800     6674976   82  Linux swap / Solaris
/dev/sda6            6801       13361    52701201   83  Linux
/dev/sda7   *       13362       30401   136873768+   7  HPFS/NTFS
matt@matt-laptop:~$ 

```

---

### Post by meierfra. on 2008-06-04
This happens whenever you install XP after Vista. XP does not recognize Vista and overwrites the Vista Bootloader.  [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista") can fix it for you.

---

### Post by meierfra. on 2008-06-04
If you did not use "Vista Disk Management" to resize Vista, you might also have this [problem]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") (But don't worry about that yet, first see whether EasyBCD can solve your problem)

---

### Post by ExBuM on 2008-06-04
Blahhh I didn't install XP on a Primary partition..
I tried BCD and when it first started it couldn't find the drive that my computer boots off of probably because I'm using Grub. 
Fortunately I think Vista is deteced again.
Unfortunately Grub doesn't load and I have that "problem" from your second post.
I also don't have Vista installation disk.. only a recovery one. So should I just start over?

---

### Post by ExBuM on 2008-06-04
Actually I'm trying my mom's Dell Vista HomePremium DVD. 
My computer is an ASUS so reinstallation wouldn't work but I guess I'll try the repair thing.

EDIT: The reinstallation DVD worked :]
I got vista back. However Grub is gone now and Windows XP isn't detected again probably because it's not a primary partition XD

---

### Post by meierfra. on 2008-06-04
Reinstalling Grub is easy. Boot from the Ubuntu LiveCD. Open a terminal and type

```
sudo grub
```
and at the Grub prompt:

```
root (hd0,5)
setup (hd0)
quit
```

After rebooting, you should be able to boot into Vista and Ubuntu.

In my next post I will show you how to fix XP

 You might also remove the boot flag from the XP partition. I don't think it causes any problems, but it definitely isn't doing anything good.

---

### Post by meierfra. on 2008-06-04
This   should fix XP:

Boot to  Ubuntu.

Step 1)  Go to Computer->Places. One of those icons is for Vista and another one for XP. Open both by double clicking.

The Vista folder should have the following files

"boot.ini", "NTLDR" and "NTDetect.com". Copy all three of them to  the XP folder.

Step 2)```
gksudo gedit /boot/grub/menu.lst
```

Add this to the end of the file:

title Windows XP
root (hd0,6)
chainloader +1


(do not  add a "makeactive" line, that does not work on logical partition)

Save the file

Step 3)  
```
sudo apt-get install testdisk
sudo testdisk /dev/sda 
```

Click enter to "proceed"
Click enter to select "intel"
Use the "down arrow" and "enter"  to select "advanced"
Use the "down arrow" to select the  "XP" partition and then "enter"  to select  "boot"
Use the "right arrow" key and enter to select "Rebuild BS"
This might take a while. Once done just follow the instruction on the screen to save the setting and quit testdisk.

That's it. Reboot and hope for the best.

---

### Post by ExBuM on 2008-06-04
Yeah I saw the reinstall Grub thing from your signature XD

I'm trying XP now

---

### Post by ExBuM on 2008-06-04
Hm. Didn't finish yet but I gotta go to sleep. Someone can mark this thread as solved since I got Vista working again.. XD Thanks meierfra!!

---

### Post by meierfra. on 2008-06-04
> Hm. Didn't finish yet but I gotta go to sleep
O.K but please keep trying tomorrow. You are my guinea pig. I only learned how to do this a few days ago. It worked perfectly for me. But I'm really curious to see whether it will work for other people on different computers.
I should mention that most of the credit for this method goes to [Herman]("http://ubuntuforums.org/showthread.php?p=4701367#post4701367"). I did some refinement and tailored it to your situation


> Someone can mark this thread as solved

That's your job: 

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads ]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by ExBuM on 2008-06-04
Okay so I'm now booting all 3 OS's perfectly with Grub :D

I don't think the testdisk thing worked for me. But the parts before that seemed sufficient. 

I think this is all I needed to do
> Boot to Ubuntu.

Step 1) Go to Computer->Places. One of those icons is for Vista and another one for XP. Open both by double clicking.

The Vista folder should have the following files

"boot.ini", "NTLDR" and "NTDetect.com". Copy all three of them to the XP folder.

Step 2)
Code:

gksudo gedit /boot/grub/menu.lst

Add this to the end of the file:

title Windows XP
root (hd0,6)
chainloader +1


(do not add a "makeactive" line, that does not work on logical partition)

Save the file


Thank you VERY much for helping me with this!

---

### Post by meierfra. on 2008-06-04
> I don't think the testdisk thing worked for me. 

testdisk is supposed to fix a number in the  boot sector of the XP partition. Maybe, for some reason you already had the correct number. Or did you run "fixboot" on the XP partion, that would fix the number, too.

What kind of problems did you have with testdisk?

> Thank you VERY much for helping me with this! 

You are welcome.  You actually managed to overcome three different problems which often lead to re-installation

1)  Installed XP after Vista.

2)  Resized Visa with gparted.

3)  XP on a logical partition.

---

### Post by ExBuM on 2008-06-05
testdisk ended up saying something was already the same or something like that. Then it quit. So I just restarted and it was okay. ^^

---

### Post by meierfra. on 2008-06-05
> testdisk ended up saying something was already the same or something like that.

So  the "testdisk" step is not always necessary.  Good to know, Thanks.

---

