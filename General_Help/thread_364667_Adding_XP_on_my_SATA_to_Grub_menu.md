---
title: "Adding XP on my SATA to Grub menu"
date: 2007-02-18
forum: General Help
---

### Post by deodeep on 2007-02-18
Hello all,

Here´s the scenario.

I had a 160GB SATA HDD that had 4 partitions with XP installed on C:

I got another HDD, a 40GB HDD from dad on which I have installed OpenSUSE 10.2 and Ubuntu.

How, while installing Ubuntu, it recognised SuSE and added it to the Grub Menu.

Now, i need to boot into XP for using VB 6.0.

The thing which I do now to boot into XP, whn both my HDDs are physically connected.

I goto BIOS and change the first HDD to SATA and boot into XP.

Is there any way I can succesfully add XP to grub menu ?

XP is on my SATA ( /dev/sda1 ) while grub is on my IDE.

I searched the forum and googled, and found that.

Adding:
---------------------------
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1
---------------------------

to grub should do the trick.. but there, the SATA is taken as hd1. I tried changing that, but doesnt work for me..

Any help ?


//EDIT:

I just need to know what I need to add to menu.lst

---

### Post by anaconda on 2007-02-18
I had almost the same situation and my menu.lst read as this:

title           Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader     +1

and.. well looks about the same.. execpt rootnoverify is better than just root..
What does the grup complain when you try to boot windows?

---

### Post by deodeep on 2007-02-18
Well,

It gives Error 23: Error while parsing number.

Shud I try adding
---------------------------
title Windows NT/2000/XP
map (hd0,0) (sd1,0)
map (sd1,0) (hd0,0)
rootnoverify (sd1,0)
makeactive
chainloader +1
---------------------------

to menu.lst ?

---

