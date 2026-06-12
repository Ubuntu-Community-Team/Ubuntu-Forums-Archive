---
title: "I really messed up, don't know if its fixable (please help)"
date: 2014-08-24
forum: General Help
---

### Post by vincentchivas16 on 2014-08-24
Ok so first things first, 
I had Ubuntu 14 and I wanted to dual boot windows, so I did all the partitioning and everything,where I messed up was I backed up everything to my HDD, I didn't move it to an external device. I didn't know windows would wipe my entire HDD until I installed it. Now I need to install Ubuntu again and I was wondering if I would be able to recover that backup or anything? Sorry if this is in the wrong section but I'm in such a hurry. Thanks for any input

---

### Post by Mark Phelps on 2014-08-24
sorry ... wrong text

---

### Post by Bashing-om on 2014-08-24
vincentchivas16; Well;

Not a "good" prospect. but a maybe:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Then there is testdisk:
```

sudo apt-get install testdisk

```
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112)


Do not write to the hard drive until such time as you have cloned it for data recovery operations.

Some small amount of luck ->
[INDENT][INDENT][INDENT]but mostly Time, hard work, and planning
[/INDENT][/INDENT][/INDENT]

---

### Post by vincentchivas16 on 2014-08-24
hey all,

so i think this is good
[IMG]http://i.imgur.com/YssGw7V.png[/IMG]
i booted in the live session and noticed my ubuntu partition has 128 gb being used, does that mean my data is safe? anyways i dont know if i should install ubuntu because wouldnt that delete it? and the bios isn't allowing me to boot into ubuntu  from the installed OS, only w7.
thanks!

---

### Post by kansasnoob on 2014-08-24
Stop and think before you do mess things up!

When you installed Windows it installed it's own bootloader which can't boot Ubuntu so you may only need to repair grub!

You can likely do that using Boot Repair from the live media you're using now:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not try reinstalling Ubuntu or you may get hit by this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by Bashing-om on 2014-08-24
vincentchivas16; Looks good !

Let's see if it is as good as it looks:
Boot that LiveDVD once more to "try ubuntu" mode -> terminal"
What do you see:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work
ls -la /mnt/work/home
ls -la /mnt/work/home/<your_user_name>
##so far so good ?

##Are you in a bootable state, let's look !
ls -la /mnt/work/boot/

```

You have lost the 'swap' partition, but that is recoverable .

[INDENT][INDENT]and so a tale is told
[/INDENT][/INDENT]

---

### Post by vincentchivas16 on 2014-08-24
> **kansasnoob said:**
> Stop and think before you do mess things up!

When you installed Windows it installed it's own bootloader which can't boot Ubuntu so you may only need to repair grub!

You can likely do that using Boot Repair from the live media you're using now:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not try reinstalling Ubuntu or you may get hit by this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

THANK YOU!!! it was that boot loader, i was so bummed, thanks!!

---

### Post by kansasnoob on 2014-08-24
As Bashing-om said, you need to see what's up with that SWAP partition also. Maybe start by seeing the output of:

```
free -m
```

---

### Post by oldfred on 2014-08-25
If you installed with an encrypted /home, swap is also encrypted and then gparted cannot see it.
So it may be normal not to see swap in gparted.

---

### Post by Bashing-om on 2014-08-25
> **oldfred said:**
> If you installed with an encrypted /home, swap is also encrypted and then gparted cannot see it.
So it may be normal not to see swap in gparted.

oldfred; marked that one down for future reference !

[INDENT][INDENT]somethings do matter
[/INDENT][/INDENT]

---

