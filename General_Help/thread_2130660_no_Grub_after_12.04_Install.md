---
title: "no Grub after 12.04 Install"
date: 2013-03-30
forum: General Help
---

### Post by Quarkrad on 2013-03-30
I just done a clean install of 12.04 on a non pae machine that already has winxp on it.  I downloaded an install iso that installs like the normal iso but is configured for the non pae issue.  When I boot I get:

[B]GNU GRUB version 1.99-21ubuntu3.9
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completitions. Anywhere else TAB lists possible device or file completions.
grub>[/B]

I have used the following to try and resolve the issue:

sudo mount /dev/sda5 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda  

and

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
(optional, only if you're on Ubuntu/Debian and wish to reinstall) apt-get install grub-pc
grub-mkconfig -o /boot/grub/grub.cfg (insure that there are NO error messages)
grub-install /dev/sdx (try grub-install --recheck /dev/sdxy if it fails)
Ctrl+D (to exit out of chroot)
sudo umount /mnt/dev
sudo umount /mnt

I have also purged grub and reinstalled - it seems to go OK, I can see grub updating and 'seeing' the winxp partition.  This is the first time in a long time I have been stuck with grub.  Any suggestion appreciated.

---

### Post by carl4926 on 2013-03-30
You should be making this: [COLOR=#000000]grub-install /dev/sdx

this: [/COLOR][COLOR=#000000]grub-install /dev/sda[/COLOR]

---

### Post by Quarkrad on 2013-03-30
ubuntu@ubuntu:~$ grub-install /dev/sda
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ sudo grub-install sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$

---

### Post by Quarkrad on 2013-03-30
This is how my system looks:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24732472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   247433129   123716533+   7  HPFS/NTFS/exFAT
/dev/sda2       247433214   312580095    32573441    5  Extended
/dev/sda5       247433216   310519807    31543296   83  Linux
/dev/sda6       310521856   312580095     1029120   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by plucky on 2013-03-30
> ubuntu@ubuntu:~$ sudo grub-install sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).


This command is wrong, should be ```
sudo grub-install /dev/sda
```

Good Luck

---

### Post by carl4926 on 2013-03-30
> **plucky said:**
> This command is wrong, should be ```
sudo grub-install /dev/sda
```

Good Luck

The OP reported a chroot condition at post #1

sudo is not required

---

### Post by Quarkrad on 2013-03-30
ubuntu@ubuntu:~$ grub-install /dev/sda
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

---

### Post by carl4926 on 2013-03-30
To fix grub from the live cd:
*Be sure you get the partitions correct ie; sda1 or sda2 or sda3 or whatever...

* Open a terminal and type


```
sudo fdisk -l

```

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt
```

sudo mount /dev/sda1 /mnt

```

    * Now mount the rest of your devices


```
sudo mount --bind /dev /mnt/dev

```

    * Now chroot into your system


```
sudo chroot /mnt

```

    *


      When that is done you need to run update-grub to create the configuration file.


```
update-grub

```

```
grub-install /dev/sda
```
reboot

---

### Post by Quarkrad on 2013-03-30
Thanks for your help.  This is what I get:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24732472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   247433129   123716533+   7  HPFS/NTFS/exFAT
/dev/sda2       247433214   312580095    32573441    5  Extended
/dev/sda5       247433216   310519807    31543296   83  Linux
/dev/sda6       310521856   312580095     1029120   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
[B]grep: /proc/mounts: No such file or directory
grep: /proc/swaps: No such file or directory
Cannot find list of partitions!  (Try mounting /sys.)[/B]
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/#

---

### Post by carl4926 on 2013-03-30
If grub wasn't working

Try adding

```
[COLOR=#000000]sudo mount --bind /sys /mnt/sys
```

after the:  [/COLOR][COLOR=#000000]sudo mount --bind /dev /mnt/dev


[/COLOR]

---

### Post by Quarkrad on 2013-03-30
We have got somewhere!!!   Wnen I reboot I get  the following after the bios bit of the boot.

[B]error:  out of disk
error:  out of disk
error:  no suitable mode found
error:  no video mode activated
error:  out of disk

Press any key to continue[/B]

if I press any key, or wait for about 20 secs, I'm taken to the logon screen.  I enter my password and I'm into the Desktop!

---

### Post by Quarkrad on 2013-03-30
Sorry, my last post was before yours.  Shall I perform your last post to address my post above?

---

### Post by Quarkrad on 2013-03-30
I get the same error with the additional command
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found memtest86+ image: /boot/memtest86+.bin
[B]grep: /proc/mounts: No such file or directory
grep: /proc/swaps: No such file or directory[/B]
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sda5
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/#

---

### Post by carl4926 on 2013-03-30
Something is not right, but I can't figure it.
Maybe someone else can. I'd consider backing up your /home/username* (Perhaps you have room in windows to create a folder on C)
You might need to re-install

---

### Post by Quarkrad on 2013-03-30
I added a command to the string your gave me:

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
**root@ubuntu:  sudo mount /proc**
update-grub
grub-install /dev/sda

The effect was that after the bios I actually got a normal grub screen.  I let it default to it's run down time and it went to a blank screen with this text:

[B]error: out of disk
Press any key to continue[/B]

after a while it boots to the Desktop.  Nearly but not quite!  I am reinstalling - fingers crossed.

---

### Post by Quarkrad on 2013-03-30
Back to square 1 - reinstalled (with partition format) and:

[B]error:  out of disk space
grub rescue>[/B]

---

### Post by Quarkrad on 2013-03-30
The ubuntu partition is 30GB

---

### Post by oldfred on 2013-03-30
Some older BIOS and grub seem to have an issue similar to the very old 137GB BIOS boot issue. Not sure if BIOS setting like IDE which should be large or LBA or a bug in grub?

First check BIOS settings.

But the typical work around is to make sure all the boot files are inside the first 100GB of a drive. I normally suggest a small / partition (similar to what you have) but inside the first 100GB of a drive. Or create a small /boot inside the first 100GB of drive. You may be able to shrink Windows, add the /boot and then a NTFS data partition to keep the same size you have for NTFS, just now in two partitions.

---

### Post by Quarkrad on 2013-03-30
This is a friends machine - I use to have both winxp and ubuntu working on it.  It has a 160GB HD that I split approx 50/50.  He needs more space for xp (he only uses it for itunes) so I've increased the xp parition - gparted shows the xp partition to be 117GB and the ext4 partition as 30GB - the xp partition is first on the disk followed by ubuntu.  I have just run the boot info scritp and have a Results.txt file but you suggest it might be this 100GB issue.  What do you suggest I do next?

---

### Post by carl4926 on 2013-03-30
This is what you quoted earlier
```
[COLOR=#000000]Disk /dev/sda: 160.0 GB, 160041885696 bytes[/COLOR]
[COLOR=#000000]255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors[/COLOR]
[COLOR=#000000]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#000000]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#000000]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[COLOR=#000000]Disk identifier: 0x24732472[/COLOR]

[COLOR=#000000]Device Boot Start End Blocks Id System[/COLOR]
[COLOR=#000000]/dev/sda1 * 63 247433129 123716533+ 7 HPFS/NTFS/exFAT[/COLOR]
[COLOR=#000000]/dev/sda2 247433214 312580095 32573441 5 Extended[/COLOR]
[COLOR=#000000]/dev/sda5 247433216 310519807 31543296 83 Linux[/COLOR]
[COLOR=#000000]/dev/sda6 310521856 312580095 1029120 82 Linux swap / Solaris[/COLOR]
```

And did you say it had been working fine previously?

---

### Post by oldfred on 2013-03-30
How full is XP? 
You have to leave 30% free for NTFS to work well. At 10% free it can be really slow.

From live CD click on the XP partition to mount it and run this. Or post gparted screen shot.

df -h

---

### Post by Quarkrad on 2013-03-30
Unfortunately guests have just arrived and I have to go - I will not be able to pick this back up for a few days!   Originally this machine had approx 80GB for winXP and 80GB for ubuntu - dual booting.  I deleted ubuntu - reformated the partition to ntfs and extended the winxp partition to 120GB (although gpartd says 117GB).  I then did a clean install of Ubuntu 12.04 (the non pae version) on the last 30GB partition.  It was after this last clean install that I had the boot/grub problems and started this thread. Oldfred seems to me (but I might be wrong) to be suggesting it could be something to do with the new size of the new winxp partiton.  Thanks for your help and hopefully, for my sake, we can pick this up later next week.

---

### Post by Quarkrad on 2013-03-31
Having resized the xp partition, this is what the HD looks like.

---

### Post by carl4926 on 2013-03-31
It wouldn't be difficult to delete all Ubuntu and extended, shrink windows back some, so you can get Ubuntu inside 100GB

---

### Post by Quarkrad on 2013-04-01
Thank you both.  Oldfred was right - I re-partitioned putting Ubuntu first and it installed, including grub, as per normal.  Much appreciated.

---

