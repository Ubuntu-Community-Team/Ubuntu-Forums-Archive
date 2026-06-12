---
title: "editing /boot/grub/menu.lst"
date: 2007-10-27
forum: General Help
---

### Post by mrmclellan on 2007-10-27
Hi - I just installed Ubunto 7.0.4 onto a multi boot machine.  Grub is installed and working fine as the boot loader.

I want to edit the /boot/grub/menu.lst file so that I can control the delay before the default o/s boots as well as changing the displayed name for the other o/s.

I have figured out how to change the menu.lst file by right clicking and making the changes but I cannot save the changes as I don't have write privileges for that directory.

When I installed Ubuntu I only created a user account.  I wasn't givn the option of creating a root account.

Do I have to learn how to use Gnome Terminal and go down the <sudo =s> approach or is there an easier way to do this??

Thanks

---

### Post by taurus on 2007-10-27
Open a terminal and run

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Use the same password that you log in with.

---

### Post by sandysandy on 2007-10-27
i hope i am not butting in.

i tried the above command (gksudo gedit /boot/grub/menu.lst) and got the menu.lst file. 
the problem is that it is empty. not a word.
however, when i manually go to the menu.lst file the entries are there.
moreover i am unable to save the menu.lst file.

i am using 7.10 (64bit) live cd, though 7.10 is installed on hdd (cannot boot though, figuring it out step by step)

system specs Pentium D 3.0GHz (64bit), 1GB RAM,160Gb SATA hdd (win XP), 40Gb IDE Hdd (Gutsy 7.10)

would appreciate help on editing the menu.lst file.

thanx & regards

---

### Post by Maestro23 on 2007-10-27
> **sandysandy said:**
> i hope i am not butting in.

i tried the above command (gksudo gedit /boot/grub/menu.lst) and got the menu.lst file. 
the problem is that it is empty. not a word.
however, when i manually go to the menu.lst file the entries are there.
moreover i am unable to save the menu.lst file.

i am using 7.10 (64bit) live cd, though 7.10 is installed on hdd (cannot boot though, figuring it out step by step)

system specs Pentium D 3.0GHz (64bit), 1GB RAM,160Gb SATA hdd (win XP), 40Gb IDE Hdd (Gutsy 7.10)

would appreciate help on editing the menu.lst file.

thanx & regards

When you try and edit thru the terminal, are you typing :

> gksudo gedit /boot/grub/menu.**l**st (lower case L)


---

### Post by taurus on 2007-10-27
> **sandysandy said:**
> i hope i am not butting in.

i tried the above command (gksudo gedit /boot/grub/menu.lst) and got the menu.lst file. 
the problem is that it is empty. not a word.
however, when i manually go to the menu.lst file the entries are there.
moreover i am unable to save the menu.lst file.

i am using 7.10 (64bit) live cd, though 7.10 is installed on hdd (cannot boot though, figuring it out step by step)

system specs Pentium D 3.0GHz (64bit), 1GB RAM,160Gb SATA hdd (win XP), 40Gb IDE Hdd (Gutsy 7.10)

would appreciate help on editing the menu.lst file.

thanx & regards

If you are running it from the LiveCD, then you first need to mount your / partition (or /boot if you have a separate /boot partition) before you can edit it!

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by sandysandy on 2007-10-28
thanx Taurus

how do u mount the partition (or /boot) [ as of now i am mounting by double clicking the partition after which i can manually go to the file /disk/boot/grub/menu.lst]

[COLOR="Red"]the out put of sudo fdisk -l is as follows:-[/COLOR]

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40634062

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       16581   107587305    f  W95 Ext'd (LBA)
/dev/sdb3           16582       19456    23093437+   7  HPFS/NTFS
/dev/sdb5            3188        8286    40957686    7  HPFS/NTFS
/dev/sdb6            8287       13385    40957686    7  HPFS/NTFS
/dev/sdb7           13386       16451    24627613+   7  HPFS/NTFS
/dev/sdb8           16452       16581     1044193+   e  W95 FAT16 (LBA)

regards

---

### Post by sandysandy on 2007-10-28
> **Maestro23 said:**
> When you try and edit thru the terminal, are you typing :

thanx

it is in lower case l

i am typing 

gksudo gedit /boot/grub/menu.lst (lower case L)

regards

---

### Post by taurus on 2007-10-28
From the LiveCD,

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Now, you are modifying the one on your harddrive, /dev/sda1.

---

### Post by sandysandy on 2007-10-28
> **taurus said:**
> From the LiveCD,

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Now, you are modifying the one on your harddrive, /dev/sda1.

dear taurus

thanx a ton.

 now i am able to edit the menu.lst file.
without digressing too much, i had one more doubt - since i am unable to boot ubuntu from hdd, would modifying the menu.lst help. [COLOR="Blue"]the menu.lst file is as follows[/COLOR]:-

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by taurus on 2007-10-28
> **sandysandy said:**
> 
 now i am able to edit the menu.lst file.
without digressing too much, i had one more doubt - since i am unable to boot ubuntu from hdd, would modifying the menu.lst help. 

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro **[COLOR="Blue"]quiet[/COLOR]** splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

What's exactly wrong with it?  You can try to remove the **[COLOR="Blue"]quiet[/COLOR]** in your kernel entry from above to see some verbose output when Gutsy boots.

---

### Post by sandysandy on 2007-10-28
thats correct. even i am not able to figure out what is wrong with it. But, I am unable to boot gutsy from hdd. whenever i boot from hdd, i just get the windows XP options, but no option for Gutsy. 
[COLOR="Blue"]just to recapitulate[/COLOR]
my SATA hdd of 160Gb has Win XP loaded on two separate partitions, both loaded before loading Ubuntu Gutsy 7.10.
My IDE hdd of 40Gb hdd has gutsy 7.10.

i tried booting from Super Grub Cd also but to no avail. i got the options of Linux but it did not boot and said [COLOR="DarkOrange"]menu.lst file not found[/COLOR] and gave [COLOR="DarkOrange"]error 15[/COLOR]. From Super Grub Menu i got the following info

[COLOR="Orange"]Natural    Linux-IDE      Linux-SCSI       Grub        HURD[/COLOR]

1                                     hda              sda               (hd0)        hd0

2              hdb              sdb               (hd1)        hd1

3              hdc              sdc               (hd2)        hd2

I also found out from Super Grub that  [COLOR="Green"]hda & hdc[/COLOR] corresponded to both my [COLOR="Green"]Windows partition[/COLOR]. the [COLOR="Red"]hdb[/COLOR] was [COLOR="Red"]empty[/COLOR]. i assume hdb may correspond to Linux, but then linux is on first hdd and win XP on second hdd partitions and so logically linux should be on hda and not hdb (if at all it is there)

would any change be required to menu.lst file or any other file .

thanx

---

### Post by sandysandy on 2007-10-28
> **taurus said:**
> From the LiveCD,

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Now, you are modifying the one on your harddrive, /dev/sda1.

can u please guide me how to unmount my home drive which i mounted using this command:-
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu

regards

---

### Post by taurus on 2007-10-28
> **sandysandy said:**
> can u please guide me how to unmount my home drive which i mounted using this command:-
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu

regards

```
sudo umount /dev/sda1
-or-
sudo umount /mnt/ubuntu
```

---

### Post by sandysandy on 2007-10-29
> **taurus said:**
> ```
sudo umount /dev/sda1
-or-
sudo umount /mnt/ubuntu
```

thanks.

would also appreciate some help on [COLOR="Blue"]sl #11[/COLOR] above.

regards

---

