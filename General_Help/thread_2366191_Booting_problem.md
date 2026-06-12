---
title: "Booting problem"
date: 2017-07-14
forum: General Help
---

### Post by RobGoss on 2017-07-14
Hello everyone I was wondering if anyone knew why this message would be appearing at startup, I'm getting the following message when I try to boot my system

**Message I'm receiving**

Busybox v1.22.1 (ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Booting problem

I'm not sure what this means but I cannot boot into my desktop
I'm running Ubuntu 16.04.2

Thanks so much for any help with this matter

---

### Post by #&amp;thj^% on 2017-07-14
Boot from a live USB stick and run:
```
sudo fsck -a /dev/sda1

```

Imprortant! --> replace /dev/sda1 with your Ubuntu partition
You can find that with:
```
lsblk
```

---

### Post by DuckHook on 2017-07-14
Busybox is the severely limited shell that is built into GRUB and is booted when GRUB cannot finish the booting process for any reason. Often, this is caused by some sort of disk corruption or system misconfiguration (sometimes from updates) that prevent GRUB from locating your *initramfs* (Initial RAM File System). While your GRUB message would seem to confirm this, the problem is that GRUB itself is so limited, and the system is at such a primitive state, that system messages like the one you received are very unreliable, often misleading, and therefore not very useful for diagnostics.

Do you remember what you were doing prior to the problem arising? Did you apply any updates or upgrades? If so, was GRUB one of the system components upgraded? Did you shut your computer down inelegantly (hard shutdown, power outtage, etc)?

You can try running boot repair which often fixes the problem. Not to be unduly pessimistic&#8212;but it's best that you prepare yourself&#8212;I've found that if boot repair doesn't work, I often have no other practical recourse than to reinstall the system. This is because the time spent hunting down the problem when the system is in such a primitive state is not worth my trouble and will take longer than a reinstall. Admittedly, the reinstall process is relatively painless in my case because I back up habitually, have my data on a separate partition, and don't run a very complex system. If you have lots of customization in your box or it's not so easy to restore from backups, then it may make more sense to invest effort in a repair attempt.

**EDIT**
ninja'd by 1fallen

---

### Post by RobGoss on 2017-07-14
> **1fallen said:**
> Boot from a live USB stick and run:
```
sudo fsck -a /dev/sda1

```

Imprortant! --> replace /dev/sda1 with your Ubuntu partition
You can find that with:
```
lsblk
```

I ran that command and I get the following below

It's telling me I much have **r/w access to the filesystem or be root**

---

### Post by RobGoss on 2017-07-15
Thank you both for the help with this issue but after trying 1fallen solution and ubable to resolve I decided to just go with the fresh install I don't have much data on my systems so doing a reinstall is no biggie. 

Thanks again

---

### Post by #&amp;thj^% on 2017-07-15
> **RobGoss said:**
> I ran that command and I get the following below

It's telling me I much have **r/w access to the filesystem or be root**

Sorry to hear that you had to reinstall>>>I have found mostly the error you have seen there** "r/w access to the filesystem"** come's from using SUDO with GUI's specifically opening a file manager with "sudo".
And the information that DuckHook has written is very well worded and very detailed as possibility's as to why you landed in a Busy Box.
Any Who take good care and Best Regards.;)

---

### Post by RobGoss on 2017-07-15
> **1fallen said:**
> Sorry to hear that you had to reinstall>>>I have found mostly the error you have seen there** "r/w access to the filesystem"** come's from using SUDO with GUI's specifically opening a file manager with "sudo".
And the information that DuckHook has written is very well worded and very detailed as possibility's as to why you landed in a Busy Box.
Any Who take good care and Best Regards.;)

Thank you 1fallen, yes after trying to get my system back up and running I was unsuccessful, my system is very minimal and does not use a lot of data, let's just say I picture folders had around 20 photos :)

---

