---
title: "My computer does not boot up"
date: 2020-09-22
forum: General Help
---

### Post by damicogiuseppe77-2 on 2020-09-22
Hi, since a couple of day, my computer with Ubuntu 18.04 Is not able to boot,maybe now my fstab Is messed up, on the root Shell with the command sudo findmnt --verify --verbose,I get this message: [E] unreachable on boot required source UUID=759fe52e-... I got the UUID with blkid.
My fstab Is:
# ...
UUID=759fe52e-....   / ext4 default 0 1

Thanks in advance

---

### Post by dino99 on 2020-09-23
Be sure that 'sudo blkid' output is matching with /etc/fstab

---

### Post by oldfred on 2020-09-23
Perhaps closed abnormally and needs fsck?
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If not fsck, then to confirm boot configuration is otherwise ok:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by damicogiuseppe77-2 on 2020-09-23
Thanks: after boot-repair, my computer still Ford not boot up,this Is the pastebin: [http://paste.ubuntu.com/p/Jy4vgz95VD/](http://paste.ubuntu.com/p/Jy4vgz95VD/)

---

### Post by oldfred on 2020-09-23
Ignore all errors on sdb, your flash drive. As a hybrid DVD/flash drive it does not have standard partitions, so shows errors. 

It says grub correctly reinstalled.
You have old BIOS/MBR configuration.

Since only one install, if you hold shift key from BIOS screen, are you able to get to grub menu?
And then try to boot recovery mode?

What brand/model system?
What video card/chip?

---

### Post by damicogiuseppe77-2 on 2020-09-24
It Is a i7 Sony vaio,
I can get ti grub menù and the root shell
NVIDIA GeForce GT 520M

---

### Post by oldfred on 2020-09-24
Then in grub menu press e for edit and add nomodeset to linux line. I normally replace quiet splash, so then you also see boot process.

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by damicogiuseppe77-2 on 2020-09-24
It does not work

---

### Post by oldfred on 2020-09-24
Do you get grub menu?
Can you boot recovery mode?

---

### Post by damicogiuseppe77-2 on 2020-09-25
Yes i can

---

