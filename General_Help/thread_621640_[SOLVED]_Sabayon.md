---
title: "[SOLVED] Sabayon?"
date: 2007-11-23
forum: General Help
---

### Post by doctorgreg on 2007-11-23
Hey there.  I am using vista on my laptop and I installed Ubuntu Gutsy on a partition so now I have the dual boot goin on.  Would I be able to install Sabayon on a 3rd partition or would that screw up the boot loader process?

---

### Post by scxtt on 2007-11-23
you can install quite a few w/o incident, depending on your partition scheme ... if you've got a working version of grub installed on the MBR, you can just edit the /boot/grub/menu.lst of the OS you last installed and include an entry for the OS you just installed ...

or let Sabayon install grub if it picks up all the OSes currently installed ...

---

### Post by doctorgreg on 2007-11-23
Well the last OS I installed was Gutsy so there is already a grub menu.  In that menu it says other operating systems and that is where vista is.  So that is probly where Sabayon will go too?

---

### Post by scxtt on 2007-11-23
the only thing you've got to "worry" about is after you install sabayon, you'll have 2 menu.lst files, 1 for each OS:

gutsy: /boot/grub/menu.lst
sabayon: /boot/grub.menu.lst

so if you want to make changes to grub, you'd have to make sure to edit menu.lst for the OS that was the last to change grub, the partition where the MBR points ...

i'd use the menu.lst from the OS you think you'll use the most ... you really can't mess anything up either way, just keep that in mind :)

---

### Post by doctorgreg on 2007-11-23
gutsy: /boot/grub/menu.lst
sabayon: /boot/grub.menu.lst

So that is all that will show up when I reboot after installing sabayon?  The OS to last change the GRUB would sabayon would it not?  What would happen if i mess it up?  I don't know if i will be able to do this (get the guts for it)

---

### Post by disturbedite on 2007-11-23
if you installed sabayon, yes, the "latest version" of grub would be on sabayon.

---

### Post by doctorgreg on 2007-11-23
I have a program in vista called easy BCD.  I can add boot entry to the vista boot menu.  That way from the original Ubuntu grub menu i will choose vista under other OS then I will be given a choice of vista or sabayon.  Think that would work?

---

### Post by scxtt on 2007-11-23
i doubt that you would be presented w/ a choice after initially selecting Vista ... you're already past the MBR area where you would make that kind of choice - it might work, but i doubt it ...

sounds like it would have been better to use "easy BCD" initially (i.e. no grub when ubuntu was installed), then added entries for Gutsy+Sabayon, etc. ...

really, there's no harm in letting Sabayon "take over" grub at this point ...

---

### Post by doctorgreg on 2007-11-23
So if sabayon takes over the grub then Ubuntu and Vista should be in that menu for me?

---

### Post by doctorgreg on 2007-11-23
Even after I installed Ubuntu,  I went into EasyBCD and added Ubuntu to the list.  Then rebooted and the GRUB menu came up for ubuntu.  From that menu i chose vista under other operating systems.  After i clicked on that i was brought to the vista boot menu and i could choose either vista or ubuntu from there.  Thats why I thought it might work.

---

### Post by scxtt on 2007-11-23
> So if sabayon takes over the grub then Ubuntu and Vista should be in that menu for me?yes, and generally it will auto-detect them and inform you of it ...

> After i clicked on that i was brought to the vista boot menu and i could choose either vista or ubuntu from there. Thats why I thought it might work.interesting, if it'll boot ubuntu fine, go for it ;)

---

### Post by doctorgreg on 2007-11-24
Alright well i'll give it a whirl.  Just don't want to get locked out of my vista or lose it cuz i have all my important stuff on there.  Thanks alot man.

---

### Post by doctorgreg on 2007-11-24
one more quick question.  Do I use the same format as ubuntu for the partition.  I think its like ex3 or something

---

### Post by scxtt on 2007-11-24
ext3 is a good f/s format - i use it predominantly (LVM too), only cause i'm to lazy to read up on the others (like reiser, etc.) :p

---

### Post by doctorgreg on 2007-11-24
one more question.  Do I need to make another swap file or just extend the existing one?

---

### Post by rsambuca on 2007-11-24
I have just one swap that I share amongst 5 different distros.  Works well.

By the way, Sabayon should detect Windows and Ubuntu - at least it detected all the distros on my setup.

---

### Post by doctorgreg on 2007-11-24
my current swap is 512mb.....what should I change it to.  Maybe just double it?

