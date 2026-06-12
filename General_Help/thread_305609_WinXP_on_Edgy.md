---
title: "WinXP on Edgy"
date: 2006-11-23
forum: General Help
---

### Post by ishift on 2006-11-23
i didn't know where to post about this, but please feel free to move to the appropriate section.

i need to to use photoshop cs2, but, from what i have read, it doesn't run well (or so easily) on edgy. therefore, i thought about running a dual boot with windows xp.

now, i'm using a 40gb hd, of which about 20gb are free. is it possible to just simply...

1. boot up the livecd
2. make my main ubuntu partition smaller
3. format the new partition as "ntfs"
4. boot xp onto the partition (without erasing any of my personal data)

:confused: 

so, is this doable? what are the risks, if any? (i'm assuming "losing your data by playing with partitions" is up there.):rolleyes: 

i read about vmware, but my laptop won't be able to handle it. (see sig for specs)

thanks guys!

---

### Post by x64Jimbo on 2006-11-23
Why not just do it in VMWare? Since photoshop doesn't require 3d acceleration, it will work just fine in a virtual environment.

---

### Post by maddog39 on 2006-11-23
Wait, I use VMWare to run ReactOS but since ReactOS is alphaware and BSOD's all the time I cant use it for everyday windoze stuff. So I've been trying to figure this out forever. How do you install windoze on VMWare without a .vwx image file?

---

### Post by telovoyagarcar on 2006-11-23
Think about this first...

Windows XP + Photoshop CS2 + a PSD file loaded with a bunch of effects on a 700mhz laptop and 256mb ram?

Whats the point?... i use like 500MB of ram to do the same in my pc when working on windows. Dual core machine.

If you need to do basic stuff, then try to get used to Gimp..
If you need to "WORK with Photoshop" then you really need a better computer in the first place...

Just my opinion.

I am also so used to work with CS2 that i know how you feel... i couldn't do the same with Gimp.

---

### Post by ishift on 2006-11-23
vmware would require, at the very least an additional 256mb to run winxp, which i don't have.

as for running cs2 in general, back when i had winxp, photoshop cs2 ran very nicely. understandably, some things slowed it down, but they were rare and far in between. i know it runs well on my machine, i'm just wondering if i can dual boot the way i explained in my first post.

and, yea, i am looking for a better laptop. however, in the meantime, i still need to use cs2. gimp is good, but (1) i lack the time needed to learn it and (2) if i can dual boot easily, why bother?

thanks!

---

### Post by x64Jimbo on 2006-11-23
You never mentioned the lack of muscle in your PC. I can see why you'd want to dual boot. You shouldn't encounter any problems.

---

### Post by ishift on 2006-11-23
so, when i boot up the winxp cd, it should recognize the ntfs partition i made for it and install only on that?

and, i shouldn't expect any problems with grub?

---

### Post by zgornel on 2006-11-23
Windows will see the ntfs partition and overwrite the mbr (if grub is located there you must boot afterwords with a live cd to restore it).

---

### Post by ishift on 2006-11-23
i can restore grub as explained in the following post?


[QUOTE=bulldog]That's easy with the live cd.
Boot into the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

```
sudo grub
```

This will get you a grub prompt

```
find /boot/grub/stage1
```

This will return a location which you have to use in the next commands.

```
root (hd?,?)
```

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Finally exit the grub shell

```
quit
```

Now Grub will be installed to the mbr.[/QUOTE]

[source]("http://ubuntuforums.org/showpost.php?p=1794135&postcount=4")

hmm? :-k

p.s. sorry, i'm kinda still in the learning stages. i really appreciate all the help!

---

### Post by x64Jimbo on 2006-11-24
You could also take a backup of your MBR and simply restore it after installing windows. 
[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/)

---

### Post by ishift on 2006-11-28
all right, so i installed the setup files on my new fat32 partition and, when i rebooted, it gave the "disk error" message. i guessed that the mbr screwed up grub, so i reinstalled grub through the livecd.

now, i don't know how to install winxp because it's not technically completely installed, therefore, grub is not seeing it.

help please.

---

### Post by ishift on 2006-11-28
bump :)

---

### Post by ishift on 2006-11-28
w00t.

i got it to work. i had to change the format of the partition from fat32 to ntfs for it to recognize the partition as bootable.

i'm really starting to love ubuntu and linux in general.

thanks guys!

---

