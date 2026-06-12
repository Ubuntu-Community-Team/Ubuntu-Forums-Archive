---
title: "Cannot boot. Just a Grub command prompt."
date: 2012-10-21
forum: General Help
---

### Post by NHerby on 2012-10-21
Hi,
I had the bad idea to install Mint on a free partition of my system disk. This disk also has a windows 7 and Ubuntu 12.04. It looks like this installation modified the MBR. After removing Mint, I cannot boot anymore. I've tried many tutorials, boot-repair, command lines... When I boot, I have a command line: GRUB>
The only thing I've managed to do is to install Ubuntu (12.10 this time) on the partition where I installed Mint. I can now boot but the Ubuntu 12.04 doesn't show up in Grub. I only have the option to boot on the freshly installed Ubuntu 12.10 or Win7.
Here's a [link]("http://paste.ubuntu.com/1295092/") to the page created by boot-repair.
Ideally, I'd like to remove Ubuntu 12.10 and keep Win7 and Ubuntu 12.04.
I've also noticed that, probably after playing with the options of boot-repair, I now have grub installed on my second drive. Should I remove it? How?
I'd really appreciate some guidance on this problem.

---

### Post by dino99 on 2012-10-21
so boot on 12.10, then into a terminal:

- sudo apt-get remove --purge grub-pc
- sudo apt-get install grub-pc

that will clean your previous config then install a clean grub. Install it on /dev/sda when asked.

---

### Post by offgridguy on 2012-10-21
> **dino99 said:**
> so boot on 12.10, then into a terminal:

- sudo apt-get remove --purge grub-pc
- sudo apt-get install grub-pc

that will clean your previous config then install a clean grub. Install it on /dev/sda when asked.

I am going to save this myself, in case i need it, Thank's

---

### Post by NHerby on 2012-10-21
Thanks for the answer.
No error after putting those lines in the terminal.
But at boot, I still cannot see the 12.04.

---

### Post by NHerby on 2012-10-21
I had a look at the report from boot repair (link in the 1st post) and found this
```
Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda6
and looks at sector 276509136 of the same hard drive
for core.img, but core.img can not be found at this location.
```It looks like there is a probelm with the Core.img that can not be found.

---

### Post by oldfred on 2012-10-21
Normally grub2 installed to a partition is just wasted. It is not used and often not correctly configured anyway.

You install in sda6 shows grub but grub.cfg is almost empty and you do not show any kernels. Was that a working install?

Grub2's os-prober from sda7 looks for the menu entries in sda6 and not finding any does not create any boot entries in sda7's grub.cfg.

---

### Post by NHerby on 2012-10-21
Thanks Oldfred for this answer. But it doesn't help me a lot. I still have no idea how to fix this problem. I think I will go the hard way, completely format the drive and reinstall everything. It may sounds stupid but I think it will save me a lot of time in the end since I also want to re-size some partitions.

---

### Post by oldfred on 2012-10-21
Sometimes reinstall is the quickest solution. Best when you have good backups and lists of installed apps to reinstall.

---

### Post by ~LoKe on 2012-10-22
Er...

Boot into a Live distro (USB or CD).  

Find out which partition your 12.04 install is on, mount it

Move /boot to /boot2

Make a symbolic link from /boot of newly mounted partition to /boot on current Live demo.

Update grub, reboot.

---

### Post by NHerby on 2012-10-22
> **oldfred said:**
> Sometimes reinstall is the quickest solution. Best when you have good backups and lists of installed apps to reinstall.
Well, I have backup made with fwbackups of my /home and /etc on a NAS. Fwbackups also creates a list of installed packages and I still have access to my 12/04 partition. I'm not worried about losing datas.
Can I just copy/paste those folders?
> 
Er...

Boot into a Live distro (USB or CD).  

Find out which partition your 12.04 install is on, mount it

Move /boot to /boot2

Make a symbolic link from /boot of newly mounted partition to /boot on current Live demo.

Update grub, reboot.     Sorry, I'm still a poor linux newbee (but trying hard to cure myself). Correct me if I'm wrong:
Assuming that my 12.04 partition is sda6 and the Live partition should be sdc1. The command line should be:```
sudo mount /dev/sda6 /mnt
```Then
```
sudo mv /mnt/sda6/boot /mnt/sda6/boot2
```Not sure how to make a symbolic link. 
```
ln -s /boot /mnt/sda6/boot
```Also could you explain what this symbolic link will do?
I'm now at work and cannot access my computer. I'll try in a few hours once back at home.

---

### Post by NHerby on 2012-10-22
Youhou!! It's fixed!
Thanks LoKe for putting me on the good path. While following your instructions, I found a folder called boot_bak in the root folder of 12.04.
So I moved the actual boot folder to boot2 and moved this boot_bak to boot, update grub and that's it... After reboot, my 12.04 partition appeared in the list of bootable OS and I'm now using it.
Thanks a lot for your help.

---

### Post by ~LoKe on 2012-10-22
Glad it worked, and glad you stumbled into the solution on your own.  Nice work!

---