---

### Post by scxtt on 2007-11-24
> **doctorgreg said:**
> my current swap is 512mb.....what should I change it to.  Maybe just double it?just use the swap configured from ubuntu, you can only use swap for 1 OS @ a time, so no sense in having multiples ...

how much physical RAM do you have? ... 512mb swap should be fine unless you've got <1Gb (depending on how much you do @ once) ...

anymore, amount of swap space config'd is irrevelant ... i used to do 2x amount of physical RAM, back when 512mb of RAM was "a lot" ... but now that HDD space is so "cheap", anything from 2Gb swap --> 8Gb swap doesn't really matter ... i had a (desktop) box w/ 2Gb of ram and i don't think it ever touched swap (maybe a teeny bit) ... now i have a VMware Server box w/ 4Gb RAM, but just 2Gb swap - don't think it's touched until i start up 5 of my VMs (1 w/ 2Gb virtual RAM alloc, most w/ 256-512) ...

---

### Post by doctorgreg on 2007-11-24
well I installed sabayon and I configured the settings in the sabayon setup.  Thought I had it all right.  I can boot into vista but get an error when i click on ubuntu gutsy.  Error 13 i guess.  Don't know what it is.

---

### Post by rsambuca on 2007-11-24
What does your /boot/grub/grub.conf say for the Ubuntu entry?

---

### Post by scxtt on 2007-11-24
post the **/boot/grub/menu.lst** from sabayon and the output of **sudo fdisk -l** ... maybe we can sort it out ...

---

### Post by doctorgreg on 2007-11-24
do i just type that code into the terminal in sabayon?

---

### Post by Paul133 on 2007-11-24
I also use ext3. As far as I know, is creator was never mixed up with a murder assusation and the Russian Mob. 

/Too much WIRED. :)

---

### Post by doctorgreg on 2007-11-24
permission denied.  I know in ubuntu I have to type sudo but what do i type in sabayon?

---

### Post by doctorgreg on 2007-11-24
when i do type sudo and then either one of the commands it says command not found?

---

### Post by Sorivenul on 2007-11-24
Don't know if it still does, but last I touched Sabayon it used grub.conf instead of menu.lst.  Anyone?  This may be a contributor to the problem editing the files.

---

### Post by meierfra on 2007-11-24
Try

```
su
fdisk -l
cat /boot/grub/menu.lst 
```

---

### Post by meierfra on 2007-11-24
Sorivenul might be right. If 

cat /boot/grub/menu.lst

does not work

try 

cat /boot/grub/menu.conf  (Edit:  Turns out /boot/grub/grub.conf is the corrected  name)

---

### Post by doctorgreg on 2007-11-24
localhost cgz # fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7462    59935648+   7  HPFS/NTFS
/dev/sda2           10068       10198     1052257+  82  Linux swap / Solaris
/dev/sda3           10201       12161    15751732+  83  Linux
/dev/sda4            7463       10067    20924662+  83  Linux

Partition table entries are not in disk order

---

### Post by doctorgreg on 2007-11-24
localhost cgz # cat /boot/grub/menu.lst
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,3)
#          kernel /boot/kernel-genkernel real_root=UUID=f2ea0f65-d2d1-4180-bb5d-07d0bbfe1c67
#          initrd /boot/initramfs-genkernel
#boot=sda
default=1
timeout=6
splashimage=(hd0,3)/boot/grub/splash.xpm.gz
title Sabayon Linux x86 3.4 Mini Edition
        root (hd0,3)
        kernel /boot/kernel-genkernel-x86-2.6.22-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=f2ea0f65-d2d1-4180-bb5d-07d0bbfe1c67  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi
        initrd /boot/initramfs-genkernel-x86-2.6.22-sabayon
title Ubuntu Gutsy GIbbons 7.10
        rootnoverify (hd0,2)
        chainloader +1
title Windows Vista
        rootnoverify (hd0,0)
        chainloader +1

---

### Post by meierfra on 2007-11-24
Open the file /boot/grub/menu.lst via

```
su
gedit /boot/grub/menu.lst
```
(If gedit does not work, use some other editor)

Replace 

title Ubuntu Gutsy GIbbons 7.10
rootnoverify (hd0,2)
chainloader +1


by

title Ubuntu Gutsy GIbbons 7.10
root (hd0,2)
configfile /boot/grub/menu.lst

---

