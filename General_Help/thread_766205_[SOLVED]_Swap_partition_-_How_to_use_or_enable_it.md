---
title: "[SOLVED] Swap partition - How to use or enable it?"
date: 2008-04-25
forum: General Help
---

### Post by danial-aalee on 2008-04-25
Hi,
First of all thanks for your time to look in this question.

I am new to Linux - started with Ubuntu 8.04 (beta) - (please pardon my ignorance and lack of knowledge). I have two questions here, not directly related to each other though.

1. I have created a separate partition for swap (2G space) but it appears that system is not using that at all.  Is there a way to find out for sure and if it is not in use, how I can enable it to be used as a swap?

2. First I was using default desktop (GNOME) and then moved to KDE environment.  Anyway, there was a screen saver "Fireworks 3D (GL)". Now I can see that in the screen saver list (under OpenGL Screen saver) but can not activate it any more, for that matter none of those OpenGL screen saver.  I can see all the setup options and can tweak those but preview and/or actual saver never comes up - just a black screen.  Any idea what I am doing wrong or did wrong, more importantly how to fix it?  Any help, guidance, assistance, a shoulder to cry on (if it is doomed already) and of course your precious time is very appreciated.
Thanks,

Guru -no- more:(

p.s.: by the way, since I am using KDE, am I using KUBUNTU (even when I have option to choose GNOME or xfce) or UBUNTU (as I choose it in prefix of this thread)?

---

### Post by kpkeerthi on 2008-04-25
To check if ubuntu is using swap run this command in a terminal.
```
top
```
It should report swap size and usage. If swap size is reported as 0, then ubuntu is not using it.

To get your swap partition, run this command
```
sudo fdisk -l
```

I asssume your swap partition is **/dev/sda3**. To quickly set your swap partition, run this command
```
sudo swapon /dev/sda3
```
Now check with the **top** command.

To set swap partition permanently, 
1. ```
gksudo gedit /etc/fstab
```
2. Add this line to the end of the file. 
```
/dev/sda3       swap            swap        defaults
```
3. Save & Exit. Reboot.

* Change /dev/sda3 to the one appropriate for you as reported by **fdisk**

---

### Post by zvacet on 2008-04-25
@ **danial-aalee**

>  by the way, since I am using KDE, am I using KUBUNTU (even when I have option to choose GNOME or xfce)

Every time when you choose KDE you are using Kubuntu.GNOME,KDE,XFCE are just different [desktop environments]("http://en.wikipedia.org/wiki/Desktop_environments"), but OS is the same.

---

### Post by danial-aalee on 2008-04-25
Good People,
Thanks a lot for your response.

**ZVACET** - Thanks for clearing the confusion about naming and OS.

**kpkeerthi** - Thanks for your detailed instructions.  I tried to work on it last night but I guess, it was a bit late and my sleepy head didn't see the very last line (in your message) to check the devices with **fdisk**.  I tried everythign else to go nowhere :(.  Later, I will check that and see if I can figure out the right device and enables it.  May be in an hour or so, I will post again with success/failure report.

Once again, thanks to both of you :KS guys/gals :KS

Danial

---

### Post by dondad on 2008-04-26
> **danial-aalee said:**
> Hi,
First of all thanks for your time to look in this question.

I am new to Linux - started with Ubuntu 8.04 (beta) - (please pardon my ignorance and lack of knowledge). I have two questions here, not directly related to each other though.

1. I have created a separate partition for swap (2G space) but it appears that system is not using that at all.  Is there a way to find out for sure and if it is not in use, how I can enable it to be used as a swap?

2. First I was using default desktop (GNOME) and then moved to KDE environment.  Anyway, there was a screen saver "Fireworks 3D (GL)". Now I can see that in the screen saver list (under OpenGL Screen saver) but can not activate it any more, for that matter none of those OpenGL screen saver.  I can see all the setup options and can tweak those but preview and/or actual saver never comes up - just a black screen.  Any idea what I am doing wrong or did wrong, more importantly how to fix it?  Any help, guidance, assistance, a shoulder to cry on (if it is doomed already) and of course your precious time is very appreciated.
Thanks,

Guru -no- more:(

p.s.: by the way, since I am using KDE, am I using KUBUNTU (even when I have option to choose GNOME or xfce) or UBUNTU (as I choose it in prefix of this thread)?
How are you determining that the swap file is not being used? Mine shows 0 usage 99% of the time because I have enough memory for what I am soing such that the system does not need to swap.

If you look at the system monitor, does it show the swap usage (or existance?)

---

### Post by danial-aalee on 2008-04-26
dondad,

I checked the system monitor and it shows 'no swap space available' and has nothing in there.  My safe assumption is swap is not turned on.  The reason I thought about swap was once in a while system would go very slow and then pick up.  I am using AMD 64X2 3800 with a 2G ram.  2 HD (60G + 200G).  Just a mediocre system - nothing fancy.

60G drive is the boot drive for Ubuntu and XP.  That particular drive has:
 
1. primary partition for XP. 
2. primary part...   for Ubuntu Ext3  10G
3. extended
3a. logical part...  for extra items Ext3 10G (not in use - not sure how to use it)
3b. logical part...  for swap Ext3 2G (apparently not in use and am trying)

When I used '*sudo swapon /dev/sda6*' command it returns "Invalid argument" error.  Now this may be because swap partition is under an extended partition.  I sure do not know the truth but tying to know.  Oh furthermore, I used **fdisk -l** to figure out device and it is **sda6**.  That is what I tried to use with 'swapon.

Alright, so this is my story for the time being, any helping hand please...

danial

---

### Post by vroy on 2008-05-05
After I let my laptop hibernate, it can't enable the swap. The output of 
sudo fdisk -l is the following

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/hda2            3316        3497     1461915   82  Linux swap / Solaris
/dev/hda3            3498        6074    20699752+  83  Linux
/dev/hda4            6075        7296     9815715    b  W95 FAT32

But, when I'm typing the command
sudo swapon /dev/hda2
it's saying

swapon: /dev/hda2: Invalid argument

By the way the output of
 free -m
is 
             total       used       free     shared    buffers     cached
Mem:           503        453         50          0         73        199
-/+ buffers/cache:        180        323
Swap:            0          0          0

Would you please tell me how to enable the swap.

---

