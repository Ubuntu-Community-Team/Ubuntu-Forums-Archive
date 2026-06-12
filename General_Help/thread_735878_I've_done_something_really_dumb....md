---
title: "I've done something really dumb..."
date: 2008-03-26
forum: General Help
---

### Post by dibbler on 2008-03-26
hi i'm new to ubuntu and linux and have been having a play with 'gutsy' in a dual boot with preinstalled vista home premium.

my hdd is 160gb and i had gutsy in its own 20gb D: partition. i thought heck why don't i shrink my C: down smaller and then I can have an extra F: partition to store all my data and things which would then be accessible by both vista and gutsy.

So to cut along story short, using windows  I formatted D: Gutsy (yeh i know) and expanded my C:

I rebooted :(

As soon as grub started up I knew what I had just done...... I couldn't believe my dumbness!!!

So I do not have any recovery disks for vista just a silly recovery partition which of course I cannot get to!!! The 'puter is only about 2 months old and so I'm not too worried about the loss of data,  I have what I need on my main puter

So I guess you know what I'm gonna ask :)

1. Is there anyway I can get my vista to boot ?
2. If not how do I get to the vista recovery partition to do a reinstall?
3. Should I install gutsy on my C: which means I'll be able to access the vista recovery partition afterwards??

any suggestions gratefully accepted, 
TIA dibb

---

### Post by Kevbert on 2008-03-26
Hi. I found this...

To fix PC boot from the vista DVD, and then chose 'command prompt' and type

bootrec /fixmbr
bootrec /fixboot

Which basically writes the Vista boot loader back into the boot sector of the disk.

Now you need to find these files or borrow a DVD.

---

### Post by dibbler on 2008-03-26
thanks for that 'K' shall have a nosey round the net and see what i can find!

---

### Post by danwood76 on 2008-03-26
You can use the supergrub disk to recover the windows MBR.
This a free and legal way to do it ;)

---

### Post by dibbler on 2008-03-26
hi dan
i'm d/l  that now, i'm going thru the documentation too which all looks very scary...
i've never burned an iso before so looks like i'm in for a steep learning curve here :)
thanks for yr help...

---

### Post by dibbler on 2008-03-26
DANWOOD THANKYOU THANKYOU THANKYOU!!!

SuperGrub is SUPER and SO EASY
Gosh the wonders of Linux, i'm sure trying to do that with windows wouldn't have been as straight forward or painless.

Right then i'm off to reinstall gutsy and give it a real good go!!!!

I'm sure it won't be the last time you see me...:)

---

### Post by danwood76 on 2008-03-26
Well done.
Linux tools are simple and powerful ;)

---