### Post by meierfra on 2007-11-24
See [http://ubuntuforums.org/showthread.php?t=621115#2]("http://ubuntuforums.org/showthread.php?t=621115#2") for a short explanation of the "configfile method"

---

### Post by doctorgreg on 2007-11-25
gedit don't work..............can i use kate...............that is listed as an editor in the start menu under editors

---

### Post by doctorgreg on 2007-11-25
I don't think kate works either...........i probly sound stupid

---

### Post by meierfra on 2007-11-25
> can i use kate.......
Yes

---

### Post by meierfra on 2007-11-25
> don't think kate works either.

Do you get an error message?

---

### Post by rsambuca on 2007-11-25
Man, this is too painful.  You can use nano as a text editor.  kate is installed by default as well if you prefer a gui.

EDIT:  And the actual file you want to edit is /boot/grub/grub.conf, although the menu.lst is just a link to it.

---

### Post by doctorgreg on 2007-11-25
kate /boot/grub/menu.lst
bash: kate: command not found

---

### Post by doctorgreg on 2007-11-25
can i not just edit it right in the grub menu when i boot up?

---

### Post by rsambuca on 2007-11-25
What?  Are you going to edit the boot menu every single time?

Why not edit it once?  Log in as root.  Then

```
nano /boot/grub/grub.conf
```

---

### Post by meierfra on 2007-11-25
> EDIT: And the actual file you want to edit is /boot/grub/grub.conf, although the menu.lst is just a link to it.

rsambuca: Thanks for the information (I know nothing about Sabayon)


doctorgreg: That means you should use "configfile /boot/grub/grub.conf" in place of  "configfile /boot/grub/menu.lst"  (Edit:  This is wrong. configfile will look for the file on the ubuntu partion. Ubuntu uses menu.lst. So it needs to be "configfile /boot/grub/menu.lst)


> an i not just edit it right in the grub menu when i boot up?

Yes, but you would have to do it every time you boot into ubuntu. There must be some editor that  works. Did you  try nano?

(Oops, didn't see rsambuca last post)

---

### Post by doctorgreg on 2007-11-25
ok i have replace the line now what do i do to save it

---

### Post by meierfra on 2007-11-25
If you are using nano: "Ctrl O"   "Ctrl X"  (Press the Ctrl key and the O key simaltaneously, then the Ctrl and X key)

---

### Post by doctorgreg on 2007-11-25
I hit CTRL 0 and it says file name to write: / boot/grub/grub.config
am i on the right track............i don't want to save the wrong thing

---

### Post by meierfra on 2007-11-25
> / boot/grub/grub.config

are you sure that it didn't say "/ boot/grub/grub.conf" ?  Anyway saving it to the wrong file won't hurt. So just go ahead. You might look at  "/ boot/grub/grub.conf" again after you closed it, to make sure you really changed the file,

---

### Post by doctorgreg on 2007-11-25
its not saving for me...........everytime i go back in it still says chainloader +1

---

### Post by rsambuca on 2007-11-25
It is Control-O (as in oh, not zero) to save.

---

### Post by doctorgreg on 2007-11-25
Ya that is what i am doing.  when i hit Ctrl X should it close the window or will it remain open

---

### Post by doctorgreg on 2007-11-25
and do i need caps on?

---

### Post by meierfra on 2007-11-25
> and do i need caps on?

No.

> a that is what i am doing. when i hit Ctrl X should it close the window or will it remain open

It should close



Just double checking: 
1) You typed "su"  to become root?
2) You open the file via "nano /boot/grub/grub.conf"? 
3) You changed  "chainloader +1"  to "configfile /boot/grub/grub.conf"
4) You did "Ctrl 0" "Enter" "Ctrl X"  to save the file and exit?

---

### Post by doctorgreg on 2007-11-25
aahhhh it worked now.........cuz nobody told me to hit enter in between the ctrl O and Ctrl X..........thank you very much everyone..........i will now reboot and see if I can log into Ubuntu.

---

### Post by doctorgreg on 2007-11-25
Now I get Error 15 File Not Found?

---

### Post by meierfra on 2007-11-25
Post the output of

```
ls -l /boot/grub
```

and 

```
 cat /boot/grub/grub.conf
```

---

