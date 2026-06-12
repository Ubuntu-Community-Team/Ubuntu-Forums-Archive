---
title: "Black Screen after log in Desktop ?!"
date: 2017-03-03
forum: General Help
---

### Post by fairbird on 2017-03-03
My ubuntu 14.04 works just fine before update some files ..
```
No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

```
And after update that files I got black screen after login to desktop.
Her my VGA Card info
```
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)

```
I have tried more solutions but nothings solve the problem ..

Please any advises ?!

Thank you

---

### Post by yoshii on 2017-03-03
try adding "NOMODESET --- NOMODESET" to the kernel boot parameters during bootup.   And then after boot, edit grub to include the same kernel boot parameter ("nomodeset").   While you're at it, you can add "threadirqs" and get rid of "splash" and "quiet".  That way, you can see what's crashing or not crashing during boot and have some more clues.   Hopefully this helps.    Somebody else, please explain how to edit the grub, I forget the pathname of the file.  Is it /etc/grub? or /etc/default/grub?  I forget.   Be sure to do a sudo update-grub afterwards though.

---

### Post by mörgæs on 2017-03-04
/etc/default/grub

---

### Post by fairbird on 2017-03-05
I have tried that method but doesn't helped ...The problem comes after...If I login to win 7 and then return back to Ubuntu I got black screen.Thank you

---

### Post by fairbird on 2017-03-06
Ok..If I edit grub files and replace nomodeset, ubuntu boot again but I can changes resolution from displays option (How can fix this) ?!
And here is my grub
Thank you
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by mörgæs on 2017-03-07
Have you considered a fresh install of 16.10? New hardware like Skylake would prefer new software.

---

### Post by fairbird on 2017-03-07
Thank you for answer ..

I'm using ubuntu 14.04 to build Dreambox E2 images ..
So..
ubuntu 12.04 to much old and doesn't help
ubuntu 15.04 I have some problem with Graphics always crashes
ubuntu 16.04 really good but doesn't full compatible with E2 building .

---

### Post by mörgæs on 2017-03-07
And 16.10?

---

### Post by fairbird on 2017-03-07
That version did not try yet.
But I am afraid that I do a formate and install the 16.10 and after fatigue does not help me to build images such a 16.04... (because some images need compatible distro to build it with kernel 2.16.8 and glic2.19) by ubuntu 16.04 I've got too much errors warring with compiling.
14.04 with me 90% perfect just this issue I have trouble.

Thank you

---

### Post by fairbird on 2017-03-08
I have install ubuntu 14.04 again on other driver bu using (nomodeset) with install >>
After finish install and boot ubuntu also I can not change resolution from displays I got only 1024X768(4:3).
Also I have edit grub file and remove (nomodeset) and update-grub and same issue I can not get 144X900(16:10)

How can I fix this issue ?!

---

### Post by mörgæs on 2017-03-09
I don't use old software so I can't help you more, sorry. 

I suggest that you focus on compiling Dreambox E2 in 16.10 and not on getting better graphics in the stale 14.04.

---

### Post by fairbird on 2017-03-09
Thank you ..
But Please read this replay from openpli team ..
[https://forums.openpli.org/topic/49019-witch-is-the-best-version-of-fedora-to-build-an-image/?view=findpost&p=680579](https://forums.openpli.org/topic/49019-witch-is-the-best-version-of-fedora-to-build-an-image/?view=findpost&p=680579)

---

### Post by mörgæs on 2017-03-10
Yes, I consider this your real problem for which you need help from the forum. 

I am not good in compiling so can't do much here, sorry.

---

### Post by fairbird on 2017-03-10
Just I want to know Any chance to remove drivers for my VGA card and install again ?!
> 00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)
Because my ubuntu 14.04 was worked just find before 3 weeks ago and after that the problem happens to me.

Thank you

---

### Post by fairbird on 2017-03-10
[COLOR=#333333][FONT=&quot]I've solved the problem ..[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Change HDMI cable and reinstall ubuntu 14.04 again..[/FONT][/COLOR]

---

