---
title: "Customize ubuntu"
date: 2016-06-16
forum: General Help
---

### Post by steviesomm on 2016-06-16
Hi I tries to customize my Ubuntu version , I used debootstrap from this wiki - [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
I faced some issues which I found hard to resolve
1. How can I edit a new user to this version? I went  -> cd /home but the regular Directories of Download, Pictures etc weren't there , How to create it? can it be imported from my "host" Home? 
2. How can I "work" and customize the Home directory of my customized chroot
3. How to create an ISO from it?
Thank's ahead

---

### Post by ventrical on 2016-06-18
That wiki is almost a year old and has not been updated since Sept. 2015.

What version of Ubuntu are you using? Are you using yakkety or xenial? If xenial then this is not the thread to ask this question.

Thanks

Regards..

---

### Post by QDR06VV9 on 2016-06-18
> **steviesomm said:**
> Hi I tries to customize my Ubuntu version , I used debootstrap from this wiki - [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
I faced some issues which I found hard to resolve
1. How can I edit a new user to this version? I went  -> cd /home but the regular Directories of Download, Pictures etc weren't there , How to create it? can it be imported from my "host" Home? 
2. How can I "work" and customize the Home directory of my customized chroot
3. How to create an ISO from it?
Thank's ahead

> **ventrical said:**
> That wiki is almost a year old and has not been updated since Sept. 2015.

Regards..
That is a Good Point and might be a bit out dated.
> **ventrical said:**
> What version of Ubuntu are you using? Are you using yakkety or xenial?  If xenial then this is not the thread to ask this question.

as ventrical states this is a Development Version section if you are using yakkety...If not Please Post in a more suited area of the forums.
Will leave here till OP responds.

---

### Post by ventrical on 2016-06-18
+1 ;)

I should of reported it in.

regards..

---

### Post by jimmy-frydkaer on 2016-06-18
+1 from me

---

### Post by deadflowr on 2016-06-18
What methodology of creating a new user did you try?

Sidenote:
I believe the /home directory is empty on the livecd until a script runs to create the user ubuntu.
A user solely created for a one time usage, and is designed to be discarded after shutdown/reboot.
So it makes sense that /home would be empty in the chroot environment.
Belief and reality, though, can be entirely different things.
So you can take it with a heavy rock of salt.

---

### Post by steviesomm on 2016-06-20
I did "useradd"  , it added the user but i didnt see any "home" directory
I'm using xenial , what is the way to create a "regular" home directory with the common Documents , Downloads Pictures , etc...

Where can I find the updated wiki for xenial 16.04?

---

### Post by coffeecat on 2016-06-20
> **steviesomm said:**
> I'm using xenial

Not an Ubuntu Development Version thread.

*Thread moved to **General Help**.*

---

### Post by deadflowr on 2016-06-20
useradd simply creates a new user, but that's about it.
To create a new user with useradd with all the trimmings you need to add a few extra flags, or at least an extra flag.
Luckily, Ubuntu, (and any debian based system) can use a different command, adduser.
Basically adduser does what useradd does but adds the extras.

Simple method to use is:
```
adduser new-user-name-here
```
adduser also a has the ability to quickly add a user to a group.
(This can be helpful when you need add your user to a single group like vboxusers, if you need to use virtualbox; as an example)
To add a user to a group with it simply:
```
adduser name-of-user name-of-group
```


You can compare and contrast by reading through each's man page
[I]man useradd
man adduser[/I]

To see which is more beneficial to whatever scenario you are attempting.

Hope it help
And good luck

---

