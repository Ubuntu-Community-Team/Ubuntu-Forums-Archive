---
title: "Xubuntu resizing boot partition"
date: 2019-09-20
forum: General Help
---

### Post by Alexander_O on 2019-09-20
Dear all,

I am using xubuntu 18.04. Since yesterday my boot partition is too small for an upgrade. I deleted all the old kernels, but it's still too small. Then, as I read online, I booted xubuntu (18.04) from a USB stick ( 'try xubuntu' ) and installed the 'kde partition manager'. My main partition is encrypted. So I decrypted the main partition in the kde partition manager in order to make it smaller (in order to enlarge my boot partition after it) but I could not resize my main partition at all. Neither the boot partition.

Can please somebody help me? What else can I try? I would really like to avoid reinstalling xubuntu.


Best regards,
Alex

---

### Post by yancek on 2019-09-20
Boot Xubuntu and from a terminal, run this command and post the output here so we have some information.

> sudo fdisk -l  Lower case Letter L in that command.

Need to know if Legacy or EFI, single or multiple systems, EFI partition and boot partition or just a boot partition?

---

### Post by Alexander_O on 2019-09-20
Hi,

here it is: [https://pastebin.com/YqR4MfiW](https://pastebin.com/YqR4MfiW)


Thanks in advance,
Alex

---

### Post by Alexander_O on 2019-09-20
It's EFI (screenshot), single system (Xubuntu 18.04.3) and both partitions - boot and efi (screenshot)

---

### Post by yancek on 2019-09-21
Your GParted output in the post above shows you have over 100MB free on the /boot partition.  Are you getting an error message when trying to upgrade and what is it?  

Also, what exactly happened when you tried to resize the partitions from the Live USB, what messages/errors were reported?

---

### Post by Alexander_O on 2019-09-21
Yes, unfortunately I'm still getting an error message if trying to upgrade - screenshot. 
There were no errors in Live USB partition manager: all the arrows for resizing were greyed out and that's all. I could not move/resize anything, neither with the arrows nor in the partition-rectangle-image above.

---

### Post by Dennis N on 2019-09-21
I'm curious. What's in your boot partition? Keeping two kernels and other boot-related files on my system shows just 107 MB total. What output does the same command show on your system?
```
dmn@Sydney:~$ ls -l -h /boot
total 107M
-rw-r--r-- 1 root root 220K Aug 20 14:32 config-5.0.0-27-generic
-rw-r--r-- 1 root root 220K Sep 12 10:00 config-5.0.0-29-generic
drwx------ 4 root root  512 Dec 31  1969 efi
drwxr-xr-x 5 root root 4.0K Sep 21 06:24 grub
-rw-r--r-- 1 root root  41M Sep 11 20:59 initrd.img-5.0.0-27-generic
-rw-r--r-- 1 root root  41M Sep 18 03:43 initrd.img-5.0.0-29-generic
-rw-r--r-- 1 root root 179K Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root 181K Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root 181K Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root 4.1M Aug 20 14:32 System.map-5.0.0-27-generic
-rw------- 1 root root 4.1M Sep 12 10:00 System.map-5.0.0-29-generic
-rw------- 1 root root 8.4M Aug 20 16:42 vmlinuz-5.0.0-27-generic
-rw------- 1 root root 8.4M Sep 12 10:01 vmlinuz-5.0.0-29-generic

```

---

### Post by Alexander_O on 2019-09-21
Hi,

```
xubu@xubian:~$ ls -l -h /boot
total 350M
-rw-r--r-- 1 root root 1,5M Jul 17  2018 abi-4.15.0-29-generic
-rw-r--r-- 1 root root 1,5M Jul 26  2018 abi-4.15.0-30-generic
-rw-r--r-- 1 root root 212K Jul 17  2018 config-4.15.0-29-generic
-rw-r--r-- 1 root root 212K Jul 26  2018 config-4.15.0-30-generic
-rw-r--r-- 1 root root 213K Aug  6 12:45 config-4.15.0-58-generic
-rw-r--r-- 1 root root 213K Aug 22 18:32 config-4.15.0-60-generic
-rw-r--r-- 1 root root 213K Sep  4 22:11 config-4.15.0-62-generic
drwx------ 3 root root 4,0K Jan  1  1970 efi
drwxr-xr-x 5 root root 1,0K Sep 13 13:49 grub
-rw-r--r-- 1 root root  58M Aug 31 23:05 initrd.img-4.15.0-29-generic
-rw-r--r-- 1 root root  58M Aug 31 23:05 initrd.img-4.15.0-30-generic
-rw-r--r-- 1 root root  58M Aug 31 23:08 initrd.img-4.15.0-58-generic
-rw-r--r-- 1 root root  58M Sep 13 13:49 initrd.img-4.15.0-60-generic
-rw-r--r-- 1 root root  58M Sep 13 13:49 initrd.img-4.15.0-62-generic
drwx------ 2 root root  12K Jun  3  2017 lost+found
-rw-r--r-- 1 root root 179K Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root 181K Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root 181K Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root    0 Jul 17  2018 retpoline-4.15.0-29-generic
-rw-r--r-- 1 root root    0 Jul 26  2018 retpoline-4.15.0-30-generic
-rw------- 1 root root 3,9M Jul 17  2018 System.map-4.15.0-29-generic
-rw------- 1 root root 3,9M Jul 26  2018 System.map-4.15.0-30-generic
-rw------- 1 root root 3,9M Aug  6 12:45 System.map-4.15.0-58-generic
-rw------- 1 root root 3,9M Aug 22 18:32 System.map-4.15.0-60-generic
-rw------- 1 root root 3,9M Sep  4 22:11 System.map-4.15.0-62-generic
-rw------- 1 root root 7,9M Jul 17  2018 vmlinuz-4.15.0-29-generic
-rw------- 1 root root 7,9M Jul 27  2018 vmlinuz-4.15.0-30-generic
-rw------- 1 root root 8,0M Aug  6 19:41 vmlinuz-4.15.0-58-generic
-rw------- 1 root root 8,0M Aug 22 18:37 vmlinuz-4.15.0-60-generic
-rw------- 1 root root 8,0M Sep  4 22:16 vmlinuz-4.15.0-62-generic
xubu@xubian:~$
```

---

### Post by TheFu on 2019-09-21
When you removed the kernels, was **apt** used?  

If using encryption and LVM, resizing the encrypted areas is extremely difficult. I did it once, but never felt like it was 100% correct.  With newer releases, during the installation process, resizing /boot would be easier. I made mine 700MB, just to prevent any issues. Once, 500MB wasn't enough a few releases earlier. Size hasn't been an issue, provided I do a **sudo apt autoremove** monthly.

Resizing LVs is usually pretty straight forward, but that's 4 level deep here - with the partition being 5th level.
Disk--Partition--Encryption blocks--PV--VG--LV

So, to resize the Partition, LV, VG, PV, blocks all need to be unrolled, unused first.
Accessing the data in the LVs, can often been point-n-click by almost all Linux file managers. Just depends.

LVM is extremely flexible, at the cost of a little complexity.

---

### Post by yancek on 2019-09-21
Most users don't keep more than 2 kernels and associated initrd and other files.   YOur last post shows 5 of each and deleting the 3 oldest would give you more than enough space.  Looks like your attempt to remove didn't work or you had a lot more kernels??  Use the command suggested:  sudo apt auto-remove and probably reboot.

---

### Post by Alexander_O on 2019-09-21
Ok. Well, I would be glad to resize just the boot partition too. Or to remove any unnecessary files on /boot. I didn't use apt.

At first I used:

```
sudo dpkg -r $(dpkg -l linux-{image,headers}-"[0-9]*" | awk '/ii/{print $2}' \
               | grep -ve "$(uname -r | sed -r 's/-[a-z]+//')")
```

and then I did:

```
sudo apt-get autoremove --purge
```


//edit

What do you think, can I delete initrd.img-4.15.0-29-generic, initrd.img-4.15.0-30-generic, initrd.img-4.15.0-58-generic and the corresponding System.map-* and vmlinuz-* files or do I need them?

---

### Post by Alexander_O on 2019-09-21
> **yancek said:**
> Most users don't keep more than 2 kernels and associated initrd and other files.   YOur last post shows 5 of each and deleting the 3 oldest would give you more than enough space.  Looks like your attempt to remove didn't work or you had a lot more kernels??  Use the command suggested:  sudo apt auto-remove and probably reboot.


I wondered about it too. Ok, I'll try this! Thanks!

---

### Post by Alexander_O on 2019-09-21
Hi again,

I tried 'sudo apt auto-remove' but the only output I get is:
```

xubu@xubian:~$ sudo apt autoremove
[sudo] password for xubu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
xubu@xubian:~$ 
```

Should I delete the three older kernels manually? Can I also delete the corresponding System.map-* and vmlinuz-* files?


Greets

---

### Post by TheFu on 2019-09-21
Using dpkg directly usually causes more problems than it solves.
I NEVER remove files that were placed by the package manager outside the package manager (some APT front-end).  If you do, you'll never be able to remove those files and dependency issues will be caused. Learned this lesson long ago.

APT is a centralized DB for all installed packages and files.  There are a few different front-ends. Using any of them, should be fine and not cause issues with the APT DB.  dpkg is a lower-level tool. It doesn't update everything that APT needs updated, though it does update parts.  Some of the APT front-ends are:
```
apt
apt-get
aptitude
synaptic
Software Center
```
apt-get supports using package name globbing, which is handy for removing too many kernels, carefully.

Whatever happened in the partition manager, I seriously doubt encryption was actually removed from sda3. Forcing the type to be ext4 won't do that. If you formatted it into ext4, then all that data is gone.

**lsblk** might provide some clarity for how things are organized.  I run an encrypted laptop with LVM. Appears the setup on the system is similar.  [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) shows my setup/layout.

Would be good to see the **df -hT** output to see if anything should be cleared up/simplified for better use later.  We never need to see any "loop" devices, so please remove them from posts.  They don't use any extra space that isn't already included in an LV or partition.

---

### Post by Alexander_O on 2019-09-21
Hi,

thank you all for your answers!

lsblk shows me:

```
NAME                     MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                        8:0    0 119,2G  0 disk  
&#9500;&#9472;sda1                     8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                     8:2    0   488M  0 part  /boot
&#9492;&#9472;sda3                     8:3    0 118,3G  0 part  
  &#9492;&#9472;sda3_crypt           253:0    0 118,3G  0 crypt 
    &#9500;&#9472;xubuntu--vg-root   253:1    0 114,4G  0 lvm   /
    &#9492;&#9472;xubuntu--vg-swap_1 253:2    0   3,9G  0 lvm   [SWAP]
sr0                       11:0    1  1024M  0 rom   
xubu@xubian:~$
```


df -hT shows:

```
xubu@xubian:~$ df -hT
Filesystem                   Type      Size  Used Avail Use% Mounted on
udev                         devtmpfs  1,9G     0  1,9G   0% /dev
tmpfs                        tmpfs     386M  1,6M  385M   1% /run
/dev/mapper/xubuntu--vg-root ext4      113G   90G   17G  85% /
tmpfs                        tmpfs     1,9G  101M  1,8G   6% /dev/shm
tmpfs                        tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        tmpfs     1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda2                    ext4      465M  360M   77M  83% /boot
/dev/sda1                    vfat      511M  6,1M  505M   2% /boot/efi
tmpfs                        tmpfs     386M   48K  386M   1% /run/user/1000
xubu@xubian:~$
```


Greets

---

### Post by Skaperen on 2019-09-21
be sure you **backup** your data, if it's still there.  this case sounds a disaster beginning to happen.  that, or the simple solution is to re-install from scratch, with the partitions better sized.

---

### Post by TheFu on 2019-09-21
I don't see any issues with storage. Here's the important parts:```

$ df -hT
Filesystem                   Type      Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root ext4      113G   90G   17G  85% 
/dev/sda2                    ext4      465M  360M   77M  83% /boot
/dev/sda1                    vfat      511M  6,1M  505M   2% /boot/efi
```
I have an alias to show only the important parts of storage:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

I would try these:```

sudo apt autoclean
sudo apt update
sudo apt upgrade
sudo apt autoremove 
```
In that order.  If any of those commands fail, stop. Often, the output will suggest a fix. Do that.  If you are stuck, post the command and "relevant" output back here.  The middle commands are weekly. The 1st and 4th commands can be run every other week or so to keep storage from being full.

By using apt-get or apt, dependencies should be removed at the same time.  Removing using dpkg, doesn't do that. If those commands above don't clean things up, you'll need to have apt remove the specific packages. That won't be fun.

You can ignore everything that follows for now.  Later ... 

Skipping ahead,  after all this is solved,  I would have laid out the LVs very differently.    / logical volume 25G. That is 10G more than needed.  Then I'd have /home/ with whatever size is needed for everything except media files.  Media files should be stored somewhere else either in a different LV or on the LAN.  Because the current root LV is so full, moving things around isn't easy.  On my SSDs, I try to leave 20% of storage on it unused to help with the SSD lifespan.  Right now, I'm using less than 50% of my available storage.
Some handy LVM commands to get an overview:
```
$ sudo pvs 
  PV                     VG        Fmt  Attr PSize   PFree
  /dev/mapper/sda3_crypt ubuntu-vg lvm2 a--  464.54g 260.08g

$ sudo vgs 
  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   4   0 wz--n- 464.54g 260.08g

$ sudo lvs
  LV      VG        Attr       LSize   Pool Origin Data%  Meta% Move Log Cpy%Sync Convert
  root    ubuntu-vg -wi-ao----  25.00g
  home-lv ubuntu-vg -wi-ao----  75.00g   
  stuff   ubuntu-vg -wi-ao---- 100.00g 
  swap_1  ubuntu-vg -wi-ao----   4.46g

```
root is for the OS. No personal files at all. I backup only specific areas, not everything.
home-lv is for all /home/ directories.  I cleanup temporary files nightly, just before backups.
stuff is for local copies of media and other stuff I never backup. The media that isn't temporary is stored on the network and only gets copied to this laptop for travel. Right now, /stuff is mostly empty.

After a fresh install, reducing the root LV to 25G is really easy.  Creating a HOME LV is easy then.
Why bother with more LVs at all? For me, it is all about backups and what needs to be handled in specific ways.

---

### Post by Alexander_O on 2019-09-21
Hi people,

thanks a lot!

@TheFu

thank you for these

```
sudo apt autoclean
sudo apt update
sudo apt upgrade
sudo apt autoremove
```

it worked great! /boot is using 172M now.

also thanks for the later advice.




Have a nice evening ;)

Greets
Alex

---

### Post by Dennis N on 2019-09-21
Having had 5 installed kernels, you probably aren't using the unattended upgrades feature. When that is enabled, your system will automatically always keep two kernels installed - when the kernel is upgraded, the oldest is automatically removed. I would suggest you look at "Software and Updates" utility > updates tab and set "When there are security updates:" to "Download and install automatically".

---

### Post by Alexander_O on 2019-09-21
Ok I'll do this. Thanks ;)

---

