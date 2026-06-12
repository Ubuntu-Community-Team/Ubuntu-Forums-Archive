---
title: "Allocating 50 GB to Kubuntu"
date: 2014-11-08
forum: General Help
---

### Post by sports fan Matt on 2014-11-08
I'd like to allocate 50 GB to Kubuntu along side my W7/Ubuntu 14.04 to see if I want to keep Kubuntu or stick with gnome. If I were to allow 50 GB, with shrinking down my NTFS Partition, how would I not harm my Windows 7 partition?

---

### Post by Impavidus on 2014-11-08
Use Windows tools to defragment the big NTFS partition and then shrink it from the right. Reboot into Windows a couple of times. Use your Ubuntu or Kubuntu live disk to expand the extended partition into the unallocated space and then create a new logical ext4 partition for Kubuntu. In the installer, use "something else" and point it to the partitions you just created. You can reuse the existing swap partition.

Instead of expanding the extended partition, you can also make a new primary partition. This can even been done from your existing Ubuntu system, but as you will use your last available primary partition, this is less flexible in case of any future modifications.

---

### Post by sports fan Matt on 2014-11-08
Could I shrink the sda 2 (Windows) by 50,000, leaving it 499 GB) then allocate the space for a new EXT4 partition for Kubuntu or does it have to come from Windows 7?

---

### Post by sports fan Matt on 2014-11-08
less flexible meaning it could break...or?

---

### Post by Impavidus on 2014-11-08
> **sports fan Matt said:**
> Could I shrink the sda 2 (Windows) by 50,000, leaving it 499 GB) then allocate the space for a new EXT4 partition for Kubuntu or does it have to come from Windows 7?Your sda2 is your Win7 partition. sda1 is a small (but vital) boot partition for Windows. You have to shrink sda2 using Windows tools.

> **sports fan Matt said:**
> less flexible meaning it could break...or?Meaning, if you later try to change more things, you can shrink that big Windows partition even more. Then you would have
* Windows boot partition (primary)
* Windows C partition (primary)
* Unallocated space
* Kubuntu root partition (primary)
* Extended partition
** Ubuntu root partition (logical)
** Swap partition (logical)

This would make it very difficult to do anything with that unallocated space. Therefore the suggestion to make the Kubuntu root partition logical. If you want to change anything later, you can simply expand the extended partition further to the left.

---

### Post by sports fan Matt on 2014-11-08
Can I now install using sda4 Kubuntu? I already have the iso image but no blank disks.

---

### Post by sports fan Matt on 2014-11-08
One other thought...Wouldn't it be easier on my sake to just install kubuntu-desktop and choose between them at startup ?

---

### Post by JayKay3OOO on 2014-11-08
You're right 

Don't bother wasting time installing kubuntu on a partition. That's just a load of un-needed time-wasting steps.

Open the terminal

For KDE desktop - sudo apt-get install kubuntu-desktop

For Gnome - sudo apt-get install ubuntu-gnome-desktop

This will install the default kubuntu desktop package with the usual set of KDE apps. You'll then be able to choose between unity and kde at startup (as you know)

If you then want to go full clean KDE in the future then install kubuntu, but you want to work through the quirks first. Either that or run kubuntu in a virtual machine. A dynamic 30GB wih 1gb allocated memory would be fine in this case.

KDE does have an annoying quirk though. It's a security thing apparently, but you can't play video files from a network drive although audio is fine. 

Have Fun.[COLOR=#555555][FONT=Arial]
[/FONT][/COLOR]

---

### Post by westie457 on 2014-11-08
Yes you could install the kubuntu desktop and choose at start up however removing either k/ubuntu desktops cleanly is an absolute nightmare and usually means a clean re-install.

If you want to try this. [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

Boot from the iso on the hard drive and install to a partition.
There is also the option to run as a virtual machine - as already suggested.

---

