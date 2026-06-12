---
title: "Configuring Grub Boot Loader????"
date: 2006-11-24
forum: General Help
---

### Post by gwilki5691 on 2006-11-24
Hi All, Does anyone know how to or if it's possible to modify the way the Grub Bootloader works?
Unfortunately I have to use Windows at work so I run WinXP and Edgy on my laptop. Grub currently defaults to Ubuntu on every boot and when I am at work this becomes a bit of a pain having to manually select Windows everytime. The software I use at work on Windows means that I have to reboot 5-6 times during the course of the day. Each time I reboot I have to be sat at my PC waiting for the Grub Loader to select Windows. More often than not I end up missing the Grub screen because I get a phonecall or an interuption and then it  boots into Ubuntu instead.](*,) 

I was therefore thinking that it would be better if Grub defaulted to the OS which was last booted. This would mean only having to re-select an OS when I want to change which one to use. Is this possible?:-k 

I am a fairly new Linux user so be gentle. :)

---

### Post by ozorba on 2006-11-24
First you need to write enable .boot/grub/menu.lst by issuing the following command from a terminal window.

sudo chmod a+w /boot/grub/menu.lst

then 

sudo gedit /boot/grub/menu.lst

got to the end of the file and you will see someting like:

--

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

----

Cut this and paste it to above this:

--

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

--

save the file and exit


then issue the follwing command from terminal window:

sudo chmod a-w /boot/grub/menu.lst

After reboot MS Windows will be your default OS.

--

OZ

---

### Post by rlozano on 2006-11-24
> **gwilki5691 said:**
> Hi All, Does anyone know how to or if it's possible to modify the way the Grub Bootloader works?
Unfortunately I have to use Windows at work so I run WinXP and Edgy on my laptop. Grub currently defaults to Ubuntu on every boot and when I am at work this becomes a bit of a pain having to manually select Windows everytime. The software I use at work on Windows means that I have to reboot 5-6 times during the course of the day. Each time I reboot I have to be sat at my PC waiting for the Grub Loader to select Windows. More often than not I end up missing the Grub screen because I get a phonecall or an interuption and then it  boots into Ubuntu instead.](*,) 

I was therefore thinking that it would be better if Grub defaulted to the OS which was last booted. This would mean only having to re-select an OS when I want to change which one to use. Is this possible?:-k 

I am a fairly new Linux user so be gentle. :)

just edit the grub menu and place the window OS loading script to be the first choice. :-k

---

### Post by gwilki5691 on 2006-11-29
Thanks, I will give it a try. :)

---

### Post by PacShady on 2006-11-29
I'd just like to add an important warning to remember when making this change to the menu.lst file:

MAKE SURE YOU PLACE THE REFERENCE TO WINDOWS ABOVE THESE LINE:

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

If you don't, the next time you update your kernel, it will delete the reference to Windows and you won't be able to boot into it AT ALL unless you can replace the Windows boot reference. Someone new to Linux is unlikely to be able to remember how to make this reference off the top of their head, and unless there's a backup menu.lst available, you'll have a hard time fixing that reference! So to save alot of headaches, PLEASE make sure you post the changes ABOVE the lines above.

'Shady

---

### Post by mcduck on 2006-11-29
this is not a good way to do it.

First, there is absolutely no need to chmod anything. Actually, better not do it.

1. Open menu.lst for editing with command 'gksudo gedit /boot/grub/menu.lst' (use gksudo with graphical apps and suo only with CLI apps!)

2. Pretty close to the start of the file (line 14) there is a line with 'default 0'. This is where you select the default boot option. 0 is the first entry in menu.lst, 1 is second etc. so change the number to point to your windows entry.

You can also set it to 'saved' and Ubuntu will always by default boot to the last used OS.

---

### Post by Rida17 on 2006-12-02
Hi...

can any one help me in modifying Grub??
i hv got an assignment on this...n i dun even know the basics of it... :(

---

### Post by the_forc3 on 2007-09-20
I am a complete noob, the top option worked fine for me thanks Oz!! but long winded but worked easy enough!

Mark.:guitar:

---

