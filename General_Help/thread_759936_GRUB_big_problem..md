---
title: "GRUB: big problem."
date: 2008-04-19
forum: General Help
---

### Post by bonezzzz on 2008-04-19
I had ubuntu installed a while back and wasn't using it... everytime my computer would boot up id select windows so one day i decided to get rid of ubuntu.  On windows i selected the partition that Ubuntu was on and i formatted the hard drive to an NTFS file system.  Now each time i start the computer i have a grub 17 error and cant get passed it.  also my computer doesnt recognize that i have any kind of cd drive this was a problem from a while back.  Can anybody help me get rid of the grub error or at least help me get access to an operating system by helping me figure out why it doesnt recognize any drivees.   thanks in advance! much love!

---

### Post by bodhi.zazen on 2008-04-19
You have to restore the windows boot loader

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by bonezzzz on 2008-04-19
> **bodhi.zazen said:**
> You have to restore the windows boot loader

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

my computer is not recognizing my cd drives so I cant boot into a windows cd.

---

### Post by bodhi.zazen on 2008-04-19
How did you install Ubuntu then ?

What is wrong with your CD-ROM ? Check the BIOS and make sure it is set to boot from the CD-ROM.

Short of that you would need to try booting from floppy, although I am not sure you can restore the windows boot loader from floppy.

The other option is to make a grub floppy or use supergrub and manually boot.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by bonezzzz on 2008-04-19
> **bodhi.zazen said:**
> How did you install Ubuntu then ?

What is wrong with your CD-ROM ? Check the BIOS and make sure it is set to boot from the CD-ROM.

Short of that you would need to try booting from floppy, although I am not sure you can restore the windows boot loader from floppy.

The other option is to make a grub floppy or use supergrub and manually boot.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

at the time when i installed it, it was working.  both my dvd rom drive and cdrw drive just died and stopped being recognized by my computer.  They still power up though.  I Don't have a floppy drive but i guess that would be pretty easy to get my hands on.

---

### Post by bonezzzz on 2008-04-20
Ok, forget the floppy. what if I put my hardrive in another computer boot into a windows cd from there and restore the windows boot loader thing from there?  Do you think that would work?

---

### Post by bonezzzz on 2008-04-20
alright guys i fixed this by sticking my hardrive in a computer with a working cd drive and booting into windows with a CD going into the repair console and reinstalling the windows boot loader by using the following two commands
fixmbr
fixboot
Now i have a 10 gb NTFS backup partition instead of ubuntu.  Thanks alot guys!

---

