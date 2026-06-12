---
title: "Triple boot Xubuntu 12.04 on new HD. Grub install questions."
date: 2013-01-21
forum: General Help
---

### Post by mikodo on 2013-01-21
New drive to go into machine. Just one. I want to triple boot again only all Xubuntu 12.04 as primary, Xubuntu 12.04 as experimental, and Xubuntu as next.

I want to have grub installed to all. But, grub installed to the drive for primary Xubuntu.

So I plan to use "The Something Else" while installing all of them after having made up the partitioning with a live CD with Gparted.

Question:

To install the grubs, the last one installed will have grub installed naturally. If I go to the primary and run                       below, will this attach it to the primary.             ```
sudo grub-install /dev/sda
```Then in the other two Xubuntu's in each use:
```
sudo grub-install /dev/sda(6)&(9) respectively.
```Then the grub from the primary should always be the one updated, and will pickup the others, correct?


Thanks.


Now to figure out how to make a media partition and link to each.

---

### Post by Elfy on 2013-01-22
I'd do 5 partitions (drive numbers just for example)

Xubuntu - sda1
Xubuntu -dev - sda2
Xubuntu -other one - sda3
Data partition 
Swap

I would let installer choose where to put grub for the primary Xubuntu.

When I installed the dev and other one's I would use the Something Else option - choose the drives as normal (eg sda2 and 3) - ALSO tell the installer to install grub to that partition. 

Then update grub in the primary and it will pick up the other two.

The data partition can then be added to fstab in all 3 so it mounts for them.

For example, I have 3 drives I mount in /mnt

Data  music  Spare

The corresponding fstab entries are 

UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2
UUID=72cf9e50-f555-476e-a018-cec87a86d2bb /mnt/Data ext4 defaults 0 2
UUID=aa678306-da8e-4a7d-a2a2-e1de2d3cdedc /mnt/Spare ext4 defaults 0 2

---

### Post by mikodo on 2013-01-22
> **Elfy said:**
> I'd do 5 partitions (drive numbers just for example)

Xubuntu - sda1
Xubuntu -dev - sda2
Xubuntu -other one - sda3
Data partition 
Swap

I would let installer choose where to put grub for the primary Xubuntu.

When I installed the dev and other one's I would use the Something Else option - choose the drives as normal (eg sda2 and 3) - ALSO tell the installer to install grub to that partition. 

Then update grub in the primary and it will pick up the other two.

The data partition can then be added to fstab in all 3 so it mounts for them.

For example, I have 3 drives I mount in /mnt

Data  music  Spare

The corresponding fstab entries are 

UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2
UUID=72cf9e50-f555-476e-a018-cec87a86d2bb /mnt/Data ext4 defaults 0 2
UUID=aa678306-da8e-4a7d-a2a2-e1de2d3cdedc /mnt/Spare ext4 defaults 0 2
Thanks buddy. I was actually reading another post of yours that got me thinking about asking this question. I am sure you guessed that though. I was hoping you would respond. 

I got it. 

I am also going to be following [Carla Shroder's Painless Linux Multi-boot guide too!]("http://www.linuxtoday.com/blog/2009/08/painless-linux.html")

Thank you!

;p

---

### Post by Bucky Ball on 2013-01-22
As we were just discussing on my thread, mikodo, install grub to sda for the first install and install the rest to the same partition as that particular install, effectively not installing it, using 'Something Else'. This means 'sudo update-grub' needs to be done in the first install to reflect anything when, say, one of the installs gets a kernel update. 

The update won't be reflected in your menu list unless you boot into the first install and sudo update-grub there. ;)

(PS: You can inadvertantly not be running the newest kernel when you forget to update from the first install after kernel upgrades in the other!)

---

### Post by mikodo on 2013-01-22
Thanks for the confirmation, Bucky Ball. I will be checking this and the other threads before installing all those new partitions on my new drive. Now, in Canada where I live it is getting close to 03:00 and I have to leave.

See you.

;p

---

### Post by Bucky Ball on 2013-01-22
Yup. Go to it! I will be doing the same shortly. ;)

---

