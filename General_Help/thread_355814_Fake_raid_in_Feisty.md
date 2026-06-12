---
title: "Fake raid in Feisty"
date: 2007-02-07
forum: General Help
---

### Post by larini on 2007-02-07
Will Feisty support fake raid (software raid) in the boot?

---

### Post by larini on 2007-02-10
Anybody knows?

---

### Post by tomm3h on 2007-02-16
It'll be nice if it does! It took me a lot of head-scratching and switching between the two main fakeraid/dmraid tutorials I could find on help.ubuntu.com, to actually get Edgy installed on the array.

But I managed it in the end. Talk about newb in the deep end, heh. 

I think this is planned, and I think there's some support built into the HERD 3 release but it definitely didn't work for me. The installer went nuts and ended up going around in a loop of errors. :(

I'm currently trying to uncover the threads that I learnt from, so that I can contribute my findings. I did have to do a bit of improvising.

---

### Post by tomm3h on 2007-04-27
I can confirm that my upgrade from Edgy to Feisty, via the update-manager, went very well. There wasn't a single problem with dmraid, and I've noticed after running update-grub, that the /boot/grub/menu.lst file has a number of comments concerning dmraid within.

I've not tried to install Feisty from scratch on a dmraid volume, but I think at least grub's configuration should be a little easier now :)

---

### Post by theb3s7 on 2007-05-19
Is there any chance to integrate the dmraid packet on the livecd, so that my 2 SATA HDD work on a RAID0 Array made by BIOS on a ASUS A8N-SLI (nForce4 Chipset) (fakeraid) without needing to make all those steps in the tutorial ?
Thanks! I also tried with fedora but didn't worked.. as for gentoo.. I don't want that :)

---

### Post by igloocentral on 2007-05-24
I installed my promise fakeraid using the [FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto), but new users might have an easier time using [FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy). If you have problems, have a look at my [FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) page or post here.

---

### Post by tomm3h on 2007-06-09
> **theb3s7 said:**
> Is there any chance to integrate the dmraid packet on the livecd, so that my 2 SATA HDD work on a RAID0 Array made by BIOS on a ASUS A8N-SLI (nForce4 Chipset) (fakeraid) without needing to make all those steps in the tutorial ?
Thanks! I also tried with fedora but didn't worked.. as for gentoo.. I don't want that :)
Have a go with the Feisty Alternate Install CD -- you might be pleasantly surprised.

Make sure you have a print-out of both the FakeRaidHowTo and FakeRaidEdgy tutorials first though. :)

I'd also HEAVILY recommend reading this [thread]("http://ubuntuforums.org/showthread.php?t=316182"), to fill in the gaps :)

---

### Post by chris23 on 2007-06-12
I followed the FakeRaidGuide successfully  up to the point where you setup the device and root for the grub...

the command  ```
find /boot/grub/stage1
```  returns  Errror that it cannot be found...

But if I go to /boot/grub I can see over there the stage1...

What is wrong?
thanks

---

### Post by chris23 on 2007-06-13
Ok I've passed that stage too...now I'm  at the last command to setup the raid....

I'll remind that I'm referring to this [guide]("https://wiki.ubuntu.com/FakeRaidEdgy").

I've managed to install grub...and I changed the #groot to point to my root partition in the menu.lst that was created with ```
exec -a update-grub /usr/sbin/update-grub.real $*
```(update-grub didn't work for me...)

The guide says that I must run grub-update again to have the  changes correctly incorporated...

But the update-grub shows me  "unexpected operator"  and exec -a update-grub /usr/sbin/update-grub.real $* does npt wotk either..."-a not found something like this..."

---

### Post by fonsocm on 2007-06-16
> **chris23 said:**
> I followed the FakeRaidGuide successfully  up to the point where you setup the device and root for the grub...

the command  ```
find /boot/grub/stage1
```  returns  Errror that it cannot be found...

But if I go to /boot/grub I can see over there the stage1...

What is wrong?
thanks

I have the same problem, do you find a solution?

Thanks.

---

### Post by chris23 on 2007-06-16
Nope I didn't find the solution...
Hoping that someone else could help us...
;)

---

### Post by fonsocm on 2007-06-18
> **chris23 said:**
> Nope I didn't find the solution...
Hoping that someone else could help us...
;)

Finally, I installed Ubuntu Fesity in my fakeraid. My problem was I created the partitions using the tool to manage the disks in Vista and the grub has must a problem recognizing them.

I create the partitions using gparted like s1mmel tell in this topic: [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

Next, I followed the steps in FakeRaid Howto.

The grub is installed and I can boot Vista but when I tried to boot Ubuntu, it gives an error: I can't mount the partition or something similar, I think the problem is dmraid modules aren't in initrd. I have to review it.

---

### Post by CheShA on 2007-06-22
How to install ubuntu onto fake raid system:

[http://www.howtoforge.com/ubuntu_dapper_raid_system?]("http://www.howtoforge.com/ubuntu_dapper_raid_system?")

---

### Post by tomm3h on 2007-07-02
> **chris23 said:**
> I followed the FakeRaidGuide successfully  up to the point where you setup the device and root for the grub...

the command  ```
find /boot/grub/stage1
```  returns  Errror that it cannot be found...

But if I go to /boot/grub I can see over there the stage1...

What is wrong?
thanks
Sounds like you were in a directory other than / ? (The answer's the benefit of those who may have the same issue in the future) :)

> **fonsocm said:**
> Finally, I installed Ubuntu Fesity in my fakeraid. My problem was I created the partitions using the tool to manage the disks in Vista and the grub has must a problem recognizing them.

I create the partitions using gparted like s1mmel tell in this topic: [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

Next, I followed the steps in FakeRaid Howto.

The grub is installed and I can boot Vista but when I tried to boot Ubuntu, it gives an error: I can't mount the partition or something similar, I think the problem is dmraid modules aren't in initrd. I have to review it.
Have you left 'savedefault' on in your menu.lst ?

---

### Post by chris23 on 2007-07-26
Ok I've passed  the 
```

find boot/grub/stage1

```

I managed to edit  the menu.lst and after I changed the groot(hd0,0) to groot(hd0,6) 

I tried to run update-grub after chroot /target as the guide says , but it returned an error 
saying 

```

[: 25: ==: unexcepted operation
exe:25 -a:not found

```

....

then  I searched for the word **savedefault**
but I didn't find it  anywhere in the menu.lst...
Now  when the grub loads it says that it can't mount the partition...

any help?

---

### Post by jlintz on 2007-07-29
has anyone had problems with fakeraid booting back and forth between the 2 disks in a mirror?  It's a very strange problem, everytime I reboot its a coin flip.  Windows is working fine but its like I have 2 linux installs and everytime i reboot i dont know which one its going to boot to.  I followed the fakeraid howto but also added LVM into the mix.  dmraid -r shows my raid devices and also says its active.

---

