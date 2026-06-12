---
title: "Can't write to any disk except home directory"
date: 2020-11-19
forum: General Help
---

### Post by Chew N Tobacca on 2020-11-19
Hello all, it's been a while. I've recently built myself a new desktop with a dual-boot of Windows 10 and Kubuntu 20.04LTS. I updated from 12.04 (yeah, I know) to 20.04 and just noticed a problem. Rather big one, for what I do. 

Here's the disk setup, to put it out here: 

I am using UEFI under GPT. The main disk is a NVME SSD with a windows partition and Kubuntu partition (and all the other necessary partitions); the secondary drive I use for storage etc. is a 1TB SATA SSD with a single partition formatted as NTFS. All of the boot, windows, and storage partitions were created using the windows install media, and Kubuntu was installed after all that was in check. Now the problem is, I can't write ANYTHING to my storage disk from Kubuntu. Nor can I write to my windows OS drive or anywhere on my Kubuntu root. Removable media behaves normally, as far as I can tell. The only place I can write any data to is my home folder. This has never been an issue until now. It all works fine if I boot to Windows.

It gives me an error, but not any more specific than "could not write to [file path]" or "could not make folder [folder path]". Again, this happens any time I try to write data outside of my home folder (even though it may be on the same partition). In the terminal, I simply get a message that says "cannot create directory [folder path] : Read-only file system". 

Would someone be kind enough to explain why this is happening, and how I can fix it? I have searched the web, and can't really find any information that helps me. 

Thanks in advance,
-Chew

---

### Post by CelticWarrior on 2020-11-20
What you describe is a consequence of the Windows Fast Startup "feature". Disable it and you should be fine.
Now, I would be doing a disservice to you and future readers if I didn't **strongly advised NOT to write to Windows system partition from outside Windows**. Always use a separated NTFS data, non-system, partition to share files between OSes, never the "C:\ drive".

---

### Post by Impavidus on 2020-11-20
There can be, typically, three reasons why people are unable to write to certain parts of their filesystem.

1: It's mounted read-only. It Windows uses Fast Startup, Ubuntu can only mount the NTFS partitions as read-only. So if you want to share data between Windows and Ubuntu, make sure you've Fast Startup disabled. And don't mount your Windows C partition (except, maybe, read-only), as it's really easy to damage Windows that way. Ubuntu allows you to write to the Windows system files without any of the built-in protection that Windows offers. When Ubuntu encounters an error accessing a particular filesystem, it may be remounted in read-only mode. Your home directory may not be on the same partition as your system, but you should know that if it were the case. The error "Read-only file system" indicates this is the problem, but should apply to entire partitions.

2: You don't have permission. In most of the filesystem on Ubuntu outside your home directory you don't have permission to write anything, except when you use sudo (and are allowed to use it). But that would give the error "Permission denied".

3: You run programs packaged as snaps. These are constrained in the directories they can access, usually your home directory and maybe /media. Most terminals and shells shouldn't be snaps, as that would make it impossible to use them for that what they're most used for (i.e. system admin tasks).

How exactly have you partitioned your hard drives? Have you disabled Fast Startup in Windows (not to be confused with Fastboot, or what was it called again, which is an UEFI feature)? Can you show us your /etc/fstab in Kubuntu?

---

### Post by Chew N Tobacca on 2020-11-20
Thank you both for the prompt replies. I honestly would have never guessed a windows setting would be responsible. I guess a lot has changed in the 8 years since I built my last machine. I am not currently at home, but when I am I will start by turning off the fast startup feature (I assume it is turned on by default) before I get too technical. I'll post back after that. 

Thanks again,
-Chew

P.S. I need to update my system specs; that's my old machine.

---

### Post by CelticWarrior on 2020-11-20
The feature was introduced with Windows 8.

---

### Post by yancek on 2020-11-20
>  I will start by turning off the fast startup feature (I assume it is turned on by default) 

Yes it is and, just so you are aware, some future windows updates wlll turn it back on.  Of course, you will not be asked or informed that this will happen so if you run into this same problem in the future, that will be the likely reason.

---

### Post by Chew N Tobacca on 2020-11-21
It looks like that's all it took. I disabled fast startup and all seems well. I can now write to my storage drive as normal. Thank you all for the excellent info. 

-Chew

---

