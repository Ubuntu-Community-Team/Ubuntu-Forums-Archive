---
title: "slow booting. performing disk check every time?"
date: 2017-03-23
forum: General Help
---

### Post by jbdelta66 on 2017-03-23
hello,  

I have a question about the booting up of my Lubuntu install.
every time i reboot, it takes a very long time to start. 

 It seems to be performing a disk check; after showing the Lubuntu splash screen for nearly 15 minutes,
 it quickly flashes dev/sda1 clean, something something blocks.. Is this normal?
It is taking up to 15 minutes for my system to boot and it is doing this check every time.
Is there some way to turn this off so it'll speed up the boot?

 have a very old desktop with an 80gb hard drive, formatted ext4.

---

### Post by oldrocker99 on 2017-03-23
The drive itself may be failing (they do), and fsck is running every boot. That what it sounds like to me.

---

### Post by vasa1 on 2017-03-24
[Others also have noted a delay]("https://ubuntuforums.org/showthread.php?t=2356422") but fifteen minutes is bad :(

Please post the output of ```
df -h
```

---

### Post by Impavidus on 2017-03-24
Try digging into the log files (/var/log/), maybe you can find something that's going on during boot.

It's quite normal that it shows /dev/sda1 clean

---

### Post by jbdelta66 on 2017-03-25
> **vasa1 said:**
> [Others also have noted a delay]("https://ubuntuforums.org/showthread.php?t=2356422") but fifteen minutes is bad :(

Please post the output of ```
df -h
```

sorry, just checked my notifs.

i got:
```

beasley@puppypc:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            232M     0  232M   0% /dev
tmpfs            50M  3.1M   47M   7% /run
/dev/sda1        73G  3.5G   66G   6% /
tmpfs           246M   29M  217M  12% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           246M     0  246M   0% /sys/fs/cgroup
tmpfs            50M   12K   50M   1% /run/user/1000
beasley@puppypc:~$
```

---

### Post by jbdelta66 on 2017-03-25
i just did a reboot and i timed it. took exactly 11 minutes.

my system is quite old; a 1.8ghz Pentium 4 with 512mb. 80gb drive

---

### Post by Autodave on 2017-03-26
800 mhz with 1 gig RAM takes 1.5 minutes (running Xubuntu) to full boot-up.     Did this machine while running Lubuntu ever boot quicker than now? Did this just start or has it been like this since install?

---

### Post by RobGoss on 2017-03-26
> it quickly flashes dev/sda1 clean, something something blocks.. Is this normal?

Yes this is normal all Ubuntu systems display this at startup

> my system is quite old; a 1.8ghz Pentium 4 with 512mb. 80gb drive  

This could be why your system is slow at booting up having only **512- of RAM **is barely making it's the cutting edge 
You can try disabling unwanted programs at** startup** but make sure you know what's needed and what you can disable

---

### Post by jbdelta66 on 2017-03-31
its been like this since install.

after it boots.. finally. it runs fairly good under the LXDE. it lags on the internet, but I've gotten it to speed up a little with adblock ext.
as far as RAM, the max i can get is like 1 GB i think of Rambus DRAM. I've upgraded to 768mb which is all I've got.

---

### Post by RobGoss on 2017-03-31
There are a few things you can do to speed things up a bit one of them is to uncheck some of the application you have starting up when you boot your machine, try going to **startup application** and uncheck what you don't need to start when you boot up 

Another thing I use on most of my machine is **Preload** this application help some of the application you use and let them start up a bit faster
You can read about it here [https://launchpad.net/ubuntu/xenial/+package/preload](https://launchpad.net/ubuntu/xenial/+package/preload)

---

### Post by jbdelta66 on 2017-03-31
thanks, i'll try that.

i have another question about my drive. Do i need to make a new post?
its about making partitions.

---

### Post by RobGoss on 2017-03-31
> **jbdelta66 said:**
> thanks, i'll try that.

i have another question about my drive. Do i need to make a new post?
its about making partitions.

Yes it would be probably be best to start a new thread as your title will capture the right answers for partitioning

---

