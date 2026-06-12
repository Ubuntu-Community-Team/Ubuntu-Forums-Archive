---
title: "Restore /boot after mistakenly formatted /boot partition"
date: 2017-04-12
forum: General Help
---

### Post by i2000s2 on 2017-04-12
I formatted /boot partition in Windows 10 as the OS asked me to get more space for a recent Creator Update by formatting 2 "unformated" partitions--I realized later that one is SWAP and the other one is /boot partition of my Ubuntu 16.04 OS installed in parallel with Windows 10. Now, either Windows or Ubuntu cannot be booted up on my computer. The windows OS was one option of the GRUB loader of Ubuntu OS. Both OS were installed in /dev/sdb disk (SSD) while I have backups in /dev/sda HDD disk. Unfortunately, I don't think I have the /boot partition backed up in my Ubuntu Deja-Dup app. The root partition and home partition were installed on a LVM and btrfs filesystems. How can I rebuild my /boot partition and make the computer work again?

I have tried using boot-repair to fix the boot partition, but it asked me to boot the LiveCD in UEFI mode. But if I enable the UEFI booting option on BIOS, then my computer cannot recognize my LiveCD USB stick. The LiveCD usb stick can only be booted up in the Legacy mode. I have also tried using chroot to reinstall linux-image, but in the chroot mode, I cannot run apt-get at all. It shows it cannot find /etc/apt/source.list and other files and dpkg was denied as I don't have the root permission (it's strange). I have searched online for days, none worked out for me. What can I do to fix this? 

Thank you!

---

