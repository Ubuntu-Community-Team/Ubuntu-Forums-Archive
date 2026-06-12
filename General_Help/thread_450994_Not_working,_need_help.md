---
title: "Not working, need help"
date: 2007-05-21
forum: General Help
---

### Post by r3n0 on 2007-05-21
Ive been following these instructions

This is EXPERIMENTAL SOFTWARE and it comes with NO GUARANTEE whatsoever. It is intended for developers only. See below for license details (GPL2)

INSTRUCTIONS:

1) Extract the contents of the archive into C:\wubi
2) Generate the disk image files the appropriate size within c:\wubi\disks
3) Copy all the files in wubi\grub\ to C:\
4) Download Ubuntu Feisty HERD-4 ALTERNATE ISO and put it in C:\wubi. The link is:
[http://cdimage.ubuntu.com/releases/feisty/herd-5/feisty-alternate-i386.iso](http://cdimage.ubuntu.com/releases/feisty/herd-5/feisty-alternate-i386.iso)
5) Add the line C:\grld="Ubuntu" to C:\boot.ini
6) Reboot and select Ubuntu


My problem is i dont boot off my C drive, 

my C is actually a partition of my H drive and i have h:\wubi

so how does the installation differ?

do i still edit the boot.ini in my C drive?

thanks

also my HDD is NTSF

---

### Post by tinybit on 2007-05-21
> 5) Add the line C:\grld="Ubuntu" to C:\boot.ini

A typo?

C:\grld ------------> C:\grldr

You should use the Boot.ini file in the same dir as the NTLDR file.

Try to append the line C:\grldr="Ubuntu" to H:\boot.ini

Note: Don't use H:\grldr="Ubuntu" in H:\boot.ini. See readme for why.

The "C:\" in "C:\grldr" is mandatory. The drive letter C cannot be changed to other letters.

---

### Post by r3n0 on 2007-05-22
well, i really want to try wubi..

is there a link you can give me with instructions exactly how to install it?

I followed the previous instructions and edited the boot.ini file and everything
when i booted up Ubuntu my computer says it cannot locate the correct files
:/


also there is no    H:\boot.ini file
only    C:\boot.ini

---

### Post by ago on 2007-05-22
What happens if you download wubi from the website and let it download the ISO?
There is no need to follow any instruction, those were for devs.

---

### Post by r3n0 on 2007-05-24
I got it to work

i made a stupid misatake


So it looks great! i like it a lot
1 problem

i have a creative labs x-fi sound card with the new chip architecture with no linux support right now\

:(

i ould plug it in my mobo but no 5.1 :(



does anyone have a link where i can read about
*why should i switch to Linux if i have always used windows?*

---

