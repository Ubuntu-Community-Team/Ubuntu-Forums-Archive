---
title: "How should I fix GRUB?"
date: 2007-05-14
forum: General Help
---

### Post by Kasper42 on 2007-05-14
Hi!

Somehow my GRUB has broke. I'm pretty sure this happened when my sister used my computer, she claims that she only got to the usual ubuntu login screen and not knowing my password to log in (I was out at the time) simply shut the computer down again. 

When I booted up my computer when I got back home, instead of being greeted by the usual GRUB screen it read:

```
GNU GRUB  version 0.96  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>

```

I have tried fixing this problem three different ways:

Firstly, I tried enterting the following at the GRUB prompt.

```
grub>root (hd0,2)
grub>setup (hd0)

```

However, this didn't work and it came up with an couple of failures, I can find these errors if it helps...

I then went on using the [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=home") and following these instructions...

> Download the Unofficial "Super Grub Disk." You can download Super Grub Disk as a cdrom iso, floppy disk image or an usb tar.gz.
Burn it to a CD, put it on a floppy, or install to a USB Disk. Whatever. Just get it on something bootable
Boot up the "Super Grub Disk"
Select your language
Select Linux
Select "Fix Boot of Linux (GRUB)"
Go back to first menu
Select Quit, and then reboot

This said it worked! Yet when I did reboot nothing seemed to have changed and the original screen appeared :(

My latest attempt was through the [Live CD method found here]("http://ubuntuforums.org/showthread.php?t=224351&") After mounting the correct partition, I followed the instructions and this said it worked too, but once again I was returned to the same screen after rebooting my computer.

Could somebody please give me any help of how to solve this? Or any ideas how GRUB broke in the first place without even logging in?

Thank you!

---

### Post by calraith on 2007-05-14
Could be impending doom for your hard drive.  There's a Windows program that would easily tell you whether this is the case, called [HD Tune]("http://www.hdtune.com/").  I dunno whether something similar exists in the Linux world or not.  I usually use [UBCD for Windows]("http://www.ubcd4win.com/") to diagnose this sort of thing.

Hey, when you get the grub> prompt, what happens when you type the following command?
```
find /boot/grub/stage1
```
Does grub confirm the location as (hd0,2)?

---

### Post by Kasper42 on 2007-05-15
I've fixed it and I am now posting from ubuntu again!

calraith, I did double check that (hd0,2) was correct using your method and it was.

I never really thought it was my HDD that could be failing as its only a year or so old. I didn't have windows installed on the computer so I googled around for a CD-R iso that could be used to check the HDD for errors, I came across the Maxtor Powermax (I have a Maxtor drive) and followed[ this guide. ]("http://forum.novatech.co.uk/viewtopic.php?t=500") Maxtor Powermax required an advanced scan of my disc and this took around 30/40mins, when it was done, it told me that I had errors in my disc and asked whether it should fix them. I chose yes and it told me the errors had been corrected. I rebooted the computer and the usual GRUB screen loaded :) Then I logged in with no errors at all.

Thanks calraith for the idea of the HDD being corrupt. I hope this helps somebody else out who has a GRUB failure seemingly at random rather than after installing a new OS or any other major change.

---

