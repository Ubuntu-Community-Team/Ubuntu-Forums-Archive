---
title: "Computer won't boot."
date: 2006-12-17
forum: General Help
---

### Post by Miki01 on 2006-12-17
Hey everyone, 

I'm currently running a PC that dual-boots from Ubuntu 6.06 and WinXP Pro.

I just recently installed the latest updates (I haven't used Ubuntu in a while).

After it asked me to reboot, I accepted and it rebooted. After the PC restarts, it shows my POST and then turns black and this text appears:

> Failed to read splash image ((hd1,0)/boot/grub/blu.xpm.gz)
Press any key to continue...

So pressed a key and my GRUB menu appears and I try to boot Ubuntu, my screen goes blank and my PC reboots... So after that same message appears again, I choose WinXP in the GRUB menu. The same thing happens, my screen turns blank and the whole PC reboots.

Does anyone know what went wrong? What do I need to do in order to fix this? I have an assignment for class due tomorrow and another for thursday. Those files are in my computer but I cannot even get to it.

Please reply soon, thanks.

---

### Post by shane2peru on 2006-12-17
Probably when you updated, your kernel was updated, and your /boot section was re-written.  You need boot up with a Ubuntu Live CD.

When you get in you need to open a terminal, and mount your Ubuntu partition.  Go to your /boot/grub/menu.lst and open it.  I'm guessing you need to comment out the line that says splashimage  just put a # in front of it.  And reboot.  It can't find the splash image and therefore doesn't display anything.  Maybe if you give it 10 seconds it will boot into the default that you have set.

Shane

---

### Post by Miki01 on 2006-12-17
Okay, I'm going to try to boot from the live CD again. The first time I tried, after I got to the screen with that bar where the icons appear and the sound effect starts to play, it rebooted... I hope this time it works.

> When you get in you need to open a terminal, and mount your Ubuntu partition. Go to your /boot/grub/menu.lst and open it. I'm guessing you need to comment out the line that says splashimage just put a # in front of it. And reboot. It can't find the splash image and therefore doesn't display anything. Maybe if you give it 10 seconds it will boot into the default that you have set.

How do I mount my partition? I'm a bit of an amateur with Ubuntu, sorry.

I found out a way to mount it, so I navigated to the menu.lst file and added the # at the beginning of splash page ((hd1,0)/boot/grub/blu.xpm.gz) and rebooting. I still cannot boot into any OSes and that message still appears before the grub menu.

What is your method of mounting hda1?

---

### Post by mayonaise15 on 2006-12-17
To mount you just need to create a directory to set as the mount point:
```
sudo mkdir /media/hda1
```

Then mount it in that directory:
```
sudo mount /dev/hda1 /media/hda1
```

The hda1 might need to be changed depending on how you have your disk partitioned.  hda1 is the first partiton on your hard drive, hda2 is the second, hda3 is the third, etc...

Here is a link to some more info about mounting:
[https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount#head-e2cd6350c74b57c36be49bc816c54f38a319e873")

---

### Post by Miki01 on 2006-12-17
EDIT: okay, I'm going to give that a try. Thanks

---

### Post by Miki01 on 2006-12-17
Okay, I did just that and checked menu.lst and it still had the # infront of the splash image line.

Apparently, it did not do anything. By the looks of it, the folder that menu.lst in, blu.xpm.gz is also in that folder, so I don't know what could be causing this...

Any more suggestions?

---

### Post by mayonaise15 on 2006-12-17
In your /boot/grub/menu.lst file, can you find your line that looks like this:
```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

I'm wondering why it is looking for the boot splash image in (hd1,0) do you have 2 hard drives in your computer?

Could you show us what prints out when you type:
```
sudo sfdisk -l
```

---

### Post by Miki01 on 2006-12-17
Yes, I do have those lines. It goes:

> ## End Default Options ##

splashimage=((hd1,0)/boot/grub/blu.xpm.gz)
splashimage=((hd1,0)/boot/grub/blu.xpm.gz)

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)    ***wouldn't that need to be (hd1,0)?***
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


What I did with shane2peru's suggestion was press CTRL+F and type in splash and just added a "#" infront of the line. Should I do that to all the lines that contain splashimage=((hd1,0)/boot/grub/blu.xpm.gz)?

sudo sfdisk -l gives me:

> ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/hda: 9729 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1          0+   1215    1216-   9767488+  83  Linux
/dev/hda2   *   4865+   9728-   4864-  39062520    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
                end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/hda3       1216    1823     608    4883760   82  Linux swap / Solaris
/dev/hda4       1824    4864    3041   24426832+   5  Extended
/dev/hda5       1824+   4864    3041-  24426801    b  W95 FAT32

---

### Post by Miki01 on 2006-12-17
Anyone? Please? This is urgent...

---

### Post by shane2peru on 2006-12-17
Ok.  here is what you need to do.  These two lines:> splashimage=((hd1,0)/boot/grub/blu.xpm.gz)
splashimage=((hd1,0)/boot/grub/blu.xpm.gz)
  need to look like this :```
#splashimage=((hd1,0)/boot/grub/blu.xpm.gz)
#splashimage=((hd1,0)/boot/grub/blu.xpm.gz)
```  Any line that contains the words Splashimage need to have that in front of them.  What this is going to do is make your Grub not look pretty anymore.  Sorry for my quick fix earlier, I was headed out the door.  Grub is having problems finding the picture, so it doesn't display anything, matter of fact, it seems to crash grub.  So by putting the # in front of that line we are eliminating that line from the script.  Once we get into Ubuntu, and Windows we can play around with getting this setting setup correctly.  Post back if you have more questions.

Shane

Probably the correct setting for that line is:
```
splashimage=((hd0,0)/boot/grub/blu.xpm.gz)
```  and you only need one of those lines in there.  - Note the 1 was changed to a 0.

---

### Post by mayonaise15 on 2006-12-18
Yeah, I think shane2peru is correct.  The line should probably read:

```
splashimage=((hd0,0)/boot/grub/blu.xpm.gz)
```

and there should only be one of them.
```

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0) wouldn't that need to be (hd1,0)?
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

^^^ That all looks right to me.  It should be (hd0,0) because hd0 = hda, hd1 = hdb in Linux.  That is why I had you show the output of sudo sfdisk -l.  I do see something that concerns me in that output, though.  Does anybody else know what this means?

```
/dev/hda2 * 4865+ 9728- 4864- 39062520 7 HPFS/NTFS
start: (c,h,s) expected (1023,254,63) found (1023,0,1)
end: (c,h,s) expected (1023,254,63) found (1023,239,63)
```

---

### Post by Miki01 on 2006-12-18
Thanks a lot shane2peru! That fixed it!

To be honest, I tried to make that background appear in my GRUB but it never actually worked! I just never got around to trying to remove it. (Removing it is as easy and deleting the file and removing the *splashimage* lines, right?)

Thanks mayonaise15. But also, when I read that output, I also thought that it sounded a little bit awkward. It expects certain variables, but some of those variables are off. I wonder what effects those will have on things to come in the future?

---

### Post by shane2peru on 2006-12-18
No problem.  I think you were very close, but the line needed to read hd0,0 instead of 1,0.  I have been there and done that.  I like the nice Grub screen, and many distros have this out of the box.  It is a nicety that Ubuntu could easily add, and hopefully will in the future.  At any rate glad you got it working.

Shane

---

