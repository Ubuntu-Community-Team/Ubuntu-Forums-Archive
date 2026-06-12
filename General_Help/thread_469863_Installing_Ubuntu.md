---
title: "Installing Ubuntu"
date: 2007-06-10
forum: General Help
---

### Post by Kzap333 on 2007-06-10
[SIZE="3"]I have diced to install Ubuntu as a second operating system on my computer (it will actually be my main system if I can get the internet to work) I was wondering I have 2 hard drives in my computer at the moment and one is just use for storage. My question is if I install Ubuntu onto the second hard drive will I lose all my windows programs and folders?[/SIZE]

---

### Post by taurus on 2007-06-10
If you install Ubuntu on the second harddrive, then all your stuff on that harddrive will be erased.  So, backup your stuff first before you install Ubuntu on that second harddrive.

---

### Post by mikewhatever on 2007-06-10
> **Kzap333 said:**
> [SIZE="3"]I have diced to install Ubuntu as a second operating system on my computer (it will actually be my main system if I can get the internet to work) I was wondering I have 2 hard drives in my computer at the moment and one is just use for storage. My question is if I install Ubuntu onto the second hard drive will I lose all my windows programs and folders?[/SIZE]

No you will not. However, accidents do happen, so back up everything important. I do not understand what programs are doing on the second HDD, but whatever. Having Ubuntu and Windows on different HDDs takes a bit more work, so read here [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
Follow this guide for the installation [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by Wim Sturkenboom on 2007-06-10
If you have a 'normal' windows installation, windows and the programs will be on C. If your second HD is only used for storage, you will only loose what is on there when you install Ubuntu. The C drive will not be touched if you do it correctly.
So just check, backup if necessary and install.

Please note that in Linux, drives are called hda/hdb or sda/sdb and not C/D

Good luck

---

### Post by Kzap333 on 2007-06-10
Okay we have contradicting points here:
I do install programs on HDDB (or D drive) becasue HDDA (C drive) is low on space.
Just to be on the safe side I will back every thing up on my laptop.
Thanks for you're help.** Long Live Ubuntu!**
One more quistion will I be able to acess the second hard drive in Windows when I have Ubuntu on it?

---

### Post by taurus on 2007-06-10
You can read and write to ext3 (default Ubuntu filesystem) with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by trippinnik on 2007-06-10
yeah, but you'll need to use a driver to access ext3fs, like this: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Kzap333 on 2007-06-10
> You can read and write to ext3 (default Ubuntu filesystem) with [http://www.fs-driver.org](http://www.fs-driver.org).
> yeah, but you'll need to use a driver to access ext3fs, like this: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
Thank you this is very help full, I shall back up all the files onto my laptop now, should be fun as I only have 2 2GB pendrives and no wireless to copy 65GB of files over I'm sure I'll find a way.

---

### Post by tpg on 2007-06-10
If you have ethernet ports on both, how about an ethernet crossover cable?

---

### Post by Kzap333 on 2007-06-10
> **tpg said:**
> If you have ethernet ports on both, how about an ethernet crossover cable?
Thats what I am looking for at the moment thanks we have loads I just need to find one that actually WORKS.:D

---

### Post by Kzap333 on 2007-06-11
Just asking if I installed Ubuntu as a second operating system on my first HDD would I lose my files?
I am just have a bit of troble backing up the files I could write them to DVD but I don't want to if I don't have to as it would take up about 3 - 4 DVDs of just the impornt stuff.

---

### Post by taurus on 2007-06-11
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Wim Sturkenboom on 2007-06-11
Just make the backup if the data files are important to you. Things just can go wrong (user mistake, power failure, ...).
Backing up programs is not usefull in my opinion; if something goes wrong, you have to re-install the program(s).

---

### Post by Kzap333 on 2007-06-12
> **Wim Sturkenboom said:**
> Just make the backup if the data files are important to you. Things just can go wrong (user mistake, power failure, ...).
Backing up programs is not usefull in my opinion; if something goes wrong, you have to re-install the program(s).
I have given up on finding a cable I have just coppied my most importent things to DVD (I need to do it any way) with a realy high compresion it still takes up 3 DVDs.
The whole thing that started my Linux hunt up again was a mager HardDrive failer and I had to re-install every thing, and I meen every thing Windows XP and every thing. I actually could not be botherd to install MS office again so used OpenOfffice I was only using freeware and opensorce stuff apart from Adobe Premire. So I thought why not switch to Linux for good at least for most stuff (not work though).

*(sory again about spelling I can't be botherd to copy this whole thing back into OpenOffice Wrighter just to check spellings)*

---

### Post by mikewhatever on 2007-06-12
> sory again about spelling I can't be botherd to copy this whole thing back into OpenOffice Wrighter just to check spellings)
What about Firefox? It does the spell check thing for me with the English dictionary installed. Good luck with Ubuntu installation.

---

### Post by Kzap333 on 2007-06-12
> **mikewhatever said:**
> What about Firefox? It does the spell check thing for me with the English dictionary installed. Good luck with Ubuntu installation.
Thanks I have firefox and I have put autospell checker on but it does not seem to be working (silly windows soon I be rid of you!).
I am just burning the last disk now.

---

### Post by Kzap333 on 2007-06-13
It would not let me partion my HardDrive I tried multiply times in both Gnome Partioner and the Install apilaction but it kept coming up with some error.
Aw well I'll just have to wait for my dad to come home from work (on friday).

---

### Post by Kzap333 on 2007-06-15
I think it is not workign because my drive show up as read only on Ubuntu but on windows they are fine. Does anyone know what to do if someone has already asked this point me in the right direction.
Many Thanks.
P.S. I have sucsessfully managed to partion a 30GiB section of my second hard drive the problem is installing Ubuntu.

---

### Post by Kzap333 on 2007-06-16
> **Kzap333 said:**
> I think it is not workign because my drive show up as read only on Ubuntu but on windows they are fine. Does anyone know what to do if someone has already asked this point me in the right direction.
Many Thanks.
P.S. I have sucsessfully managed to partion a 30GiB section of my second hard drive the problem is installing Ubuntu.
I'm downloading the text based installer I'll se if that works any better.

---

### Post by j.miller565 on 2007-06-16
Good luck. Hope all goes well.

---

### Post by Kzap333 on 2007-06-16
I am able to install Ubuntu but I don't have an internet conection this is okay as I can do browsing in Windows and every thing else in Ubuntu but iis there any where with a list of all the supported Ubuntu aplications so I can download them in XP and put them on a CD for Ubuntu. I'm sure there must be a place I just don't know where and I don't realy wont to copy the names down of all the programs I want to download.
Many thanks you guys on the forums have been loads of help.

---

### Post by Kzap333 on 2007-06-17
DONE!!!
WAAHOOOO!!!
I can't bleave how happy I am.
**looks around**
Where is everybody.

---

