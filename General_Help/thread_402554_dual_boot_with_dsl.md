---
title: "dual boot with dsl"
date: 2007-04-05
forum: General Help
---

### Post by bmenge on 2007-04-05
I am trying to install install dsl (damn small linux) as a dual boot.  I used gpart to set up a partion for it and installed it on it.  The only problem is I couldn't get ubuntu to boot.  I final deleted the new partion and had to use the ubuntu live cd to fix grub.  How can I get dsl and ubuntu working?

Most of the post about dual boot are for windows and one linux distro I am sure some lots of people have run two linux at one point or another.

---

### Post by LaurelLynn on 2007-04-05
I had a similar problem with knoppix about a year ago.

I believe the problem is that dsl uses lilo and it has wiped out the Grub bootloader without adding an entry for Ubuntu to lilo.

I know there is an easier solution, but I think I solved the problem by backing up the knoppix install to a USB external hard drive using dd. Then I installed Ubuntu on the knoppix partition to get Grub back. Restored the knoppix backup to the partition.

Then I recall Grub booted off the /boot/grub/grub.lst of my original Ubuntu install.  Which I editted to add knoppix.

Time consuming, but I remember it working.

First I would look for ways to change lilo, or install grub without the reinstall. I know there is a how-to somewhere around here.
Laurel Lynn

---

### Post by zvacet on 2007-04-06
Why didn´t you try to fix grub with CD before you deleted partition?

---

### Post by bmenge on 2007-04-06
Because my wife wanted the computer back to ubuntu and I was in a panic I guess.  I just didn't do enough research before hand.  I did try to reinstall dsl with a frugal install with grub but had no luck thats when I deleted the partion.  I will get a thread going on the dsl forum( I think people are a little more friendly here).:-$

---

### Post by bmenge on 2007-04-08
ok I had a little time today to get this working with grub after I reinstalled dsl and booted with a grub boot disk very easy 

if anyone else has finds this in a search.  I installed dsl on new partion ran lilo(there is a frugal install in the apps/tools folder with automated grub but I had no luck with this).  Then I booted the grub.iso cd(google search) 

$ find /boot/grub/stage1

This gives you the info for grub

mine was hd0,0 I think this if fairly common 
enter the result in next line
$ root (hd0,0)

$setup (hd0)

then remove cd and reboot

you could use the live cd and not download an iso of grub if you wanted.  I just happened to have one already.

---

### Post by bmenge on 2007-04-08
If you want to make ubuntu load as the default os you will need to edit the lilo file.  /etc/lilo.conf

run the lilo comand I did it in dsl I don't think you could do it in ubuntu but I don't know for sure

$ sudo nano /etc/lilo.conf 

once in the file you change the default to the proper dirve that has the grub with ubuntu on it.

save and exit the run lilo

$ sudo lilo

reboot 

you should make a copy of the /etc/lilo.conf just in case you mess it up so you can fix it from the live cd.

---