### Post by i2000s2 on 2017-04-13
Ok, I managed to booted into UEFI mode, and run the boot-repair info: [http://paste2.org/ZvsBb92Z](http://paste2.org/ZvsBb92Z)
Boot-repair cannot run normally to restore the /boot partition and grub, as there is always an error asking me to "close all package managers" which I don't think I have any open. Still not sure how to handle this...

Update: I followed some steps from [http://forums.debian.net/viewtopic.php?f=30&t=98324](http://forums.debian.net/viewtopic.php?f=30&t=98324) and installed some kernel files to /boot. I hope this can help me move onto update grub, following instructions like [https://ubuntuforums.org/showthread.php?t=2168334](https://ubuntuforums.org/showthread.php?t=2168334) . IstiCurrently, made a boot-repair-disk but no internet access. I need some sleep now. Comments are appreciated. I still cannot run any command in chroot mode.

---

### Post by oldfred on 2017-04-13
I do not know LVM & encryption.

But you are showing two ESP - efi system partitions on sdb. That almost always causes issues.
UEFI does allow more than one, but I have not seen that work with any system. And a few that have two, hide one or remove boot flag & then switch boot flag, so not really two ESP, just two FAT32 partitions with only one in use as ESP at a time.

Your sdb9 cannot be an ESP as it is ext4, and ESP must be FAT32. Remove boot flag from sdb9 with gparted or other tools.

The other issue may be that with UEFI, grub only installs to the ESP on sda. But  you have an old MBR(msdos) partitioned drive on sda.
There is some way to flag a MBR partition as ESP, but UEFI normally uses gpt.

You may be able to unplug sda, so current sdb seen as sda, to get grub to install correctly.

---

### Post by i2000s2 on 2017-04-13
> **oldfred said:**
> I do not know LVM & encryption.

But you are showing two ESP - efi system partitions on sdb. That almost always causes issues.
UEFI does allow more than one, but I have not seen that work with any system. And a few that have two, hide one or remove boot flag & then switch boot flag, so not really two ESP, just two FAT32 partitions with only one in use as ESP at a time.

Your sdb9 cannot be an ESP as it is ext4, and ESP must be FAT32. Remove boot flag from sdb9 with gparted or other tools.

The other issue may be that with UEFI, grub only installs to the ESP on sda. But you have an old MBR(msdos) partitioned drive on sda.
There is some way to flag a MBR partition as ESP, but UEFI normally uses gpt.

You may be able to unplug sda, so current sdb seen as sda, to get grub to install correctly.

Hi @oldfred,

Glad to have you on my thread! I have seen a lot of your posts regarding boot-repair which are very insightful. Since I am a newbie in this regard, could you give me a few more details on what I should do to make the computer work again? My understanding on the steps to follow is:

1. Remove/disconnect the HDD (sda) from my computer. But would this lead me to rebuild the disk table at some point?
2. Boot up the computer using my Ubuntu 16.04.2 LiveCD and then open GParted to remove the boot flag on sdb9 (it may be recognized as sda9?). 
3. Run boot-repair again in the LiveCD environment without putting a boot flag? But still have the separated /boot on sdb9 and /boot/efi on sdb7. Since I have made some linux-image files in the /boot partition which might not be the original one yet still couldn't run apt-get or dpkg commands in chroot mode with permission issues, I guess I will still need to have the internet connection to update the kernel and so on. 
4. If the boot-repair doesn't work as before (it asked me to class all package managers which I didn't have any open), I may be able to use the following command to rebuild the grub?: 
[COLOR=#000000]
sudo fdisk -l # to confirm the /root is ubuntuvg/root and /boot is sdb9 and so on. 
sudo mount -t btrfs /dev/ubuntuvg/root /mnt 
sudo mount /dev/sdb9 /mnt/boot 
sudo mount /dev/sdb7 /mnt/boot/efi[/COLOR]
[COLOR=#000000]sudo grub-install --root-directory=/mnt/ /dev/sdb # After removing the HDD, the SSD disk might become sda instead of the old sdb. Need to confirm in the first step.[/COLOR]
[COLOR=#000000]# The above command should work but I may also need the following for grub 2.02 with Xenial 16.04:[/COLOR]
[COLOR=#000000]sudo grub-install --boot-directory=/mnt/boot /dev/sdb[/COLOR]
[COLOR=#000000]#If that returns any errors run:[/COLOR]
[COLOR=#000000]sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb[/COLOR]
[COLOR=#000000]# If no errors on previous commands reboot into working system and run this:[/COLOR]
[COLOR=#000000]sudo update-grub[/COLOR]


Let me know if this is the minimal steps that I can try. I will return my result once it's confirmed feasible. Thanks.

---

### Post by oldfred on 2017-04-13
If you disconnect current sda, then all the sdb references should then be sda.

Boot-Repair will only work if you mount & unencrypt the LVM. It sometimes gets confused with RAID & LVM as both can use /mapper. And then it may not install grub correctly. (or really it is grub as Boot-Repair is just running commands.)

Do not know the chroot mount with LVM & encryption.
I expect you have to include the LVM mount & decrypt the encrypted partition's root. And then mount those.

Fdisk will only show physical partitions, not the logical partitions inside the LVM.

See steps 1 thru 4 and it was before UEFI, so you must  also mount the ESP as you had posted above.
[https://ubuntuforums.org/showthread.php?p=4530641](https://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by i2000s2 on 2017-04-13
I don't think my LVM Volume Groups are encrypted. Maybe I need to do the following before running any commands in chroot:

chroot /mnt/sabayon /bin/bash
env-update
source /etc/profile
export PS1="(chroot) $PS1"

Ref: [https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD](https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD)

I maybe able to try it later. But I would do some research to understand what you are saying. Thanks for your insight!

---

### Post by i2000s2 on 2017-04-13
Ok, I got frustrated! chroot doesn't give me root permission, not only that, there are all kinds of files missing errors. If I run boot-repair, again it will ask me to close all package managers which I don't have in open. I don't know what's the problem after googling around for a day. I gave up on reinstalling MBR on the SSD (sdb) as it seems complicated. Maybe it's time for me just backup the files and reinstall Ubuntu 16.04.2 instead of wasting time on fixing those things.

Latest system info with only one disk: [http://paste2.org/VAHO8pjP](http://paste2.org/VAHO8pjP)

---

### Post by oldfred on 2017-04-14
Is this file just sitting their?
/var/lib/dpkg/lock

That is supposed to be created with any update process and to prevent other update processes from starting. But if just there, it did not get deleted on the end of an update. If absolutely sure an update process is not running, just delete it.

If you do not have encryption, not sure why you want LVM.
LVM was another one of the work arounds for the 4 primary partition limit with MBR(msdos). And one of its advantages is easier partition changes using its tools, but it then needs to be the entire drive.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) 

Also some have posted in past that BTRFS is not quite ready for prime time. They keep making improvements and some use it for testing.
 EXT4, Btrfs, XFS & F2FS On Linux 4.6 Through 4.9
[http://www.phoronix.com/scan.php?page=article&item=4fs-linux-4649&num=1](http://www.phoronix.com/scan.php?page=article&item=4fs-linux-4649&num=1) 

With two drives, I also liked to keep Windows & Ubuntu on separate drives. But would then suggest that both be gpt with UEFI installs. And second drive include all the standard partitions including ESP, even though grub will install to ESP on sda.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by i2000s2 on 2017-04-14
Ha, this looks simple to do. I don't know why there was an update process not finished, but I don't think there is anything important hanging there. I will try to delete the /varlib/dpkg/lock file shortly. 

Another problem is I don't have any free space left in the /sdb disk and hence it's hard to install the MBR there. I have tried to run grub-update, but it had problems with installing on sdb (sda when I removed the HDD). I will try to install the MBR in the original /sda disk first. Also, the /boot partition cannot be flagged as /boot as it will be automatically marked as ESP again. I guess this might be related to the fact that /boot/efi on the other partition has been marked as ESP which might have affected /boot partition? But I have made a boot label for the /boot partition, and I hope it works.

Regarding the LVM and the two-disk configuration, I had the Windows OS preinstalled on the /sda disk which is HDD. Then I formatted the disk and reinstalled the Windows and then the Ubuntu OS on the /sdb disk which is an SSD. I regret not to have the HDD uninstalled while installing the OS's which made the MBR installed in a strange way in the end (it may also because the formation of disk sda didn't remove the MBR zone). For me, I prefer to have the OS's installed on the SSD as it's dramatically faster than HDD. Also I plan to have two more NVMe disks replacing the SSD disk in the near future for a better performance and more space. That is the main reason I use LVM and put all OS's on one disk. The HDD stores my backups and all data files. LVM will be useful when I want to extend the /home directory over the new NVMe cards later. 

Thank you for all the references. I will give a last try and hopefully, everything can be fixed then.

---

### Post by i2000s2 on 2017-04-14
> **oldfred said:**
> Is this file just sitting their?
/var/lib/dpkg/lock

That is supposed to be created with any update process and to prevent other update processes from starting. But if just there, it did not get deleted on the end of an update. If absolutely sure an update process is not running, just delete it.



I just tried deleting the file, but it cannot recognize my `rm` command. All the command line history can output is below:
```

ubuntu-gnome@ubuntu-gnome:~$ sudo apt update
Ign:1 cdrom://Ubuntu-GNOME 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215) xenial InRelease
Hit:2 cdrom://Ubuntu-GNOME 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215) xenial Release
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:5 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [247 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [512 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [105 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [207 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [287 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.2 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [47.4 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7,428 B]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,428 B]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [108 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [55.5 kB]
Get:18 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [188 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7,776 B]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,548 B]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [457 kB]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [175 kB]
Get:25 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:26 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Fetched 3,085 kB in 2s (1,130 kB/s)                                  

** (appstreamcli:3360): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
137 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu-gnome@ubuntu-gnome:~$ sudo apt install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version (2.02.133-1ubuntu10).
0 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.
ubuntu-gnome@ubuntu-gnome:~$ sudo vgchange -ay ubuntuvg #make the ubuntuvg available.
  2 logical volume(s) in volume group "ubuntuvg" now active
ubuntu-gnome@ubuntu-gnome:~$ sudo lvscan 
  ACTIVE            '/dev/ubuntuvg/root' [35.00 GiB] inherit
  ACTIVE            '/dev/ubuntuvg/home' [110.22 GiB] inherit
ubuntu-gnome@ubuntu-gnome:~$ cd ~/Downloads/
ubuntu-gnome@ubuntu-gnome:~/Downloads$ sudo -s
root@ubuntu-gnome:~/Downloads# mount -t btrfs /dev/ubuntuvg/root /mnt -o rw
root@ubuntu-gnome:~/Downloads# mount -t btrfs /dev/ubuntuvg/home /mnt/home -o rwroot@ubuntu-gnome:~/Downloads# mount -t ext4 /dev/sdb9 /mnt/boot -o rw
root@ubuntu-gnome:~/Downloads# #mkdir -p /mnt/boot/efi
root@ubuntu-gnome:~/Downloads# mount /dev/sdb7 /mnt/boot/efi -o rw
root@ubuntu-gnome:~/Downloads# mount --bind /dev /mnt/dev
root@ubuntu-gnome:~/Downloads# mount --bind /dev/pts /mnt/dev/pts
root@ubuntu-gnome:~/Downloads# mount --bind /sys /mnt/sys
root@ubuntu-gnome:~/Downloads# mount -t proc proc /mnt/proc
root@ubuntu-gnome:~/Downloads# cp -f /etc/resolv.conf /mnt/etc/resolv.conf
root@ubuntu-gnome:~/Downloads# chroot /mnt /bin/bash
bash-4.3# apt update
Get:1 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Err:2 http://security.ubuntu.com/ubuntu xenial-security InRelease 
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Err:1 http://archive.ubuntu.com/ubuntu xenial InRelease      
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Err:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: No sandbox user '_apt' on the system, can not drop privileges
W: GPG error: http://security.ubuntu.com/ubuntu xenial-security InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
E: The repository 'http://security.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://archive.ubuntu.com/ubuntu xenial InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
E: The repository 'http://archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://archive.ubuntu.com/ubuntu xenial-updates InRelease: Could not execute 'apt-key' to verify signature (is gnupg installed?)
E: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bash-4.3# rm /var/lib/dpkg/lock
bash: rm: command not found
bash-4.3# grub-install
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
bash-4.3# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
bash-4.3# dpkg -S /boot
dpkg-query: error: failed to open package info file '/var/lib/dpkg/status' for reading: No such file or directory



```

It looks different from other people's experience using chroot: after running `chroot /mnt` I got the `bash-4.3#` prompt, but I see others have the `(chroot)` prompt; secondly, I cannot use `ls` and other bash commands, but some others like `cd` works. Why is that. It has cost me a lot of time now. Maybe I should consider reinstalling the OS... What do you think what I can try for the last time?

---

### Post by oldfred on 2017-04-14
I thought you did not need sudo once chrooted?
But not familiar with your security errors. I think I have seen a few threads with them.

I would think if you have NVMe drives, you want UEFI & gpt. And operating systems on those fast drives where data can be on slower HDD as not accessed as much.

With LVM, if any drive fails you lose all data on all drives. So just be sure to have good backups.

I keep /home inside my / (root) so user configs load quickly from SSD, but have smaller SSD and then larger HDD for data.

Grub does not use boot flag at all. Windows requires boot flag on NTFS partition with boot files in BIOS mode on MBR partitioned drives.
With gpt all systems require boot flag on ESP only, never on any other partition.
Boot flag with gpt is not really boot flag like MBR. It is just a signal to gparted to assign a very long GUID that says that partition is the ESP and UEFI should then find it.

---

### Post by i2000s2 on 2017-04-14
Thank you for the prompt response! I didn't use sudo after chroot. But the error is very annoying. After a little bit of search, I didn't find any useful information and don't know what to do. Why it's so different from all other people's experience using chroot and even my own past experience using chroot? Did I broken some root file already? I cannot even see what files the chroot mode is loading. Under the normal mode outside of chroot, my /mnt directory has the following directories:
```
ubuntu-gnome@ubuntu-gnome:/mnt$ ls
@    boot      BootInfo  dev  home  lib64  proc  sys  usr
bin  boot_bak  boot-sav  etc  lib   media  run   tmp  var
ubuntu-gnome@ubuntu-gnome:/mnt$ cd var/
ubuntu-gnome@ubuntu-gnome:/mnt/var$ ls
apt  lib  log
ubuntu-gnome@ubuntu-gnome:/mnt/var$ cd lib/
ubuntu-gnome@ubuntu-gnome:/mnt/var/lib$ ls
apt
ubuntu-gnome@ubuntu-gnome:/mnt/var/lib$ cd /mnt/@
ubuntu-gnome@ubuntu-gnome:/mnt/@$ ls
bin   cdrom  dev  home  lib32  media  opt   root  sbin  srv  tmp  var
boot  core   etc  lib   lib64  mnt    proc  run   snap  sys  usr
ubuntu-gnome@ubuntu-gnome:/mnt/@$ cd var/
ubuntu-gnome@ubuntu-gnome:/mnt/@/var$ ls
backups  crash  lib    lock  mail     opt  snap   tmp
cache    games  local  log   metrics  run  spool



```
It seems all root files are in the `@` directory. Under the /mnt/var directory, there is even no such `dpkg` folder. Is this normal?

---

### Post by oldfred on 2017-04-14
I have not tried a chroot for years.
But also wonder where @ folder is coming from?

Your Summary Report from Boot-Repair did not show fstab. Maybe because LVM  not yet mounted when it looks for that.
But do you have any other system folders as partitions?

---

### Post by i2000s2 on 2017-04-14
I don't understand that neither. I just appears after I mount the root directory. Have I ruined my other partitions already?

I have /boot, /boot/efi, / and /home in separated partitions, and should have mounted them or activated the LVM logic volumes before the boot-repair step. But whenever I mount the partitions, I always have the @ folder to have all the files.

---

### Post by i2000s2 on 2017-04-14
I think I have to give up. I will be reinstalling Ubuntu 16.04  GNOME-Desktop next. Thank @oldfred for the patient help along the way!

---

### Post by i2000s2 on 2017-04-15
I tried to reinstalling, but it crashed! Ubiquity package seems to have a bug. I am not clear what happened. I read some references you shared to me and decided to install the boot loader to /dev/sdb7 where UEFI files are located. I don't know if this is relevant. Trying again...

Update: reinstalled again, it installed but then it hanged on the black screen before login. More lessons to learn...

---

