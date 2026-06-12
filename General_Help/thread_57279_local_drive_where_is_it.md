---
title: "local drive? where is it"
date: 2005-08-15
forum: General Help
---

### Post by cts on 2005-08-15
Ubuntu live CD boots OK but I cant see my local drive
[C:  hda1 or whatever you like to call it]

nothing in mnt

I try to run mount
the first few times it just rolls the syntax help
then it says 
"only root can do that"
so I go su
and what is the password??????????????????
Its extremely irritating when  a bootable cd asks for a password...

To sum up:  a bootable CD of Linux is *completely useless* if it cant access the local harddrive.

---

### Post by amohanty on 2005-08-15
> Ubuntu live CD boots OK but I cant see my local drive
[C: hda1 or whatever you like to call it]

nothing in mnt

I try to run mount
the first few times it just rolls the syntax help
then it says
"only root can do that"
so I go su
and what is the password??????????????????
Its extremely irritating when a bootable cd asks for a password...

To sum up: a bootable CD of Linux is *completely useless* if it cant access the local harddrive. 

I am sorry you are having so much trouble, but the forums have a very nice search feature, which you should use before giving up.

First off, if your disks have not been partitioned and formatted I doubt any Live CD will let you access it (I could be wrong on this, but AFAIK mount needs to know what format the drive is in before it can mount the drive.)

Secondly Ubuntu does not allow root login by default which IMO _is a very good thing_ - especially because it stops newbies from screwing things up beyond repair. What Ubuntu does is to allow sudo access to the default user. To run anything which requires root permission just prepend sudo before it in the terminal like so:
>> sudo mount .....
It will prompt you for _your_ password and when you provide it it will do as you want. There are several arguments for and against this approach and if you would like to know more just google it.

Please remember Linux/Ubuntu is _not_ windows. IMO its far better. Before you use something please put in a few minutes to read a bit about it, and also visit beginner's forums.

HTH
AM

---

