---
title: "File Recovery; Testdisc/photorec"
date: 2007-05-19
forum: General Help
---

### Post by schalicto on 2007-05-19
I'm a total noob.  I can not ephisize this enough.  I was playing with gparted and I accidently deleted the partition that contained all of my music and historical family photos.... dumb, right?  

That partition was an NTFS partition on a second harddrive.  Currently that drive has no partition on it and I am trying to recover the files on it.

Everything I find points me to testdisc and photorec however I don't have the first clue of how to use these programs.  I got the furthest using photorec however I got confused when it was asking me where I want the files to be put.  My goal is to put them on a third harddrive that is currently empty and formated in NTFS (I still use a lot of windows).

The reason that I am working on this primarily with Linux is that whenever these harddrives are installed I can't boot into windows... I think it has to do with a previous botched linux install that put the grub bootloader on a harddrive besides my primary one.

So if I say "pretty pretty please" will someone give me detailed instructions on how to use these programs?  Maybe even give me some help on AIM or if you live in Minnesota come over to my house?  Please?  I'll buy beer/coffee.

Alright, I'm done making a fool out of myself.  Please help me if you can.

-Josh

p.s. I've already searched the forums and read a few threads but I still don't get it.

---

### Post by schalicto on 2007-05-21
> **schalicto said:**
> I'm a total noob.  I can not ephisize this enough.  I was playing with gparted and I accidently deleted the partition that contained all of my music and historical family photos.... dumb, right?  

That partition was an NTFS partition on a second harddrive.  Currently that drive has no partition on it and I am trying to recover the files on it.

Everything I find points me to testdisc and photorec however I don't have the first clue of how to use these programs.  I got the furthest using photorec however I got confused when it was asking me where I want the files to be put.  My goal is to put them on a third harddrive that is currently empty and formated in NTFS (I still use a lot of windows).

The reason that I am working on this primarily with Linux is that whenever these harddrives are installed I can't boot into windows... I think it has to do with a previous botched linux install that put the grub bootloader on a harddrive besides my primary one.

So if I say "pretty pretty please" will someone give me detailed instructions on how to use these programs?  Maybe even give me some help on AIM or if you live in Minnesota come over to my house?  Please?  I'll buy beer/coffee.

Alright, I'm done making a fool out of myself.  Please help me if you can.

-Josh

p.s. I've already searched the forums and read a few threads but I still don't get it.

Bump.  Nobody can help me with this?

---

### Post by Herman on 2007-05-21
Here, [Herman's Own TestDisk How-to]("http://users.bigpond.net.au/hermanzone/TestDisk%20How-To.html") This is just a sort of illustrated record of some of my trials with TestDisk. I will only leave it on my website for a few days since it isn't really good enough, I am just learning TestDisk myself. I have used TestDisk to recover partitions successfullly. I hope that will help you a little. You should also of course read through the of official documentation on [TestDisk's home site]("http://www.cgsecurity.org/wiki/TestDisk") a fwe times and compare that to my illustrations. I also recommend practicing with some unimportant partitions on an old hard disk first if you can. TestDisk is quite simple and easy to use though, and works very well when you know what to do.

I'll be back in twelve or so hours, you may want to ask me some questions. That webpage is not complete, it was only for me and I can remember most of what I need to know, so lost of comments ands explanations I would include for new users is left off it. Good luck, and don't hurry, take your time, or even wait if you're not sure. Your data will still be there for years if you don't touch it.
Regards, Herman :D

---

### Post by schalicto on 2007-05-21
> **Herman said:**
> Here, [Herman's Own TestDisk How-to]("http://users.bigpond.net.au/hermanzone/TestDisk%20How-To.html") This is just a sort of illustrated record of some of my trials with TestDisk. I will only leave it on my website for a few days since it isn't really good enough, I am just learning TestDisk myself. I have used TestDisk to recover partitions successfullly. I hope that will help you a little. You should also of course read through the of official documentation on [TestDisk's home site]("http://www.cgsecurity.org/wiki/TestDisk") a fwe times and compare that to my illustrations. I also recommend practicing with some unimportant partitions on an old hard disk first if you can. TestDisk is quite simple and easy to use though, and works very well when you know what to do.

I'll be back in twelve or so hours, you may want to ask me some questions. That webpage is not complete, it was only for me and I can remember most of what I need to know, so lost of comments ands explanations I would include for new users is left off it. Good luck, and don't hurry, take your time, or even wait if you're not sure. Your data will still be there for years if you don't touch it.
Regards, Herman :D

That was great information!  Thank you sir!  Is there a rep system on this forum?  It doesn't matter, +REP :p

---

### Post by Herman on 2007-05-22
Thanks schalicto,
What operating system are you planning to use TestDisk from? Do you have Ubuntu installed to hard disk, or a Ubuntu Live CD? or some other LiveCD like GParted LiveCD or System Rescue CD?

Can you type 'sudo fdisk -ls' into a terminal and post the output from that here? (If you can).

If you have a hard disk installed Ubuntu operating system, you would need to install TestDisk first using apt-get or synaptic package manager.
Once you have TestDisk running you would start it by typing: sudo testdisk into a terminal.
```
sudo testdisk
```You then get that black screen  about whether you want to testdisk to create a log file for you or not. Are you with me so far? 
Regards, Herman :D

EDIT: Maybe you meant you have already done it and were successful. I have updated that page a little anyway, so if you still need it, it will be a little easier to follow. I'll check back here again in a few hours.

---

### Post by ramjet_1953 on 2007-05-22
I have found SpinRite Ver 6.0 quite good at data recovery.

It is a Windows executable, that you use to create an iso bootable disk.

The Windows executable works fine under Wine.

One catch, though, it's not free.

Here's a link: [http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

Regards,
Roger :cool:

---

### Post by Herman on 2007-05-22
Yes, ramjet_1953, thanks for the tip. I'll keep a note about that one too.
Parted is good for partitions that have just been deleted too.
```
sudo parted
```[Parted User's Manual]("http://www.gnu.org/software/parted/manual/parted.html")    |   [rescue]("http://www.gnu.org/software/parted/manual/parted.html#rescue")

Regards, Herman :D

---

### Post by schalicto on 2007-05-25
Herman.  Testdisk worked great.  I was impressed at how well it worked.  Instead of finding the files and moving them someplace else it just sorta recreated the NTFS file system with all the files right where they were!  Color me impressed.

:D

---

### Post by Herman on 2007-05-25
Hello schalicto,
I'm glad you got it done so easily,  I'm impressed that you were able to work it out by yourself and didn't need any more help than that! :D Well done and congratulations! 

TestDisk scans your hard drive for the start points for partitions and as long as those are in good condition it can write the partition table entry for that partition back to the MBR again.  All your data has always been there all the time, it was never really erased. Only the entry in the partition table for that partition was deleted, so your regular software didn't have the information it needed to tell it where to look for the data.
I have even recovered partitions including data after a new partition has been made and formatted with a new file system over the top of the old one, but only providing the start point for the new partition is in a different place in the hard disk. (So the first sectors of the old partition are not overwritten or damaged). TestDisk can be a great when it is needed. 

Regards, Herman :D

---

