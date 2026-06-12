---
title: "Ubuntu see one of my partition as &quot;swap&quot; ??"
date: 2007-04-18
forum: General Help
---

### Post by harry000 on 2007-04-18
Hello,

Ubuntu see one of my partition as "swap" partition; but the that partition is actually NTFS!!

[B][ if u dont want to read the whole story below.. i will cut it short here.... i ran swapon /dev/hd5 command and by mistake.. mounted a NTFS partition as swap.... ubuntu is still seeing that partion as swap, although not using it ]
[/B]

It all happened like this - for some reason, i had problems wit my "real" swap partition and Ubuntu wasnt recognizing it, so I tried to remounted the swap with "swapon /dev/had5" command.... but i made a mistaker here... i put the wrong partition here.... hda3 
and then.. after that... linux started showing this partition as swap.. althought.. not using it

everything was fine in Windows with that partition. And in between I had to reinstall Ubuntu for some reason. 
Everything was still okay.

but then... for some reason, when I restarted the computer, grub gave me error 17... couldnt boot into linux or windows... so I inserted windows CD.. and fixed MBR there...

so.. i was able to boot into windows.. but now.. I had another problem... the drive that linux see as swap, was missing..... (i had all the picture in thta drive)... so.. I tried recovering the partition and data... and did it. everything was normal again....

i reinstalled grub and boot into linux... Now.. it still see that partition as swap.. uhhh...
i also tried booting with live cd and ran the "gparted" there... it shows it swap too :-(

So, basic point is that...linux is mis-recognizing the partition swap...

---

### Post by amohanty on 2007-04-18
Can you post the contents of /etc/fstab

AM

---