### Post by doctorgreg on 2007-11-25
cgz@localhost ~ $ ls -l /boot/grub
total 468
-rw-r--r-- 1 root root     30 2007-11-24 20:42 device.map
-rw-r--r-- 1 root root   7904 2006-08-20 17:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7744 2006-08-20 17:31 fat_stage1_5
-rw-r--r-- 1 root root   7040 2006-08-20 17:31 ffs_stage1_5
-rw------- 1 root root    944 2007-11-25 01:24 grub.conf
-rw-r--r-- 1 root root   1624 2006-08-20 17:31 grub.conf.sample
-rw------- 1 root root    943 2007-11-25 00:53 grub.conf.save
-rw------- 1 root root    943 2007-11-25 01:02 grub.conf.save.1
-rw------- 1 root root    943 2007-11-25 01:21 grub.conf.save.2
-rw-r--r-- 1 root root   7040 2006-08-20 17:31 iso9660_stage1_5
-rw-r--r-- 1 root root   8480 2006-08-20 17:31 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2007-11-24 20:45 menu.lst -> ./grub.conf
lrwxrwxrwx 1 root root      9 2007-11-24 20:29 menu.lst.rpmsave -> grub.conf
-rw-r--r-- 1 root root   7200 2006-08-20 17:31 minix_stage1_5
-rw-r--r-- 1 root root   9504 2006-08-20 17:31 reiserfs_stage1_5
-rw-r--r-- 1 root root  26262 2006-08-20 22:22 splash.xpm.gz
-rw-r--r-- 1 root root    512 2006-08-20 17:31 stage1
-rw-r--r-- 1 root root 102748 2006-08-20 17:31 stage2
-rw-r--r-- 1 root root 102748 2006-08-20 17:31 stage2_eltorito
-rw-r--r-- 1 root root 102236 2006-07-25 13:18 stage2.old
-rw-r--r-- 1 root root   7392 2006-08-20 17:31 ufs2_stage1_5
-rw-r--r-- 1 root root   6592 2006-08-20 17:31 vstafs_stage1_5
-rw-r--r-- 1 root root   9224 2006-08-20 17:31 xfs_stage1_5

---

### Post by doctorgreg on 2007-11-25
localhost cgz # cat /boot/grub/grub.conf
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,3)
#          kernel /boot/kernel-genkernel real_root=UUID=f2ea0f65-d2d1-4180-bb5d-07d0bbfe1c67
#          initrd /boot/initramfs-genkernel
#boot=sda
default=1
timeout=6
splashimage=(hd0,3)/boot/grub/splash.xpm.gz
title Sabayon Linux x86 3.4 Mini Edition
        root (hd0,3)
        kernel /boot/kernel-genkernel-x86-2.6.22-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=f2ea0f65-d2d1-4180-bb5d-07d0bbfe1c67  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi
        initrd /boot/initramfs-genkernel-x86-2.6.22-sabayon
title Ubuntu Gutsy GIbbons 7.10
        rootnoverify (hd0,2)
        configfile /boot/grub/grub.conf
title Windows Vista
        rootnoverify (hd0,0)
        chainloader +1

---

### Post by meierfra on 2007-11-25
Change "rootnoverify (hd0,2)"  to "root (hd0,2)"

---

### Post by doctorgreg on 2007-11-25
do you want me to reboot now and see if it worked

---

### Post by meierfra on 2007-11-25
Sure

---

### Post by doctorgreg on 2007-11-25
well that didn't work........do you think the (hd0,2) could be a diff number like 3 or 4?

Device Boot Start End Blocks Id System
/dev/sda1 * 1 7462 59935648+ 7 HPFS/NTFS
/dev/sda2 10068 10198 1052257+ 82 Linux swap / Solaris
/dev/sda3 10201 12161 15751732+ 83 Linux
/dev/sda4 7463 10067 20924662+ 83 Linux

in this list number 2 is swap........but i don't know if these numbers are diff.

---

### Post by meierfra on 2007-11-25
(hd0,2) is correct (grub starts counting at zero). But I  screwed up. Ubuntu uses "/boot/grub/menu.lst". So change

"configfile /boot/grub/grub.conf" to "configfile /boot/grub/menu.lst"

Reboot and it really should work this time

---

### Post by doctorgreg on 2007-11-25
should i change the root back to rootnoverify as well?

---

### Post by meierfra on 2007-11-25
No

---

### Post by doctorgreg on 2007-11-25
Well it worked flawlessly.  I am in ubuntu right now....thank you very much eveyone who helped out. :)

---

### Post by meierfra on 2007-11-25
Good news. Sorry for the "menu.lst"-"grub.conf"-mix up. I got confused between Ubuntu and Sabayon.

---

### Post by doctorgreg on 2007-11-25
hey man not a problem...cheers

---

