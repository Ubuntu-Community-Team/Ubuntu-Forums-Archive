---
title: "[SOLVED] copying dvd iso"
date: 2008-06-10
forum: General Help
---

### Post by logos34 on 2008-06-10
How do you copy .iso from a dvd, but only the USED disc space?

I have a copy of ubuntustudio-8.04-alternate-amd64.iso (1.1 GB) on dvd, but when I use the command

dd if=/dev/dvd of=ubuntustudio-8.04-alternate-amd64.iso 

I get a huge 4.4 GB raw iso.  

Is it because I left off the 'bs=4096'?

(I need to copy it to hard disk to free up the dvd+rw for other uses)

---

### Post by sdennie on 2008-06-10
I would imagine that genisoimage can do this.  I've not looked into how (the man page is very dense) but, that might be something to look into.

---

### Post by mc4man on 2008-06-10
> I get a huge 4.4 GB raw iso. This is another example of how linux burning apps _can_ do an improper job.
Quick test - took a dvd-rw burned the sgd iso (2.4mb) with imgburn then dd'ed it. End result a 2.4mb iso
Took the dvd-rw used cd/dvd creator to burn the same iso, dd'ed it. End result a 4.3gb iso
somehow the linux burning app(s) are making the whole dvd-rw appear as one big fs

edit: took the same cd/dvd creator disk ,used imgburn in read mode - 2.4mb iso
maybe some linux creating/burning apps aren't doing a proper job of deleting before burning and dd is continuing to read till it reaches either the end of disk or the end of largest amount _ever _written

---

### Post by logos34 on 2008-06-10
this is really weird...maybe there's some other gui burning app out there that can do it properly?  I've never encountered it because I hardly ever have need to mess with dvd-sized isos.  

I have ISO Master, but that doesn't seem to handle copying...

---

### Post by mc4man on 2008-06-10
if you didn't delete Imgburn use that in read mode to copy your -rw
i'm gonna boot into hardy later and test Brasero, ect.
It appears this only affects -/+rw media, write once +/-r the data size is correctly calculated 
The copy disk function (gutsy) is even worse than dd, no matter what burned it or the data size it creates a 4.3gb iso

---

### Post by logos34 on 2008-07-26
Ok, I found the answer.  

Apparently some padding was added to the end of the disc when I burned it to dvd.  In order to copy back only the iso, you do:
> 
isoinfo -i /dev/dvd -dLook for this part:

> Logical block size is: xxxx
Volume size is: **XXXXXX**Plug it into the dd command:

> dd if=/dev/dvd of=file.iso bs=xxxx count=**XXXXXXX**Run md5sum on file.  It should match the original.

Specifically n my case:

> $ isoinfo -i /dev/dvd -d
CD-ROM is in ISO 9660 format
System id: LINUX
Volume id: Ubuntu-Studio 8.04 amd64
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
[COLOR=Blue]Logical block size is: 2048
Volume size is: 571661[/COLOR]
El Torito VD version 1 found, boot catalog is in sector 3716
Joliet with UCS level 3 found
Rock Ridge signatures version 1 found
Eltorito validation header:
    Hid 1
    Arch 0 (x86)
    ID ''
    Key 55 AA
    Eltorito defaultboot header:
        Bootid 88 (bootable)
        Boot media 0 (No Emulation Boot)
        Load segment 0
        Sys type 0
        Nsect 4
        Bootoff E7D 3709

$ [COLOR=Black][B]dd if=/dev/dvd of=isos/ubuntustudio-8.04-alternate-amd64.iso bs=2048 count=[COLOR=Blue]571661

[/COLOR][/B][COLOR=Black]571661+0 records in
571661+0 records out
1170761728 bytes (1.2 GB) copied, 202.103 s, 5.8 MB/s

$ md5sum [/COLOR][/COLOR][COLOR=Black]/isos/ubuntustudio-8.04-alternate-amd64.iso[/COLOR]48bc91bc0e0652e68186594338516e71 ubuntustudio-8.04-alternate-amd64.iso
You can also use **K3b** disc to disc copy function--just tell it to create the image only and set the output directory:
> 
>Tools>Copy DVD>Options tab>"**Only create image**">Image tab>"Write image file to" (select dir.  Default is /tmp)

---

