---
title: "Password Protecting Windows 10 Partition in Ubuntu 14.04.3"
date: 2016-02-06
forum: General Help
---

### Post by grace3 on 2016-02-06
Hello,

I have a dual Boot system; and I would like to password protect the Windows 10 partition from the Ubuntu side.

Any help appreciated.

---

### Post by Petro Dawg on 2016-02-06
Not sure if that is possible. I believe it is possible to use software like BitLocker to encrypt the windows volume.  Not sure how well that plays with an Ubuntu partition if it is on the same HD though.  I have had setups with a separate drive for each where windows was encrypted and not accessible while running Ubuntu.

---

### Post by Vladlenin5000 on 2016-02-06
More often than not, in this forums, I'm the one with a self-imposed task to ask the hard questions and sometimes say the hard truths many people don't like. This is my way to provide better support for those in their first steps of the learning curve, instead of simply replying to questions such as "how can I jump into the abyss?". Faced with such questions I'll ask "why do you wanna do that?" and try my best to avoid a tragedy.

I fear this is one of those situations. This is the feeling I got from reading your other thread. So...

Why do you wanna password protect the Windows 10 partition?
Provided you don't click on it in your file manager (Nautilus or other) it won't be mounted, i.e., it won't be accessed in any way by Ubuntu. I'm sure you know what you're doing. If you're concerned about other people with whom you may share the computer then the first thing you should do is to set an account for each person, limited and totally separated from yours.

---

### Post by yancek on 2016-02-06
The following entry in your fstab file will allow only the user with root (sudo) privileges to access the partition.  Anyone else will get permission denied to access.  Use chmod to set the user:group to root:root and change the /dev to what yours is and also change your mount point.  You can also modify this so that a specific user will have access in addition to root.  An acquaintance had pre-teens and didn't want them to even have access to view each others files.  It worked, little bit of paranoia.  Of course this doesn't prevent anyone from accessing the windows files booted into windows and doing whatever.

> /dev/sda1 /mnt/windows ntfs-3g defaults,noauto,nouser,umask=777 0 0

---

### Post by Mark Phelps on 2016-02-07
Actually, that's not really needed.

Win10 comes with the new hibernation mode enabled -- known as FastStartup -- which is different from Fast Boot.

With FastStartup, whenever you shut down Win10, it's partitions remain mounted -- thus preventing you from mounting them again in any Linux distro.

Thus, if you leave it enabled, any attempt to access any Win10 filesystem partition is going to fail with an error message.

---

### Post by grace3 on 2016-02-08
I think yancek was the closest to what I'm trying to do.

I configure all of my laptops with dual-boot Windows 10 / Ubuntu. I have had problems accessing the Windows 10 partition, which I want to be able to do, with hibernation enabled, in fact it corrupts the NTFS files system, if I try to do this from the ubuntu side; so I disable this feature. I think a folder can be made to require a password. I would like to do this as a kind of firewall to tell remind myself to make sure that hibernation is turned off, so that I don't corrupt the NTFS partition when I try to access it. In all of my new builds, I will create a separate NTFS partition for passing files between the NTFS and EXT partitions; but if I get impatient I can still accidentally click on the NTFS partition, which would be disaterous.

---

### Post by yancek on 2016-02-08
I don't use the newer windows but my understanding is that with windows 8 and newer it uses hibernation by default and this being the case, a Linux system will not mount it and one would usually get a message such as the filesystem (ntfs) is in an unsafe state.  So you have a choice, either turn off hibernation and anything to do with fastboot, fast start or whatever the options are called or don't access from Linux/Ubuntu.   I don't know any other way around but I don't use the newer windows.  The problem is there because microsoft wants it's system to appear to boot faster and there is nothing Linux/Ubuntu developers are going to be able to do about it.

---

### Post by Vladlenin5000 on 2016-02-08
> **grace3 said:**
> I think yancek was the closest to what I'm trying to do.

I configure all of my laptops with dual-boot Windows 10 / Ubuntu. I have had problems accessing the Windows 10 partition, which I want to be able to do

You may think you do but actually you don't. There's absolutely NO reason to do that. Under no circumstance you should be messing with the Windows system partition from outside.
If you need to share data between both system then, for your own sake, make another partition (NTFS) and save or copy your personal files there.

---

### Post by yancek on 2016-02-08
> There's absolutely NO reason to do that. Under no circumstance you  should be messing with the Windows system partition from outside

I'd agree with that 100%.  My understanding was this was a separate data partition but after re-reading some of the posts, it looks like that's not the case.

---

