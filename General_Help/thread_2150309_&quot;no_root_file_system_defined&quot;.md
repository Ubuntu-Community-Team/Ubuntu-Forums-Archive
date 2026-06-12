---
title: "&quot;no root file system defined&quot;"
date: 2013-05-31
forum: General Help
---

### Post by mani008 on 2013-05-31
when ever i try to install ubuntu....at the time of installation a dialog box prompts up saying that "no root file system defined".
can u plzzz tell me yy this is happening....and how to cure it ??

---

### Post by AgentZ86 on 2013-05-31
Several questions

what version of ubuntu are you installing and are you installing on a hard drive on a PC computer ?
I'm assuming your running the live CD and booting to the Ubuntu Live CD/DVD right  ?
Or are you booting to windows then running the CD/DVD from windows ?

If booting directly to the CD/DVD and you select install Ubuntu when it loads up, then this could indicate that your hard disk is failed or unallocated space perhaps

Run the partition tool and look at your hard drive and see what it says.

Please advise

---

### Post by FabioBeneditto on 2013-05-31
Hi!

In my Dell Vostro 260S at home I've same problem.

Workaround: generate bootable pendrive from *buntu CD.

At work, as supported by BIOS, I've change UEFI boot to use DVD, and works fine.

Give a try :)

---

### Post by mani008 on 2013-05-31
sir. i trying to install ubuntu 11.10....in my lappy m installing it inside window n the problm pops up when its start it earlier verification .....jus before completion of the verification.

---

### Post by FabioBeneditto on 2013-05-31
11.10 is too old, and does not have support.

Unless you have an very old machine, I recommend use 64-bit version as indicated in [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Actually, wubi don't have support, and no more available.

---

### Post by AgentZ86 on 2013-05-31
Ahh ok 11.10

Why not 12.04, 12.10 or even 13.04 ? 
I'm not as familiar with installing Ubuntu from within Windows


Normally it's best to boot to linux CD/DVD or flash drive first then click install. It will let you install along side windows and set the partition size
If you have a windows restore partition this could be causeing some trouble too because you won't have enough primary partitions and you don't want to delete your restore partition which may have your windows OS on there for reinstall later.

Anyhow it sounds like there is no room to install it and I'm not sure how it installs when your already booted to Windows
I'm more familiar with booting to the CD/DVD and installing from there along side of or next to windows. Then you can boot to whatever OS you want to once it's installed

---

### Post by Isamu715 on 2013-05-31
Ubuntu 11.10 is not supported anymore, I recommend you try installing 12.04 LTS. I'd also consider installing it on the hard drive as a dual-boot or replace Windows, it's much better than wubi(installing in Windows, that's what I believe you're currently trying to do). Also check the partitioning tool in the Ubuntu installer and make sure you have a root(/) partition selected.

---

### Post by Mark Phelps on 2013-05-31
Do NOT rush into this.  You make a mistake and you'll end up corrupting Windows and NOT having a working Ubuntu as well.

Need to know what version of Windows you are running -- as it makes a major difference in SUCCESSFULLY installing Ubuntu in dual-boot mode.

Do NOT just stick in a CD or DVD and choose the option to install side-by-side by shrinking MS Windows with the Slider -- this can easily result in corrupted Windows loader.

Also, need to know the make and model laptop, and some specs: Processor, memory, disk size.

---

### Post by AgentZ86 on 2013-05-31
> **Mark Phelps said:**
> Do NOT rush into this.  You make a mistake and you'll end up corrupting Windows and NOT having a working Ubuntu as well.

Need to know what version of Windows you are running -- as it makes a major difference in SUCCESSFULLY installing Ubuntu in dual-boot mode.

Do NOT just stick in a CD or DVD and choose the option to install side-by-side by shrinking MS Windows with the Slider -- this can easily result in corrupted Windows loader.

Also, need to know the make and model laptop, and some specs: Processor, memory, disk size.


I never had a corrupt windows loader from installing side by side and adjusting the partition sizes with the live CD. Never a problem in the past 7+ years and I have done it on a lot of computers this way.
Not to say it can't happen but I mean a lot of computers 100's in fact

---

### Post by rnerwein on 2013-05-31
> **mani008 said:**
> when ever i try to install ubuntu....at the time of installation a dialog box prompts up saying that "no root file system defined".
can u plzzz tell me yy this is happening....and how to cure it ??
hi
i gues your problem is - after you finished your disklayout - this error comes up. the solution is: ---> "/" must be defined as your basic filesystem. it's not c: .... d: .... bla bla. --> c: is the root for windows but in unix/linux is it just "/root". give it a shot.
ciao

---

### Post by lisati on 2013-05-31
> **AgentZ86 said:**
> I never had a corrupt windows loader from installing side by side and adjusting the partition sizes with the live CD. Never a problem in the past 7+ years and I have done it on a lot of computers this way.
Not to say it can't happen but I mean a lot of computers 100's in fact

Mileage **can** vary, depending on a bunch of stuff such as Windows version, Ubuntu version, hardware specs, etc....

I concur with the advice not to rush into things. Make sure you have backups of things like recovery media, important files etc.

---

### Post by 3rdalbum on 2013-05-31
On the partitioning screen, select the partition you want to install Ubuntu to, and click Edit Partition.

Set the mount point to /

This is the "root file system" and you can now continue.

Use Ubuntu 12.04 or later, though. And make sure you have your data backed up. Installing Ubuntu will of course format that partition.

---

### Post by bcbc on 2013-06-01
When you get no root filesystem defined with a Wubi install, then you will also get it for a normal install. It's due to some partition table issues. [URL="http://askubuntu.com/a/103495/14916"]
http://askubuntu.com/questions/103345/wubi-no-root-system-file-defined[/URL]

You can also get this problem on a normal installation due to a user error (using manual partitioning, but forgetting to set the / (root) partition), but this is definitely not the case when using Wubi. Also it has nothing to do with running an out of support release (11.10).

---

