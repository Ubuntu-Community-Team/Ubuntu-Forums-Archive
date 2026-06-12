---
title: "Grub error after reboot"
date: 2008-06-16
forum: General Help
---

### Post by 164747 on 2008-06-16
PROBLEM
Hi, I have problems with Grub. When I reboot the computer, the Grub menu does not show up, instead Grub throws an error (15 I think). Sometimes (after several "reboots"), it succeeds in building the grub-menu, but then it can't boot any entry, it says something like "Bios cant read beyond sector 1023". However, if you push mem-test 3 times in a row, it will perform a memtest on the third try. I have Also at one time gotten it to boot windows, but windows could not fully boot as it throwed a Blue-screen


A STUPID FIX
If I boot the computer with a live-cd and then runs the following commands 
[FONT="Courier New"]su -
aptitude update
aptitude -y install cryptsetup initramfs-tools hashalot lvm2
modprobe aes-i586
modprobe dm-crypt
modprobe dm-mod
cryptsetup luksOpen /dev/sda3 sda3crypt
mkdir /mnt/root
mount /dev/mapper/sda3crypt /mnt/root
mount /dev/sda2 /mnt/root/boot

chroot /mnt/root
apt-get --reinstall install grub
exit
grub-install --root-directory=/mnt/root /dev/sda
reboot
[/FONT]
Then the grub menu is just fine after THIS reboot. If I reboot again, it is back with the errors again. After searching the internet I changed menu.lst according to

[FONT="Courier New"]
#savedefault=true   ==> savedefault=false
savedefault         ==> #savedefault
[/FONT]
After this the system could boot without errors a couple  (3 I think) of times but then it came back to the same problem.



CONFIGURATION
[FONT="Courier New"]**Linux msd 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

**root@msd:~# cat /etc/crypttab
# <target name>	<source device>		<key file>		<options>
sda3crypt 	/dev/sda3		none 			luks, retry=1
sda4crypt	/dev/sda4		/etc/luks-keys/sda4	luks, retry=1, lvm=vg
sdb1crypt	/dev/sdb1		/etc/luks-keys/sdb1	luks, retry=1, lvm=vg

**Part of fstab
# <file system>		<mount point>		<type>
proc            	/proc           	proc
/dev/mapper/sda3crypt	/               	jfs
/dev/mapper/vg-bkp	/bkp            	jfs
/dev/sda2		/boot           	jfs
/dev/mapper/vg-storage	/storage        	jfs
/dev/mapper/vg-swap	none            	swap

**Grub: 0.97-29ubuntu21

**fdisk /dev/sda -p
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        3886      498015   83  Linux
/dev/sda3            3887       11182    58605120   83  Linux
/dev/sda4           11183       19457    66468937+  83  Linux
[/FONT]


Any suggestions would greatly appreciated!

//David

---

