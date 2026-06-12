---
title: "Stuck at DELL logo after installing Ubuntu"
date: 2015-08-23
forum: General Help
---

### Post by Rodolfo_Carlos on 2015-08-23
Hi,

I've been having a problem with my Ubuntu installation for some weeks now. Ubuntu properly installs and after installation is complete it boots correctly for the first time but when I perform a reboot my PC hangs at the DELL logo forever and no matter what I do on further boots I cannot get past the DELL logo and my only option has been removing the HDD and formatting on another PC.

It's worth mentioning that Ubuntu is the only OS that I've been having this problem with. I've made a full Arch Linux installation and even installed Windows to make some tests and they booted correctly each time.

I'll leave my PC specs down below as well as an image depicting the problem:

[LIST]
[*]Dell XPS 8700
[*]16GB RAM
[*]1TB HDD
[*]NVIDIA GeForce GTX 660
[*]Intel Core i7 (4th Gen)
[/LIST]

Image depicting the problem:
[IMG]http://i.imgur.com/klX5L45.jpg?1[/IMG]


Any help is much appreciated.

---

### Post by coldraven on 2015-08-24
If you remove the HDD does it get past the Dell logo? Have you tried booting from CD or USB stick?

---

### Post by Rodolfo_Carlos on 2015-08-24
Yes if I remove the HDD it gets past the Dell logo and can boot from USB. I have tried formatting the HDD and creating a new partition table, and after installing Ubuntu I get the same results. I tried today with Fedora and openSUSE and got the same results: first boot into the system goes without problem, when I reboot everything I cannot get past the Dell logo.

Also, I tried disconnecting the HDD and installing Ubuntu onto a spare 32GB SDD and had the same results, couldn't get past the Dell logo after the first boot.

I'm starting to believe it has to do with the BIOS or with the Linux kernel itself, the weird thing is that neither Windows nor Arch Linux present the same issue.

---

### Post by sandyd on 2015-08-24
Have you tried adjusting the UEFI boot order in the bios? Ubuntu sometimes sets the wrong UEFI boot order after installation.

---

### Post by Rodolfo_Carlos on 2015-08-25
@sandyd I checked the BIOS config and the boot order seems fine :|. 

[IMG]http://i.imgur.com/FQlpiCP.jpg?1[/IMG]

The issue is present even while booting in Legacy mode.

Right now I'm "zeroing" my HDD (dd if=/dev/zero of=/dev/sda) in case that might help, most probably it won't but that's an option I haven't tried.

---

### Post by coldraven on 2015-08-26
Is there an updated BIOS available? I know it's a long shot but this is an odd problem. The downside is that you might have to install Windows to update the BIOS. I recently bricked my HP laptop using a FreeDos bootable USB stick that failed halfway through the update. I don't know much about UEFI so this advice may not be relevant to your machine.

---

### Post by Rodolfo_Carlos on 2015-08-26
@coldraven Already upgraded BIOS to the latest version and also downgraded BIOS to the first version, still the same result.

---

### Post by QIII on 2015-08-26
When you installed other OSes, were they on that same disk?

---

### Post by sandyd on 2015-08-27
Odd, mine lists the actual UEFI entries instead of just 'disk'
[IMG]http://i.imgur.com/NAKqvaC.jpg[/IMG]

Can you try [boot repair]("https://help.ubuntu.com/community/Boot-Repair") from a livecd please?

---

### Post by Rodolfo_Carlos on 2015-08-28
I finally found the source of the problem. I booted into an Ubuntu live USB and executed the efibootmgr application which showed me the list of boot entries. Much to my surprise the list was full of entries of the times I'd been distro-hopping. Something similar to this:


[ubuntu@ubuntu ~]# sudo efibootmgr
BootCurrent: 0004
BootNext: 0003
BootOrder: 0004,0000,0001,0002,0003
Timeout: 30 seconds
Boot0080* UEFI OS
Boot0001* UEFI OS
Boot008B* WINDOWS BOOTLOADER
Boot0090* UEFI OS
Boot0004* KingstonUSB


I then proceeded to delete all the entries with the following command for each entry: 


```
sudo efibootmgr -b [hex_number_of_the_boot_entry] -B

```

Example:


```
sudo efibootmgr -b 8B -B

```

Then, I proceeded to install Ubuntu 14.04 and after that I was able to reboot even 3 times which meant that the problem was solved. I still performed another test with elementary OS 0.2 and rebooting was successful too.


Thanks everyone for your help and guidance, I appreciate it very much. I've been using Ubuntu for about 8 years and once again I'm convinced that it's a great OS with a great community.


I'll be marking this thread as solved.

---

