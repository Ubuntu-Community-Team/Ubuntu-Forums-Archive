---
title: "mdadm error message when sudo apt-get upgrade, remote system won't boot"
date: 2019-12-07
forum: General Help
---

### Post by bomberb17 on 2019-12-07
Hello, I have a remote ODROID box running Ubuntu 18.04 and controlling it through SSH remotely.
I just executed a apt-get upgrade and after it finished, I got the following warnings:


```

...
update-initramfs: deferring update (trigger activated)

...
update-initramfs: Generating /boot/initrd.img-3.8.13.30
W: mkconf: MD subsystem is not loaded, thus I cannot scan for arrays.
W: mdadm: failed to auto-generate temporary mdadm.conf file.
```

I was not sure why I got these (probably because I had mounted an external hard disk which was not accessible) , but since they were warnings I decided to reboot anyway.
Now my system is unreachable. I am not on site but I can instruct someone to put the sd card (which contains the system) into a computer so I can directly modify any files needed to make it bootable again.
Can you please give me some insight on what to do?
Thanks

---

### Post by TheFu on 2019-12-07
I'm guessing the OS on the flash drive got corrupted.
If you didn't setup RAID, then mdadm isn't needed.  

Probably nothing, but that kernel is really old.  My r-pi has v4.14.78. 

For remote systems, I'm pretty cautious about rebooting when there isn't a DRAC or IPMI access, but I could easily have been in a similar situation.

---

