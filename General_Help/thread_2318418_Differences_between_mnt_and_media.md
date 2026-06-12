---
title: "Differences between /mnt and /media?"
date: 2016-03-25
forum: General Help
---

### Post by lakeshore2985 on 2016-03-25
So I was wondering are there any advantages to creating mount points (/mnt)? 

Is it safer to use /mnt rather than the default /media folder? For example, if I have a Linux computer specifically for running several P2P programs 24/7, is it better from a security standpoint to mount only certain folders related to those P2P applications? I don't understand why having two folders doing roughly the same thing: /mnt and /media.

---

### Post by Bucky Ball on 2016-03-25
If you plug in an external device it is generally automatically mounted in /media. Doesn't make any difference that I know of where you decide to create the mount point, but others may have very good reasons for doing one or the other.

I leave /media alone, personally. You could, theoretically, create a mount point in /home and mount there if you want. Doesn't make a lot of difference. 

For me, anything mounted in /mnt is done so manually. Anything mounted in /media happens automatically. Save me confusion. :)

(PS: Used to be things automagically mounted in /media when you plugged them in. Now, for some reason, in newer versions of *buntu it has been changed to /home/username/media. Don't know why.)

---

### Post by Morbius1 on 2016-03-26
Back in the olden tymes there were strict rules about where to mount things and if you were to mount permanent partitions under /media people would berate you, call you nasty names, and steal your lunch money at recess. These people tend to use the phrase "proper way" in their posts indicating that this is their way or their interpretation or sometimes misinterpretation of these rules. 

The reality is however that you can mount something pretty much anywhere you want.

The only peculiarity between /media and /mnt is the way certain desktop environments handle such mounts. If you mount something under /media a mount icon / launcher is placed on the side panel of your file manager and your desktop. If you mount it under /mnt it does not. This is because /media was traditionally used for temporary mounts of external media like USB sticks for example and the user was given a visual indication on the desktop that something was mounted so that he would remember to unmount it before removing the device from his computer.

---

### Post by lakeshore2985 on 2016-03-26
> **Morbius1 said:**
> Back in the olden tymes there were strict rules about where to mount things and if you were to mount permanent partitions under /media people would berate you, call you nasty names, and steal your lunch money at recess. These people tend to use the phrase "proper way" in their posts indicating that this is their way or their interpretation or sometimes misinterpretation of these rules.

I like your language style, dang! :)

Alright I got this (I guess?). I can create mount points pretty much anywhere I want. So the question now is, can I create a specific mount points within a USB stick? Or in other words, create a mount point in /media pointing to an USB device? That'd make life easier handling external devices.

Have lots of USB sticks and HDD's plugged in for P2P'ing, many of which would be nice to have the ability to mount/unmount via SSH (don't think I can do that pretty easily messing with /media folder instead).

---

### Post by Bucky Ball on 2016-03-26
Yes you can! From any where to anywhere. Say you have the mountpoint /mnt/external and an external drive with the partition sdc1, then:

> sudo mount /dev/sdc1 /mnt/external

Done. This applies to a USB also. But USB drives should mount when they are plugged in. They don't for you?

* BTW: to umount:

> sudo umount /mnt/external

---

### Post by lakeshore2985 on 2016-03-26
> **Bucky Ball said:**
> Yes you can! From any where to anywhere. Say you have the mountpoint /mnt/external and an external drive with the partition sdc1, then:



Done. This applies to a USB also. But USB drives should mount when they are plugged in. They don't for you?

* BTW: to umount:

Yeah they do mount automatically already.

Another question is how do I mount a certain folder instead of the whole partition? Is it even possible? For example what I did is "*sudo mkdir /mnt/VMs.VDI*" and then tried "*sudo /dev/sda1/My.VMs.Folder /mnt/VMs.VDI*" but it returns an error saying something like partition is not a block device? What I want to do is I want to create a mount point only for my VirtualBox VDI's so these .vdi files can be shared over the network.

---

### Post by Bucky Ball on 2016-03-26
No, you don't mount folders. ;)

You mount the partition they're on (/dev/sd**) *to* a folder (/mnt/your_partition).

---

### Post by lakeshore2985 on 2016-03-27
> **Bucky Ball said:**
> No, you don't mount folders. ;)

You mount the partition they're on (/dev/sd**) *to* a folder (/mnt/your_partition).

So basically what I have to do is create a partition only for my VMs right... ok I get it.

But still what I don't understand is the purpose of creating mount points in Linux. It seems everytime I reboot the machine it doesn't keep the configurations, only the folder name in /mnt which means it's temporary. Is there a way to make it permanent though? I wonder if it has anything to with fiddling with /etc/fstab? And if so, then what should the line look like? Perhaps something like this:

```
/dev/sda1 **/mnt/VMs**   ntfs  defaults       0  0
```

Seriously though... I have no idea lol.

---

### Post by Bucky Ball on 2016-03-27
That's exactly what it has to do with. 

To improve your chances of support, I think it would be best if you marked this as solved and started a new thread rather than posting about it here. 

[Do some research]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") on 'mount partition at boot ubuntu' first and you might not need to. ;)

---

### Post by lakeshore2985 on 2016-03-27
> **Bucky Ball said:**
> That's exactly what it has to do with. 

To improve your chances of support, I think it would be best if you marked this as solved and started a new thread rather than posting about it here. 

[Do some research]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") on 'mount partition at boot ubuntu' first and you might not need to. ;)

Oh, it worked Bucky.

I just did what I described in the post above (fstab config line) and the /mnt point is automatically mounted at boot.

Thanks again!

---

### Post by Bucky Ball on 2016-03-27
Good news. :)

Please mark this thread as solved. Thanks. This will not close the thread to further discussion.

---

### Post by lakeshore2985 on 2016-03-28
> **Bucky Ball said:**
> Good news. :)

Please mark this thread as solved. Thanks. This will not close the thread to further discussion.

Hmm, hasn't really answered the differences between /mnt and /media but may start another topic about this later again sometime.

---

