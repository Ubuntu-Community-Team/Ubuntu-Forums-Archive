---
title: "[SOLVED] quad boot grub problem"
date: 2008-04-28
forum: General Help
---

### Post by LashSilence83 on 2008-04-28
I was running ubuntu 7.10, fc8, and xp all booting fine with the help of qgrubeditor... That is until tonight I tried to install kubuntu 64-bit on a spare partition and even though I don't recall any option to install GRUB like previously seen on other installs, it seems to have totally screwed up all of my grub entries and now the only one that works at all is ubuntu gutsy. I've already tried changing various things in the grub config but nothing seems to be helping as I'm still very new to this whole thing. Any suggestions?

---

### Post by Ralphie on 2008-04-28
You can access kubuntu by logging out (shortcut: ctrl+alt+backspace)
and then changing the session.
There should be a "session" button on the log-in screen somewhere, after pressing it you will be prompted with all different versions of ubuntu you might have. 

As far as the grub goes, the only entries you need are the different OSes, but not the various ubuntu flavors, because like i said you can do that at the log-in screen.

---

### Post by Ralphie on 2008-04-28
oops I realize I didn't fully answer the question, 

I edit my grub by hand, so I don't know the program you are using, but are you given options for xp a fc8 at all? or are they not there all together? 

can you add them with the program? if not you will have to do it by hand

---

### Post by LashSilence83 on 2008-04-28
I had no idea about the multiple sessions being available from just one grub entry. Also, the xp and fc8 entries are still there but whats really weird is that it changed the name of the entry for fc8 from "Fedora Core 8" to "FC8 werewolf" and now when I try it I get a kernel panic. I have already went into my /boot dir and tried to give it the correct info for booting fc8 but I still get the panic every time. As far as the xp entry, I have screwed it up so many times in the past that I was able to fix it right away(not that I even use it anymore :) ). The main thing I'm trying to figure out is why it did the following things: 
1. added a few extra ubuntu entries for generic and rescue options and only one of them works and boots ubuntu gutsy the same as it always did. 
2. changed the name and apparently the boot info for my fedora entry rendering it useless until I find out where the issue is
3. switched the order around for all the entries :confused:

Also, I do understand how to edit the grub by hand to some degree and I'm beginning to think that the program I use sucks and only complicates things. 
Sorry for being so verbose about this, I'm not sure how else to convey whats happening.

---

### Post by LashSilence83 on 2008-04-28
I just realized that I may have failed to mention that I'm trying to make 32 and 64 bit versions of ubuntu/kubuntu co-exist which I'm thinking may not work as far as the logging out and changing session thing goes. I'm wondering if I need to make separate GRUB entries for this. Has anyone done this already so as to know what's in store for me?

---

### Post by Ralphie on 2008-04-28
Yes, I would think you would have to have seperate grub entries for  what you are trying to do, I have not messed with that sort of thing personally, though.

The names of the boot options are not important, you can name those whatever you want, what is probably the issue is the 
root (hdx,x) option.
hdx is the hard drive number (The first being 0) and the second x is the partition number (again the first being 0). These two numbers should point to the place you have your different OS's. 

Could you post what your menu.lst has (just the relevant parts?)
and some info on your hdds and partitions? 

Or maybe now knowing this, you can just troubleshoot it yourself. Whichever is easiest! :D

---

### Post by LashSilence83 on 2008-04-28
here goes:

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=bf9494ed-c95e-4387-8841-3c769c8a277b ro quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

title Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-rt  root=UUID=bf9494ed-c95e-4387-8841-3c769c8a277b ro single
initrd /boot/initrd.img-2.6.22-14-rt

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=bf9494ed-c95e-4387-8841-3c769c8a277b ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=bf9494ed-c95e-4387-8841-3c769c8a277b ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Fedora Core 8
root (hd1,2)
kernel (hd1,2)-1/boot/vmlinuz-2.6.23.1-42.fc8 root=UUID=b3039563-fa42-4345-afe8-7f16212d12e3
initrd (hd1,2)-1/boot/initrd-2.6.23.1-42.fc8.img
quiet


I installed 64-bit Kubuntu 7.10 on hd0,1 if that helps at all. So it has no   grub entry but when I look through my computer in nautilus the partition for it shows up so I know it's there at least. Also, the entry for fc8 is the new one I tried to set up but it doesn't work. Also, can I just get rid of the "other operating systems" part without it doing any damage?

---

### Post by Ralphie on 2008-04-29
I'm sorry but I can't help  you with adding kubuntu 64-bit to the grub, I am not sure of all the options and paths to set, perhaps someone else knows how? Is it not showing up while changing sessions at all? This is the only way I personally know how to use different ubuntu versions.

As far as getting windows to work, make the entry look like this:

```
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

This *should* fix it.
If not, try adding:
```
map (hd0) (hd0)
map (hd0) (hd0)
```
To that list. But I don't think it is necessary since windows is on your first drive.

*edit*
Oh! I forgot, you can remove "other operating systems" from the file, what I suggest doing is commenting it out by adding a "#" before the "title" and "root" options for that line. This will make it easier should you decide you want it again.

---

