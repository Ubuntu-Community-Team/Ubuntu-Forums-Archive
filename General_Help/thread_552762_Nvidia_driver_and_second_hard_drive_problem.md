---
title: "Nvidia driver and second hard drive problem"
date: 2007-09-16
forum: General Help
---

### Post by maaylix on 2007-09-16
Ok, I've just installled Ubuntu 7.04 and I'm having trouble with two things:

The first one and, is that I'm trying to install nvidia's proprietary driver. 

I downloaded NVIDIA-Linux-x86-100.14.11-pkg1.run from nvidia's website and followed the only instruction that was to type:
 ```
sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```

I did that and this is what followed:

```
sh: Can't open NVIDIA-Linux-x86-100.14.11-pkg1.run
```

PS: I have 7300 GT

Now for my second problem:

 I'm currently only using Ubuntu in my pc. My system has two sata hard drives, I partitioned the first to be the main file system or the ''/'' mount.

On my second hard drive I created two partitions, a swap partition with 2gigs and the rest of the hard drive I partitioned as ext3 and specified the mount as ''/media/sec'' 

To have my second hard drive mount automatically during boot I typed the following:

```
sudo chgrp plugdev /media/sec
sudo chmod g+w /media/sec
sudo chmod +t /media/sec
```

My second hard drive is mounted during boot but I can't use it, there's a single folder called ''lost+found'' in it and I can't save anything in it or create anything in it.

---

### Post by maaylix on 2007-09-16
UPDATE: I recently rebooted my pc and my second hard drive didn't mount, now I'm a bit more lost!

---

### Post by confused57 on 2007-09-17
I think you need to chmod the downloaded Nvidia driver file, as explained by bodhi.zazen here:
[http://ubuntuforums.org/showpost.php?p=3000269&postcount=28](http://ubuntuforums.org/showpost.php?p=3000269&postcount=28)

For your mounting issues, this guide should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
or
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by maaylix on 2007-09-17
I'm getting a wierd error, after stoping X to install the driver, as indicated in the guide you mentioned. Terminal isn't recognizing the commands ''wget'' and ''sudo'', it gives me an error like: ''wget: command not found''

---

### Post by aldenhg on 2007-09-17
Instead of the /etc/init.d/gdm stop, try sudo init 1.Follow the other instructions and type sudo init 3 when you're done. This will bring the GUI back up and everything should be copecetic. If that doesn't work, you can always download the package ahead of time from the nvidia website and then run it once you've init'ed down to 1.

---

### Post by maaylix on 2007-09-17
> **aldenhg said:**
> Instead of the /etc/init.d/gdm stop, try sudo init 1.Follow the other instructions and type sudo init 3 when you're done. This will bring the GUI back up and everything should be copecetic. If that doesn't work, you can always download the package ahead of time from the nvidia website and then run it once you've init'ed down to 1.

My computer freezes after I input sudo init 1 (after I enter my password), I tried the method suggested by the guide again, terminal still gives me: ''sudo unknown command''

As for my hard drive, i'm getting the following error messege at boot up:

```
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=41f8acf0-cdc4-4822-957d-0d37d3ee6db9'

fsck died with exit status 8
```

Boot up stops at this point, and the terminal prompts me for a command, I type in ''reboot'' and then Ubuntu continues the boot procedure and finally boots up without my second
hard drive. 

My second hard drive is no longer detected by Ubuntu, I tried to see it using gparted, but that didn't detect it either. 
My second hard drive is being detected in BIOS with no problem, so I'm pretty sure it's an Ubuntu related problem, also my swap partition is on my second hard drive, and as Ubuntu is booting up, I'm guessing that that's working

Is it ok to have the swap partition on a diffrent drive than the ''/'' mount drive?

---

### Post by maaylix on 2007-09-25
Ok both problems fixed, my nvidia installation errors were happening due to typo errors and the lack of libc6-dev

My hard drive problem was an incompatibility issue with my motherboard Asus M2N-X and Ubuntu 7.04 kernel, the problem was solved by installing Ubuntu 7.10 kernel

---

### Post by ubnewbie2 on 2007-11-18
> **maaylix said:**
> Ok both problems fixed, my nvidia installation errors were happening due to typo errors and the lack of libc6-dev

My hard drive problem was an incompatibility issue with my motherboard Asus M2N-X and Ubuntu 7.04 kernel, the problem was solved by installing Ubuntu 7.10 kernel

I am considering purchasing a M2N-X motherboard for use in building a mythtv box, which will run mythbuntu 7.10, so the news that 7.10 fixed your problem, thanks

I was just wondering if you have had any other problems with ubuntu and this m/b, and have you ever tried using the spdif out from the sound system?

---

