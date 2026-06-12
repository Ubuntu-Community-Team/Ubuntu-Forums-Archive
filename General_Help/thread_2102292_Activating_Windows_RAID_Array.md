---
title: "Activating Windows RAID Array"
date: 2013-01-06
forum: General Help
---

### Post by rsjc852 on 2013-01-06
Since the Mint forums are being slow, I thought I'd post this here, since its not really OS-specific.


-----------------------------------------------------------------


I have a Raid Array, RAID 0 to be exact, that I made on Windows using the standard Disk Management Console.

How can I activate the array so I can access 99.9% of all of my stuff?

I would think MDADM would help, but after installing it, it's no where to be found!

Help?

---

### Post by sandyd on 2013-01-06
> **rsjc852 said:**
> Since the Mint forums are being slow, I thought I'd post this here, since its not really OS-specific.


-----------------------------------------------------------------


I have a Raid Array, RAID 0 to be exact, that I made on Windows using the standard Disk Management Console.

How can I activate the array so I can access 99.9% of all of my stuff?

I would think MDADM would help, but after installing it, it's no where to be found!

Help?

what version of windows? 7?
Are they Dynamic Disks?

Also, for windows-created RAID configurations, you use DMRAID

---

### Post by rsjc852 on 2013-01-06
I swear, im all over the place today.

Usually im really in-depth, but I think that's off-putting to some people.

Anyways, to answer your questions:

Yes, Windows 7 64-bit
Striped

It appears I have DMRAID installed. I pulled up "DMRAID --help", and it gives me some squable; 10 different ways that look promising.

But considering all my games/school work/music are on there, I don't want to end up messing my system up.


-----------------------------------------------------------------

If anyone can give me a nudge in the right direction, that'd be great.

My current setup:

sda - 128GB Maxtor M4 SSD
     sda1 - Linux Mint 14

sdb - 1tb unrecognized
(Also, it's giving me 169 bad sectors)

sbc - 1tb unrecognized

Thanks

---

### Post by ronparent on 2013-01-07
Your post provides little information but it appears that Mint is up and running. In a terminal type 'sudo dmraid -ay'. That command should activate your raid so that you can browse all the partitions with nautilus. It's response will also tel you whether or not it is installed. If not installed, install it (ie sudo apt-get install dmraid). 

I suspect that it is not installed otherwise you should have no problem seeing your raid drives - they a usually automatically activated on boot with dmraid installed.

---

### Post by rsjc852 on 2013-01-07
> **ronparent said:**
> Your post provides little information but it appears that Mint is up and running. In a terminal type 'sudo dmraid -ay'. That command should activate your raid so that you can browse all the partitions with nautilus. It's response will also tel you whether or not it is installed. If not installed, install it (ie sudo apt-get install dmraid). 

I suspect that it is not installed otherwise you should have no problem seeing your raid drives - they a usually automatically activated on boot with dmraid installed.

Mint is running, albeit not quite as stable as I'd like.

Typing "Sudo dmraid -ay" returns "no raid disks"


When I'm at my Computer directory (Which, by the way is Nemo on Mint, not Naut), it shows:

-1 TB Hard Disk
-1 TB Hard Disk
-128GB Disk
-File System

This confuses me. The 128GB Disk IS my File System.


Honestly, beyond giving you this information, I'm not sure what you actually need to solve the problem.

---

### Post by ronparent on 2013-01-07
> sda - 128GB Maxtor M4 SSD
sda1 - Linux Mint 14

sdb - 1tb unrecognized
(Also, it's giving me 169 bad sectors)

sbc - 1tb unrecognized

This says that Mint is installed on a separate 126GB drive. The two 1TB drives apparently are the raid. As long as the raid remains unactivated the drives could not be expected to be readable and even gparted would show them both with unallocated space. 

I don't think I can't deal with why the partition on the 1TB disk are unactivated by dmraid. I suspect that it may have something to do with Windows no longer differentiating between primary and extended partition and thus resulting in a structure that a linux distribution cannot deal with? If you can state how the raid drive is partitioned in Windows I might make a guess.

---

### Post by ronparent on 2013-01-07
OK Iv'e researched your situation further. You probably have a GPT file system which introduces certain limitations. We need someone who has direct knowledge of using GPT in the linux environment to jump in and address your problem. 

This thread - [http://ubuntuforums.org/showthread.php?t=2102285](http://ubuntuforums.org/showthread.php?t=2102285) - addresses GPT with raid to some degree. Your situation is different in that your grub2 MBR is not on the raid! But some issue with the GPT file system seems to be preventing dmraid from properly mounting your raid partitions. I frankly don't know the specifics well enough to be of much help.

---

