---
title: "Black screen on Ubuntu 22.04.3"
date: 2024-01-09
forum: General Help
---

### Post by kotgc on 2024-01-09
I removed SSD 3 of 4 which is an empty disk  and connected a LinuxMint SSD to test if the LinuxMint SSD was fried or not. The LinuxMint SSD ran perfectly.
I then shutdown, disconnected the LinuxMint SSD and reconnected SSD 3 of 4.

SSD1 of 4 has Ubuntu 22.04.3 LTS on sda2, however now it won&#8217;t boot into a graphical interface?

Boot with no USB in machine -> hold Shift key down -> select Ubuntu Advanced Mode -> select Ubuntu, with Linux 6.2.0-39-generic (recovery) -> Recovery Menu (filesystem state: read-only) text menu: resume; clean; dpkg; fsck; grub; network; root; system-summary.
1: Recovery mode text menu -> I selected resume: Resume normal boot -> You are now going to exit the recovery mode and continue the boot sequence. Please note that some graphic drivers require a full graphical boot and so will fail when resuming from recovery. If that's the case, simply reboot from the login screen and then perform a standard boot: I selected OK -> but boots to black screen.

2: Recovery mode text menu -> network selection -> boot into root -> circles back to the recovery options text menu.

3: Recovery mode text menu -> I selected the command prompt -> command $ sudo startx, but error:
xinit: connection to X server lost
waiting for X server to shut down (II) Server terminated successfully (0). Closing log file.

I tried command ffplay videoName.mp4.
The /var/log/Xorg.0.log file shows errors, but not sure how to upload photos of 400 lines?

Also the KVM should have auto started, however this appears to not be the case. I ran command # virt-manager but message: (virtual-manager: 1236): Gtk-WARNING **: 11:06:10.577: cannot open display
I&#8217;m trying to boot KVM so the virtual router can connect the network and Internet.

# ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING> nut 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6 ::1 prefixlen 128 scopeid 0x10<host>
loop txqueuelen 1000 (Local Loopback)
RX packets 2240 bytes 165760 (165.7 KB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 2240 bytes 165760 (165.7 KB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

root@ubuntu:/# lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINTS
sda 8:0 0 223.6G 0 disk
|&#8212;sda1 8:1 0 512M 0 part /boot/efi
|&#8212;sda2 8:2 0 223.1G 0 part /
sdb 8:16 0 111.8G 0 disk
|&#8212;sdb1 8:17 0 111.8G 0 part
sdc 8:32 0 111.8G 0 disk
|&#8212;sdc1 8:33 0 111.8G 0 part
sdd 8:48 0 0 111.8G 0 disk
|&#8212;sdd1 8:49 0 111.8G 0 part

---

### Post by MAFoElffen on 2024-01-09
Do not try to start X as Root. It needs to be logged in as a User. (I saw your prompt as root...) That doesn't work without a bit of hacking (which is not a good idea).

What happens if you go to recovery mode then to resume? That would be the equivalent to starting with nomodeset...

Or, from the Grub2 menu, press the <E> key to get into an edit mode > go down to the line the starts with "linux" > Replace the words "quiet splash" with "--- 3", then <Contrl><X> to start... It should then to boot to a console, where you can log in as your User, then use "startx" to start the graphics layer to diagnose why it is not coming up as your user...

---

### Post by kotgc on 2024-01-09
Thank you, I tried all your suggestions however Ubuntu shows a black screen when recovery mode is used.
With user$ startx -> Enter -> black screen -> after ~2 minutes a graphical image appears in grey and orange Ubuntu icon: Sorry, the application had-usb-protection has stopped unexpectedly. Send problem report to the developers? If you notice further problems, try restarting the computer. Remember this in future. Show Details, Don’t send, Send.

No keyboard or mouse control to select the options.

---

### Post by MAFoElffen on 2024-01-10
Please boot an Ubuntu Installer LiveUSB... Use the "Try" option. Download & run the 'system-info' script in my signature line. Select to upload the report to a pastebin. Please post the URL of where it uploads in a post.

---

### Post by kotgc on 2024-01-10
[https://termbin.com/chtv](https://termbin.com/chtv)

---

### Post by MAFoElffen on 2024-01-10
What drive/partition on that report is your Ubuntu root system installed to?

And do you have a way out to the network if you boot from an Installer LiveUSB? I remember you saying your router is inside a VM that is on that machine...

If you boot to a console vai option #2 from the last post, did you have networking? 

If so... Then do
```

sudo apt update
sudo apt remove --purge nvidia* libnvidia*
sudo apt install nvidia-driver-470
sudo reboot

```
If not, then answer which drive/partition is your root, ad I will give directions to to chroot from a LiveUSB to do the same from there. Either way, you would need an internet connection to do it either way.

---

### Post by kotgc on 2024-01-10
Ubuntu is installed on SSD1 of 4, which is /dev/sda. I think that’s the /dev/sda2 thingy that boots, however I am unsure?

Yes, somehow magically, the Live USB has Internet; and yes the machine typically only has network LAN/WAN access via a KVM router.
No, the option 2 recovery mode? doesn’t have Internet.
Sorry, I’m unclear if you’re referring to post #4 as the ‘last post’?
Ubuntu recovery mode just boots to a black screen and in command prompt, ping 1.1.1.1 fails.

---

### Post by MAFoElffen on 2024-01-11
When you boot the Installer LiveUSB > Try > Open terminal
```

sudo su -
mount /dev/sda2 /mnt

```
Do this first to check to see if it looks like a root partition
```

ls /mnt

```
If it does have something similar to this
```

root@ubuntu:/home/ubuntu# ls /
bin   cdrom  etc   lib    lib64   media  opt   rofs  run   snap  sys  usr
boot  dev    home  lib32  libx32  mnt    proc  root  sbin  srv   tmp  var

```
Then do 
```

root@ubuntu:/home/ubuntu# ls /
bin   cdrom  etc   lib    lib64   media  opt   rofs  run   snap  sys  usr
boot  dev    home  lib32  libx32  mnt    proc  root  sbin  srv   tmp  var

```
Then do 
```

umount /mnt

```
and repeat the mount command on a different partition... and recheck until you find it.

Once you find it then do
```

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot /mnt /bin/bash --login
mount -a
apt update
apt remove --purge nvidia* libnvidia*
apt install nvidia-driver-470
reboot

```
Remove the LiveUSB and test it.

---

### Post by kotgc on 2024-01-11
LiveCD -> Try -> Terminal -> ubuntu@ubuntu:~$ sudo su - -> select Enter -> root@ubuntu:~# mount /dev/sda2 -> select Enter -> mount: /dev/sda2: can’t find in /etc/fstab. 
root@ubuntu:~# ls / -> select Enter -> those directories you show appear.

What do I do about the error?

---

### Post by MAFoElffen on 2024-01-11
Edit my last post, #8

Sorry. Omitted the mount point. Was tying quickly, right before bed...

Please try again.

---

### Post by kotgc on 2024-01-11
Issue remains.
I tried to find the root with this command, but it seems to only pickup the live usb:
root@ubuntu:/home/ubuntu/Desktop# df
Filesystem                  1K-blocks    Used Available Use% Mounted on
tmpfs                         1625844   10176   1615668   1% /run
/dev/sde1                     4914194 4914194         0 100% /cdrom
/cow                          8129216  284780   7844436   4% /
/dev/disk/by-label/writable   9958660   63012   9368188   1% /var/log
tmpfs                         8129216       0   8129216   0% /dev/shm
tmpfs                            5120       8      5112   1% /run/lock
tmpfs                         8129216     572   8128644   1% /tmp
tmpfs                         1625840     152   1625688   1% /run/user/999


I’m not sure /dev/sda2 is root but I just went with it…the files shown are the same as your example.
Removing nvidia command said no nvidia to remove.
Nvidia install said latest package is already installed. 
I had to exit chroot to reboot.

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0     3G  1 loop /rofs
loop1    7:1    0     4K  1 loop /snap/bare/5
loop2    7:2    0  63.4M  1 loop /snap/core20/1974
loop3    7:3    0  73.9M  1 loop /snap/core22/858
loop4    7:4    0 237.2M  1 loop /snap/firefox/2987
loop5    7:5    0 349.7M  1 loop /snap/gnome-3-38-2004/143
loop6    7:6    0 485.5M  1 loop /snap/gnome-42-2204/120
loop7    7:7    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop8    7:8    0  53.3M  1 loop /snap/snapd/19457
loop9    7:9    0   452K  1 loop /snap/snapd-desktop-integration/83
loop10   7:10   0  12.3M  1 loop /snap/snap-store/959
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part 
&#9492;&#9472;sda2   8:2    0 223.1G  0 part 
sdb      8:16   0 111.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 111.8G  0 part 
sdc      8:32   0 111.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 111.8G  0 part 
sdd      8:48   0 111.8G  0 disk 
&#9492;&#9472;sdd1   8:49   0 111.8G  0 part 
sde      8:64   1  14.4G  0 disk 
&#9500;&#9472;sde1   8:65   1   4.7G  0 part /cdrom
&#9500;&#9472;sde2   8:66   1   4.9M  0 part 
&#9500;&#9472;sde3   8:67   1   300K  0 part 
&#9492;&#9472;sde4   8:68   1   9.7G  0 part /var/crash
                                 /var/log
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# mount --make-private --rbind /dev/ /mnt/dev
mount: /mnt/dev: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /proc/ /mnt/proc
mount: /mnt/proc: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /sys/ /mnt/sys
mount: /mnt/sys: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /run/ /mnt/run
mount: /mnt/run: mount point does not exist.
root@ubuntu:~# ls /mnt/
root@ubuntu:~# ls /
bin  boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var

---

### Post by MAFoElffen on 2024-01-11
Comment:

How NVidia linux drivers have broken over the span of the past 15 years during a kernel update, is, even after all that time, it happens occasionally.

Yes it said it was installed. That is to the problem. It needed to be reinstalled, compile with the new kernel. To do that, it is one packaage that you cannot just tell it to reinstall. You remove it, then install it again.

You just said you did not follow those directions. You instead tried to install it, without removing it. So there was no change made then, was there...

Good luck with that...

---

### Post by kotgc on 2024-01-11
Well I ran nvidia uninstall, but error says nothing to uninstall.
I then ran the nvidia install and it said Nvidia is already installed?
This all happened the 1st time.
Now with subsequent attempts, I'm receiving new errors:
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# mount --make-private --rbind /dev/ /mnt/dev
mount: /mnt/dev: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /proc/ /mnt/proc
mount: /mnt/proc: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /sys/ /mnt/sys
mount: /mnt/sys: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /run/ /mnt/run
mount: /mnt/run: mount point does not exist.

---

### Post by MAFoElffen on 2024-01-11
I ignored what you said about what you thought you did... And instead looked at your output...

You skipped over mounting /dev/sda2 to /mnt, so everything failed after that. For example run, sys, proc & dev had nothing to mount to, because /dev/sdb2 was not mounted.

reread the instructions carefully, and try again.

Any errors, stop and post back.

---

### Post by kotgc on 2024-01-11
I'm still not even sure /dev/sda2 is the root.
I followed your post #8, however perhaps /dev/sda1 is the root?
I think /dev/sda2 is, but I wouldn't bet your life on it.

I follow your post #8, however the output is an error:
root@ubuntu:/home/ubuntu/Desktop# sudo su -
root@ubuntu:~# mount /dev/sda2 /mnt/
root@ubuntu:~# ls /mnt/
bin  boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swapfile  sys  tmp  usr  var
root@ubuntu:~# ls /
bin  boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var
root@ubuntu:~# umount /mnt 
root@ubuntu:~# mount --make-private --rbind /dev/ /mnt/dev
mount: /mnt/dev: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /proc/ /mnt/proc
mount: /mnt/proc: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /sys/ /mnt/sys
mount: /mnt/sys: mount point does not exist.
root@ubuntu:~# mount --make-private --rbind /run/ /mnt/run
mount: /mnt/run: mount point does not exist.

Perhaps the command should be:
mount --make-private --rbind /dev/sda2 /mnt/dev/sda2
however I'm unwilling to try it, to avoid wiping the OS or something exploding!

---

### Post by MAFoElffen on 2024-01-12
LOL. Leave it mouted!!! I meant not to do not do umount, unless it was the wrong drive...

That is the only reason it posted that, for the just in case you needed to unmount it, and mout another partition.

It looked like /dev/sba2 was the correct partition...

Try it again, but do not do that first umount....

---

### Post by kotgc on 2024-01-12
Ok, made progress with these correct commands:
Live USB -> Terminal ->
sudo su - -> select Enter ->
mount /dev/sda2 /mnt -> select Enter ->
ls /mnt -> select Enter ->
ls / -> select Enter ->
umount /mnt -> select Enter ->
mount /dev/sda2 /mnt -> select Enter -> (this is the issue where I was unsure if /dev/sda2 was root and did not know this command was needed to create a mountable directory)
mount --make-private --rbind /dev  /mnt/dev-> select Enter ->
mount --make-private --rbind /proc /mnt/proc-> select Enter ->
mount --make-private --rbind /sys  /mnt/sys-> select Enter ->
mount --make-private --rbind /run  /mnt/run-> select Enter ->
cd /mnt-> select Enter ->
chroot /mnt /bin/bash --login-> select Enter ->
mount -a -> select Enter ->
apt update-> select Enter ->
apt remove --purge nvidia* libnvidia*-> select Enter ->
apt install nvidia-driver-470-> select Enter ->
exit-> select Enter ->
reboot-> select Enter ->
remote Live USB media -> select Enter ->
Ubuntu boots to black screen.

---

### Post by kotgc on 2024-01-12
Full output:
```
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# mount /dev/sda2 /mnt/
root@ubuntu:~# ls /mnt/
bin  boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swapfile  sys  tmp  usr  var
root@ubuntu:~# ls /
bin  boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var
root@ubuntu:~# umount /mnt 
root@ubuntu:~# mount /dev/sda2 /mnt/
root@ubuntu:~# mount --make-private --rbind /dev/ /mnt/dev/
root@ubuntu:~# mount --make-private --rbind /proc/ /mnt/proc/
root@ubuntu:~# mount --make-private --rbind /sys/ /mnt/sys/
root@ubuntu:~# mount --make-private --rbind /run/ /mnt/run/
root@ubuntu:~# chroot /mnt/bin/bash --login
chroot: cannot change root directory to '/mnt/bin/bash': Not a directory
root@ubuntu:~# chroot /mnt /bin/bash --login
root@ubuntu:/# mount -a
root@ubuntu:/# apt update 
Running in chroot, ignoring command 'start'
Hit:1 http://au.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://au.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                      
Hit:3 http://au.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                                               
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                                                                  
Hit:5 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu jammy InRelease                                                     
Hit:6 https://apt.syncthing.net syncthing InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
30 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@ubuntu:/# apt remove --purge nvidia*
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'nvidia-cuda-toolkit-doc' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit-gcc' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-430' for glob 'nvidia*'
Note, selecting 'nvidia-headless-435' for glob 'nvidia*'
Note, selecting 'nvidia-headless-440' for glob 'nvidia*'
Note, selecting 'nvidia-headless-450' for glob 'nvidia*'
Note, selecting 'nvidia-headless-455' for glob 'nvidia*'
Note, selecting 'nvidia-headless-460' for glob 'nvidia*'
Note, selecting 'nvidia-headless-465' for glob 'nvidia*'
Note, selecting 'nvidia-headless-470' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-495' for glob 'nvidia*'
Note, selecting 'nvidia-headless-510' for glob 'nvidia*'
Note, selecting 'nvidia-headless-515' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-520' for glob 'nvidia*'
Note, selecting 'nvidia-headless-525' for glob 'nvidia*'
Note, selecting 'nvidia-headless-530' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535' for glob 'nvidia*'
Note, selecting 'nvidia-driver-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-primus-vk-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-driver-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-headless-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-utils' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-435' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-440' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-450' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-455' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-460' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-465' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-470' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-495' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-510' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-515' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-520' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-525' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-530' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-535' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-435' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-440' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-450' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-455' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-460' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-465' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-470' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-495' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-510' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-515' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-520' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-525' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-530' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535' for glob 'nvidia*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia*'
Note, selecting 'nvidia-driver-410' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418' for glob 'nvidia*'
Note, selecting 'nvidia-driver-430' for glob 'nvidia*'
Note, selecting 'nvidia-driver-435' for glob 'nvidia*'
Note, selecting 'nvidia-driver-440' for glob 'nvidia*'
Note, selecting 'nvidia-driver-450' for glob 'nvidia*'
Note, selecting 'nvidia-driver-455' for glob 'nvidia*'
Note, selecting 'nvidia-driver-460' for glob 'nvidia*'
Note, selecting 'nvidia-driver-465' for glob 'nvidia*'
Note, selecting 'nvidia-driver-470' for glob 'nvidia*'
Note, selecting 'nvidia-driver-495' for glob 'nvidia*'
Note, selecting 'nvidia-driver-510' for glob 'nvidia*'
Note, selecting 'nvidia-driver-515' for glob 'nvidia*'
Note, selecting 'nvidia-driver-520' for glob 'nvidia*'
Note, selecting 'nvidia-driver-525' for glob 'nvidia*'
Note, selecting 'nvidia-driver-530' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-utils-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-primus-vk-wrapper' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless' for glob 'nvidia*'
Note, selecting 'nvidia-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-utils-435' for glob 'nvidia*'
Note, selecting 'nvidia-utils-440' for glob 'nvidia*'
Note, selecting 'nvidia-utils-450' for glob 'nvidia*'
Note, selecting 'nvidia-utils-455' for glob 'nvidia*'
Note, selecting 'nvidia-utils-460' for glob 'nvidia*'
Note, selecting 'nvidia-utils-465' for glob 'nvidia*'
Note, selecting 'nvidia-utils-470' for glob 'nvidia*'
Note, selecting 'nvidia-utils-495' for glob 'nvidia*'
Note, selecting 'nvidia-utils-510' for glob 'nvidia*'
Note, selecting 'nvidia-utils-515' for glob 'nvidia*'
Note, selecting 'nvidia-utils-520' for glob 'nvidia*'
Note, selecting 'nvidia-utils-525' for glob 'nvidia*'
Note, selecting 'nvidia-utils-530' for glob 'nvidia*'
Note, selecting 'nvidia-utils-535' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-egl-wayland-common' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.146.02' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.146.02' for glob 'nvidia*'
Note, selecting 'nvidia-utils-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-390xx-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.54.03' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-430' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-435' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-440' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-450' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-455' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-460' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-465' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-470' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-495' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-390xx-smi' for glob 'nvidia*'
Note, selecting 'nvidia-prebuilt-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-510' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-515' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-520' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-525' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-530' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-535' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils' for glob 'nvidia*'
Note, selecting 'nvidia-driver-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-fs-modules' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-headless-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-390' for glob 'nvidia*'
Note, selecting 'nvidia-fs-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-headless-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-fs-prebuilt-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-460-server' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-435' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-440' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-450' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-455' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-460' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-465' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-470' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-495' for glob 'nvidia*'
Note, selecting 'nvidia-cudnn' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-510' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-515' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-520' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-525' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-530' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.113.01' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-450' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-460' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-470' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-510' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-515' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-525' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-535' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.113.01' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-450' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-460' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-470' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-510' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-515' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-525' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-535' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-utils-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.129.03' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-430' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-435' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-440' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-450' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-455' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-460' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-465' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-470' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-495' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-510' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-515' for glob 'nvidia*'
Note, selecting 'nvidia-headless-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-520' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-525' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-530' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.129.03' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.104.05' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.104.12' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.104.05' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.104.12' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.86.05' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.54.03' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-utils-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-driver-510-server' for glob 'nvidia*'
Package 'nvidia-egl-wayland-common' is not installed, so not removed
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-390' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-driver-410' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-legacy-390xx-opencl-icd' is not installed, so not removed
Package 'nvidia-legacy-390xx-smi' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.113.01' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.146.02' is not installed, so not removed
Package 'nvidia-firmware-535-535.104.12' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-compute-utils-430' is not installed, so not removed
Package 'nvidia-compute-utils-435' is not installed, so not removed
Package 'nvidia-compute-utils-440' is not installed, so not removed
Package 'nvidia-compute-utils-450' is not installed, so not removed
Package 'nvidia-compute-utils-455' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-dkms-430' is not installed, so not removed
Package 'nvidia-dkms-435' is not installed, so not removed
Package 'nvidia-dkms-440' is not installed, so not removed
Package 'nvidia-dkms-450' is not installed, so not removed
Package 'nvidia-dkms-455' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-driver-430' is not installed, so not removed
Package 'nvidia-driver-435' is not installed, so not removed
Package 'nvidia-driver-440' is not installed, so not removed
Package 'nvidia-driver-450' is not installed, so not removed
Package 'nvidia-driver-455' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-435' is not installed, so not removed
Package 'nvidia-headless-440' is not installed, so not removed
Package 'nvidia-headless-450' is not installed, so not removed
Package 'nvidia-headless-455' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-435' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450' is not installed, so not removed
Package 'nvidia-headless-no-dkms-455' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-common-430' is not installed, so not removed
Package 'nvidia-kernel-common-435' is not installed, so not removed
Package 'nvidia-kernel-common-440' is not installed, so not removed
Package 'nvidia-kernel-common-450' is not installed, so not removed
Package 'nvidia-kernel-common-455' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-kernel-source-430' is not installed, so not removed
Package 'nvidia-kernel-source-435' is not installed, so not removed
Package 'nvidia-kernel-source-440' is not installed, so not removed
Package 'nvidia-kernel-source-450' is not installed, so not removed
Package 'nvidia-kernel-source-455' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
Package 'nvidia-utils-430' is not installed, so not removed
Package 'nvidia-utils-435' is not installed, so not removed
Package 'nvidia-utils-440' is not installed, so not removed
Package 'nvidia-utils-450' is not installed, so not removed
Package 'nvidia-utils-455' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-cuda-toolkit-doc' is not installed, so not removed
Package 'nvidia-cuda-toolkit-gcc' is not installed, so not removed
Package 'nvidia-cudnn' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-primus-vk-common' is not installed, so not removed
Package 'nvidia-primus-vk-wrapper' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-418-server' is not installed, so not removed
Package 'nvidia-compute-utils-440-server' is not installed, so not removed
Package 'nvidia-compute-utils-450-server' is not installed, so not removed
Package 'nvidia-compute-utils-460' is not installed, so not removed
Package 'nvidia-compute-utils-460-server' is not installed, so not removed
Package 'nvidia-compute-utils-465' is not installed, so not removed
Package 'nvidia-compute-utils-470-server' is not installed, so not removed
Package 'nvidia-compute-utils-495' is not installed, so not removed
Package 'nvidia-compute-utils-510' is not installed, so not removed
Package 'nvidia-compute-utils-510-server' is not installed, so not removed
Package 'nvidia-compute-utils-515' is not installed, so not removed
Package 'nvidia-compute-utils-515-server' is not installed, so not removed
Package 'nvidia-compute-utils-520' is not installed, so not removed
Package 'nvidia-compute-utils-525' is not installed, so not removed
Package 'nvidia-compute-utils-525-server' is not installed, so not removed
Package 'nvidia-compute-utils-530' is not installed, so not removed
Package 'nvidia-compute-utils-535' is not installed, so not removed
Package 'nvidia-compute-utils-535-server' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-418-server' is not installed, so not removed
Package 'nvidia-dkms-440-server' is not installed, so not removed
Package 'nvidia-dkms-450-server' is not installed, so not removed
Package 'nvidia-dkms-460' is not installed, so not removed
Package 'nvidia-dkms-460-server' is not installed, so not removed
Package 'nvidia-dkms-465' is not installed, so not removed
Package 'nvidia-dkms-470-server' is not installed, so not removed
Package 'nvidia-dkms-495' is not installed, so not removed
Package 'nvidia-dkms-510' is not installed, so not removed
Package 'nvidia-dkms-510-server' is not installed, so not removed
Package 'nvidia-dkms-515' is not installed, so not removed
Package 'nvidia-dkms-515-open' is not installed, so not removed
Package 'nvidia-dkms-515-server' is not installed, so not removed
Package 'nvidia-dkms-520' is not installed, so not removed
Package 'nvidia-dkms-520-open' is not installed, so not removed
Package 'nvidia-dkms-525' is not installed, so not removed
Package 'nvidia-dkms-525-open' is not installed, so not removed
Package 'nvidia-dkms-525-server' is not installed, so not removed
Package 'nvidia-dkms-530' is not installed, so not removed
Package 'nvidia-dkms-530-open' is not installed, so not removed
Package 'nvidia-dkms-535' is not installed, so not removed
Package 'nvidia-dkms-535-open' is not installed, so not removed
Package 'nvidia-dkms-535-server' is not installed, so not removed
Package 'nvidia-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-418-server' is not installed, so not removed
Package 'nvidia-driver-440-server' is not installed, so not removed
Package 'nvidia-driver-450-server' is not installed, so not removed
Package 'nvidia-driver-460' is not installed, so not removed
Package 'nvidia-driver-460-server' is not installed, so not removed
Package 'nvidia-driver-465' is not installed, so not removed
Package 'nvidia-driver-470-server' is not installed, so not removed
Package 'nvidia-driver-495' is not installed, so not removed
Package 'nvidia-driver-510' is not installed, so not removed
Package 'nvidia-driver-510-server' is not installed, so not removed
Package 'nvidia-driver-515' is not installed, so not removed
Package 'nvidia-driver-515-open' is not installed, so not removed
Package 'nvidia-driver-515-server' is not installed, so not removed
Package 'nvidia-driver-520' is not installed, so not removed
Package 'nvidia-driver-520-open' is not installed, so not removed
Package 'nvidia-driver-525' is not installed, so not removed
Package 'nvidia-driver-525-open' is not installed, so not removed
Package 'nvidia-driver-525-server' is not installed, so not removed
Package 'nvidia-driver-530' is not installed, so not removed
Package 'nvidia-driver-530-open' is not installed, so not removed
Package 'nvidia-driver-535' is not installed, so not removed
Package 'nvidia-driver-535-open' is not installed, so not removed
Package 'nvidia-driver-535-server' is not installed, so not removed
Package 'nvidia-driver-535-server-open' is not installed, so not removed
Package 'nvidia-fabricmanager-515' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-515' is not installed, so not removed
Package 'nvidia-firmware-535-535.104.05' is not installed, so not removed
Package 'nvidia-firmware-535-535.113.01' is not installed, so not removed
Package 'nvidia-firmware-535-535.129.03' is not installed, so not removed
Package 'nvidia-firmware-535-535.146.02' is not installed, so not removed
Package 'nvidia-firmware-535-535.54.03' is not installed, so not removed
Package 'nvidia-firmware-535-535.86.05' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.104.05' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.104.12' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.129.03' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.54.03' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-418-server' is not installed, so not removed
Package 'nvidia-headless-440-server' is not installed, so not removed
Package 'nvidia-headless-450-server' is not installed, so not removed
Package 'nvidia-headless-460' is not installed, so not removed
Package 'nvidia-headless-460-server' is not installed, so not removed
Package 'nvidia-headless-465' is not installed, so not removed
Package 'nvidia-headless-470' is not installed, so not removed
Package 'nvidia-headless-470-server' is not installed, so not removed
Package 'nvidia-headless-495' is not installed, so not removed
Package 'nvidia-headless-510' is not installed, so not removed
Package 'nvidia-headless-510-server' is not installed, so not removed
Package 'nvidia-headless-515' is not installed, so not removed
Package 'nvidia-headless-515-open' is not installed, so not removed
Package 'nvidia-headless-515-server' is not installed, so not removed
Package 'nvidia-headless-520' is not installed, so not removed
Package 'nvidia-headless-520-open' is not installed, so not removed
Package 'nvidia-headless-525' is not installed, so not removed
Package 'nvidia-headless-525-open' is not installed, so not removed
Package 'nvidia-headless-525-server' is not installed, so not removed
Package 'nvidia-headless-530' is not installed, so not removed
Package 'nvidia-headless-530-open' is not installed, so not removed
Package 'nvidia-headless-535' is not installed, so not removed
Package 'nvidia-headless-535-open' is not installed, so not removed
Package 'nvidia-headless-535-server' is not installed, so not removed
Package 'nvidia-headless-535-server-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-495' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-common-418-server' is not installed, so not removed
Package 'nvidia-kernel-common-440-server' is not installed, so not removed
Package 'nvidia-kernel-common-450-server' is not installed, so not removed
Package 'nvidia-kernel-common-460' is not installed, so not removed
Package 'nvidia-kernel-common-460-server' is not installed, so not removed
Package 'nvidia-kernel-common-465' is not installed, so not removed
Package 'nvidia-kernel-common-470-server' is not installed, so not removed
Package 'nvidia-kernel-common-495' is not installed, so not removed
Package 'nvidia-kernel-common-510' is not installed, so not removed
Package 'nvidia-kernel-common-510-server' is not installed, so not removed
Package 'nvidia-kernel-common-515' is not installed, so not removed
Package 'nvidia-kernel-common-515-server' is not installed, so not removed
Package 'nvidia-kernel-common-520' is not installed, so not removed
Package 'nvidia-kernel-common-525' is not installed, so not removed
Package 'nvidia-kernel-common-525-server' is not installed, so not removed
Package 'nvidia-kernel-common-530' is not installed, so not removed
Package 'nvidia-kernel-common-535' is not installed, so not removed
Package 'nvidia-kernel-common-535-server' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-kernel-source-418-server' is not installed, so not removed
Package 'nvidia-kernel-source-440-server' is not installed, so not removed
Package 'nvidia-kernel-source-450-server' is not installed, so not removed
Package 'nvidia-kernel-source-460' is not installed, so not removed
Package 'nvidia-kernel-source-460-server' is not installed, so not removed
Package 'nvidia-kernel-source-465' is not installed, so not removed
Package 'nvidia-kernel-source-470-server' is not installed, so not removed
Package 'nvidia-kernel-source-495' is not installed, so not removed
Package 'nvidia-kernel-source-510' is not installed, so not removed
Package 'nvidia-kernel-source-510-server' is not installed, so not removed
Package 'nvidia-kernel-source-515' is not installed, so not removed
Package 'nvidia-kernel-source-515-open' is not installed, so not removed
Package 'nvidia-kernel-source-515-server' is not installed, so not removed
Package 'nvidia-kernel-source-520' is not installed, so not removed
Package 'nvidia-kernel-source-520-open' is not installed, so not removed
Package 'nvidia-kernel-source-525' is not installed, so not removed
Package 'nvidia-kernel-source-525-open' is not installed, so not removed
Package 'nvidia-kernel-source-525-server' is not installed, so not removed
Package 'nvidia-kernel-source-530' is not installed, so not removed
Package 'nvidia-kernel-source-530-open' is not installed, so not removed
Package 'nvidia-kernel-source-535' is not installed, so not removed
Package 'nvidia-kernel-source-535-open' is not installed, so not removed
Package 'nvidia-kernel-source-535-server' is not installed, so not removed
Package 'nvidia-kernel-source-535-server-open' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-utils-418-server' is not installed, so not removed
Package 'nvidia-utils-440-server' is not installed, so not removed
Package 'nvidia-utils-450-server' is not installed, so not removed
Package 'nvidia-utils-460' is not installed, so not removed
Package 'nvidia-utils-460-server' is not installed, so not removed
Package 'nvidia-utils-465' is not installed, so not removed
Package 'nvidia-utils-470-server' is not installed, so not removed
Package 'nvidia-utils-495' is not installed, so not removed
Package 'nvidia-utils-510' is not installed, so not removed
Package 'nvidia-utils-510-server' is not installed, so not removed
Package 'nvidia-utils-515' is not installed, so not removed
Package 'nvidia-utils-515-server' is not installed, so not removed
Package 'nvidia-utils-520' is not installed, so not removed
Package 'nvidia-utils-525' is not installed, so not removed
Package 'nvidia-utils-525-server' is not installed, so not removed
Package 'nvidia-utils-530' is not installed, so not removed
Package 'nvidia-utils-535' is not installed, so not removed
Package 'nvidia-utils-535-server' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-fabricmanager-450' is not installed, so not removed
Package 'nvidia-fabricmanager-460' is not installed, so not removed
Package 'nvidia-fabricmanager-470' is not installed, so not removed
Package 'nvidia-fabricmanager-510' is not installed, so not removed
Package 'nvidia-fabricmanager-525' is not installed, so not removed
Package 'nvidia-fabricmanager-535' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-450' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-460' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-470' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-510' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-525' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-535' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386 libgl1:i386
  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386 libnvidia-cfg1-470 libnvidia-common-470 libnvidia-compute-470:i386
  libnvidia-decode-470 libnvidia-decode-470:i386 libnvidia-egl-wayland1 libnvidia-encode-470 libnvidia-encode-470:i386 libnvidia-extra-470 libnvidia-fbc1-470 libnvidia-fbc1-470:i386 libnvidia-gl-470
  libnvidia-gl-470:i386 libnvidia-ifr1-470 libnvidia-ifr1-470:i386 libpciaccess0:i386 libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0
  libxshmfence1:i386 libxxf86vm1:i386 pkg-config screen-resolution-extra xserver-xorg-video-nvidia-470
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-compute-utils-470* nvidia-dkms-470* nvidia-driver-470* nvidia-kernel-common-470* nvidia-kernel-source-470* nvidia-prime* nvidia-settings* nvidia-utils-470*
0 upgraded, 0 newly installed, 8 to remove and 30 not upgraded.
After this operation, 93.1 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 220469 files and directories currently installed.)
Removing nvidia-driver-470 (470.223.02-0ubuntu0.22.04.1) ...
Removing nvidia-compute-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Running in chroot, ignoring command 'stop'
Removing nvidia-dkms-470 (470.223.02-0ubuntu0.22.04.1) ...
Removing all DKMS Modules
Done.
INFO:Disable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Removing nvidia-kernel-common-470 (470.223.02-0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
Running in chroot, ignoring command 'daemon-reload'
Removing nvidia-kernel-source-470 (470.223.02-0ubuntu0.22.04.1) ...
Removing nvidia-prime (0.8.17.1) ...
Removing nvidia-settings (510.47.03-0ubuntu1) ...
Removing nvidia-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.2.0-39-generic
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.5) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
(Reading database ... 219915 files and directories currently installed.)
Purging configuration files for nvidia-prime (0.8.17.1) ...
Purging configuration files for nvidia-compute-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Purging configuration files for nvidia-dkms-470 (470.223.02-0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-kernel-common-470 (470.223.02-0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
Running in chroot, ignoring command 'daemon-reload'
Running in chroot, ignoring command 'daemon-reload'
Purging configuration files for nvidia-settings (510.47.03-0ubuntu1) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.2.0-39-generic
root@ubuntu:/# apt install nvidia-driver-470
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  nvidia-compute-utils-470 nvidia-dkms-470 nvidia-kernel-common-470 nvidia-kernel-source-470 nvidia-prime nvidia-settings nvidia-utils-470
The following NEW packages will be installed:
  nvidia-compute-utils-470 nvidia-dkms-470 nvidia-driver-470 nvidia-kernel-common-470 nvidia-kernel-source-470 nvidia-prime nvidia-settings nvidia-utils-470
0 upgraded, 8 newly installed, 0 to remove and 30 not upgraded.
Need to get 45.0 MB of archives.
After this operation, 93.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 nvidia-compute-utils-470 amd64 470.223.02-0ubuntu0.22.04.1 [114 kB]
Get:2 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 nvidia-kernel-source-470 amd64 470.223.02-0ubuntu0.22.04.1 [25.7 MB]
Get:3 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 nvidia-kernel-common-470 amd64 470.223.02-0ubuntu0.22.04.1 [17.3 MB]                                                                     
Get:4 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 nvidia-dkms-470 amd64 470.223.02-0ubuntu0.22.04.1 [31.1 kB]                                                                              
Get:5 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 nvidia-utils-470 amd64 470.223.02-0ubuntu0.22.04.1 [408 kB]                                                                              
Get:6 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 nvidia-driver-470 amd64 470.223.02-0ubuntu0.22.04.1 [453 kB]                                                                             
Get:7 http://au.archive.ubuntu.com/ubuntu jammy/main amd64 nvidia-prime all 0.8.17.1 [9,956 B]                                                                                                                    
Get:8 http://au.archive.ubuntu.com/ubuntu jammy/main amd64 nvidia-settings amd64 510.47.03-0ubuntu1 [960 kB]                                                                                                      
Fetched 45.0 MB in 38s (1,189 kB/s)                                                                                                                                                                               
Selecting previously unselected package nvidia-compute-utils-470.
(Reading database ... 219914 files and directories currently installed.)
Preparing to unpack .../0-nvidia-compute-utils-470_470.223.02-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-compute-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Selecting previously unselected package nvidia-kernel-source-470.
Preparing to unpack .../1-nvidia-kernel-source-470_470.223.02-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-kernel-source-470 (470.223.02-0ubuntu0.22.04.1) ...
Selecting previously unselected package nvidia-kernel-common-470.
Preparing to unpack .../2-nvidia-kernel-common-470_470.223.02-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-kernel-common-470 (470.223.02-0ubuntu0.22.04.1) ...
Selecting previously unselected package nvidia-dkms-470.
Preparing to unpack .../3-nvidia-dkms-470_470.223.02-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-dkms-470 (470.223.02-0ubuntu0.22.04.1) ...
Selecting previously unselected package nvidia-utils-470.
Preparing to unpack .../4-nvidia-utils-470_470.223.02-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Selecting previously unselected package nvidia-driver-470.
Preparing to unpack .../5-nvidia-driver-470_470.223.02-0ubuntu0.22.04.1_amd64.deb ...
Unpacking nvidia-driver-470 (470.223.02-0ubuntu0.22.04.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../6-nvidia-prime_0.8.17.1_all.deb ...
Unpacking nvidia-prime (0.8.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../7-nvidia-settings_510.47.03-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (510.47.03-0ubuntu1) ...
Setting up nvidia-kernel-source-470 (470.223.02-0ubuntu0.22.04.1) ...
Setting up nvidia-prime (0.8.17.1) ...
Setting up nvidia-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Setting up nvidia-compute-utils-470 (470.223.02-0ubuntu0.22.04.1) ...
Warning: The home dir /nonexistent you specified can't be accessed: No such file or directory
Adding system user `nvidia-persistenced' (UID 129) ...
Adding new group `nvidia-persistenced' (GID 137) ...
Adding new user `nvidia-persistenced' (UID 129) with group `nvidia-persistenced' ...
Not creating home directory `/nonexistent'.
Setting up nvidia-kernel-common-470 (470.223.02-0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-6.2.0-26-generic
cat: /var/tmp/mkinitramfs_8xf0yb/lib/modules/6.2.0-26-generic/modules.builtin: No such file or directory
W: Can't find modules.builtin.modinfo (for locating built-in drivers' firmware, supported in Linux >=5.2)
depmod: WARNING: could not open modules.order at /var/tmp/mkinitramfs_8xf0yb/lib/modules/6.2.0-26-generic: No such file or directory
depmod: WARNING: could not open modules.builtin at /var/tmp/mkinitramfs_8xf0yb/lib/modules/6.2.0-26-generic: No such file or directory
Created symlink /etc/systemd/system/systemd-hibernate.service.requires/nvidia-hibernate.service &#8594; /lib/systemd/system/nvidia-hibernate.service.
Created symlink /etc/systemd/system/systemd-suspend.service.requires/nvidia-resume.service &#8594; /lib/systemd/system/nvidia-resume.service.
Created symlink /etc/systemd/system/systemd-hibernate.service.requires/nvidia-resume.service &#8594; /lib/systemd/system/nvidia-resume.service.
Created symlink /etc/systemd/system/systemd-suspend.service.requires/nvidia-suspend.service &#8594; /lib/systemd/system/nvidia-suspend.service.
Setting up nvidia-settings (510.47.03-0ubuntu1) ...
Setting up nvidia-dkms-470 (470.223.02-0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-6.2.0-26-generic
cat: /var/tmp/mkinitramfs_5ENtOE/lib/modules/6.2.0-26-generic/modules.builtin: No such file or directory
W: Can't find modules.builtin.modinfo (for locating built-in drivers' firmware, supported in Linux >=5.2)
depmod: WARNING: could not open modules.order at /var/tmp/mkinitramfs_5ENtOE/lib/modules/6.2.0-26-generic: No such file or directory
depmod: WARNING: could not open modules.builtin at /var/tmp/mkinitramfs_5ENtOE/lib/modules/6.2.0-26-generic: No such file or directory
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-470.223.02 DKMS files...
Building for 6.2.0-26-generic 6.2.0-39-generic
Building for architecture x86_64
Module build for kernel 6.2.0-26-generic was skipped since the
kernel headers for this kernel does not seem to be installed.
Building initial module for 6.2.0-39-generic
Secure Boot not enabled on this system.
Done.

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.2.0-39-generic/updates/dkms/

nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.2.0-39-generic/updates/dkms/

nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.2.0-39-generic/updates/dkms/

nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.2.0-39-generic/updates/dkms/

nvidia-peermem.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.2.0-39-generic/updates/dkms/

depmod...
Setting up nvidia-driver-470 (470.223.02-0ubuntu0.22.04.1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.5) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.2.0-39-generic
root@ubuntu:/# exit
logout
root@ubuntu:~# reboot

```

---

### Post by kotgc on 2024-01-12
Just tried in Live USB chroot, the additional command:
 update-initramfs -u
However, same issue.

---

### Post by kotgc on 2024-01-12
Boot -> hold Shift -> select e to edit -> change &#8216;quiet splash&#8217; to &#8216;nomodeset&#8217; -> Ctrl+x -> boots showing dmesg, but then boots to black screen.
Boot -> hold Shift -> select e to edit -> change &#8216;quiet splash&#8217;  to &#8216;---3&#8217; -> Ctrl+x -> boots showing dmesg, but then boots to  black screen.
Boot -> hold Shift -> select e to edit -> change &#8216;quiet splash&#8217;  to &#8216;acpi=off&#8217; -> Ctrl+x -> boots showing dmesg, but then boots to  black screen.

---

### Post by kotgc on 2024-01-12
Tried installing nvidia-driver-450, but still black screen.
Boot now shows dmesg error:
Failed to start NVIDIA persistence daemon. Then black screeen. 

Reinstalled via Live USB, the nvidia-driver-470, but still black screen and
Boot still shows dmesg error:
Failed to start NVIDIA persistence daemon. Then black screen.

---

### Post by kotgc on 2024-01-12
Logs here if they might help?
boot.log: [https://dpaste.com/EUB9D8LS3](https://dpaste.com/EUB9D8LS3)

casper.log: [https://dpaste.com/89E34CCJ4](https://dpaste.com/89E34CCJ4)

kern.log: [https://dpaste.com/GNRPHAGNH](https://dpaste.com/GNRPHAGNH)

syslog: [https://dpaste.com/G8UQ5Y725](https://dpaste.com/G8UQ5Y725)
or Xorg.0.log?
```
root@ubuntu:/var/log# ls
auth.log  boot.log  btmp  casper.log  cups  dmesg  gdm3  gpu-manager.log  installer  kern.log  lastlog  private  syslog  ubuntu-advantage.log  unattended-upgrades  wtmp  Xorg.0.log
root@ubuntu:/var/log# cat Xorg.0.log 
[    22.878] 
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[    22.878] Current Operating System: Linux ubuntu 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64
[    22.878] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash ---
[    22.878] xorg-server 2:21.1.4-2ubuntu1.7~22.04.1 (For technical support please see http://www.ubuntu.com/support) 
[    22.878] Current version of pixman: 0.40.0
[    22.878]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.878] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.878] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 12 08:25:22 2024
[    22.878] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.879] (==) No Layout section.  Using the first Screen section.
[    22.879] (==) No screen section available. Using defaults.
[    22.879] (**) |-->Screen "Default Screen Section" (0)
[    22.879] (**) |   |-->Monitor "<default monitor>"
[    22.879] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    22.879] (==) Automatically adding devices
[    22.879] (==) Automatically enabling devices
[    22.879] (==) Automatically adding GPU devices
[    22.879] (==) Automatically binding GPU devices
[    22.879] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    22.880] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.880]     Entry deleted from font path.
[    22.880] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.880]     Entry deleted from font path.
[    22.880] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.880]     Entry deleted from font path.
[    22.880] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.880]     Entry deleted from font path.
[    22.880] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.880]     Entry deleted from font path.
[    22.880] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    22.880] (==) ModulePath set to "/usr/lib/xorg/modules"
[    22.880] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.880] (II) Loader magic: 0x559326aab020
[    22.880] (II) Module ABI versions:
[    22.880]     X.Org ANSI C Emulation: 0.4
[    22.880]     X.Org Video Driver: 25.2
[    22.880]     X.Org XInput driver : 24.4
[    22.880]     X.Org Server Extension : 10.0
[    22.880] (++) using VT number 1

[    22.880] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    22.881] (II) xfree86: Adding drm device (/dev/dri/card0)
[    22.881] (II) Platform probe for /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[    22.882] (--) PCI:*(1@0:0:0) 10de:128b:1043:85e7 rev 161, Mem @ 0xaa000000/16777216, 0xa0000000/134217728, 0xa8000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/131072
[    22.882] (II) LoadModule: "glx"
[    22.882] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.927] (II) Module glx: vendor="X.Org Foundation"
[    22.927]     compiled for 1.21.1.4, module version = 1.0.0
[    22.927]     ABI class: X.Org Server Extension, version 10.0
[    23.040] (==) Matched modesetting as autoconfigured driver 0
[    23.040] (==) Matched fbdev as autoconfigured driver 1
[    23.040] (==) Matched vesa as autoconfigured driver 2
[    23.040] (==) Assigned the driver to the xf86ConfigLayout
[    23.040] (II) LoadModule: "modesetting"
[    23.040] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.048] (II) Module modesetting: vendor="X.Org Foundation"
[    23.048]     compiled for 1.21.1.4, module version = 1.21.1
[    23.048]     Module class: X.Org Video Driver
[    23.048]     ABI class: X.Org Video Driver, version 25.2
[    23.048] (II) LoadModule: "fbdev"
[    23.048] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.049] (II) Module fbdev: vendor="X.Org Foundation"
[    23.049]     compiled for 1.21.1.3, module version = 0.5.0
[    23.049]     Module class: X.Org Video Driver
[    23.049]     ABI class: X.Org Video Driver, version 25.2
[    23.049] (II) LoadModule: "vesa"
[    23.049] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.050] (II) Module vesa: vendor="X.Org Foundation"
[    23.050]     compiled for 1.21.1.3, module version = 2.5.0
[    23.050]     Module class: X.Org Video Driver
[    23.050]     ABI class: X.Org Video Driver, version 25.2
[    23.050] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.050] (II) FBDEV: driver for framebuffer: fbdev
[    23.050] (II) VESA: driver for VESA chipsets: vesa
[    23.050] (II) modeset(0): using drv /dev/dri/card0
[    23.050] (WW) Falling back to old probe method for fbdev
[    23.050] (II) Loading sub module "fbdevhw"
[    23.050] (II) LoadModule: "fbdevhw"
[    23.050] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.063] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.063]     compiled for 1.21.1.4, module version = 0.0.2
[    23.063]     ABI class: X.Org Video Driver, version 25.2
[    23.064] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.064] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    23.064] (==) modeset(0): RGB weight 888
[    23.064] (==) modeset(0): Default visual is TrueColor
[    23.064] (II) Loading sub module "glamoregl"
[    23.064] (II) LoadModule: "glamoregl"
[    23.064] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    23.095] (II) Module glamoregl: vendor="X.Org Foundation"
[    23.095]     compiled for 1.21.1.4, module version = 1.0.1
[    23.095]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.041] (II) modeset(0): glamor X acceleration enabled on NV106
[    27.041] (II) modeset(0): glamor initialized
[    27.041] (==) modeset(0): VariableRefresh: disabled
[    27.041] (==) modeset(0): AsyncFlipSecondaries: disabled
[    27.181] (II) modeset(0): Output DVI-D-1 has no monitor section
[    27.246] (II) modeset(0): Output HDMI-1 has no monitor section
[    27.256] (II) modeset(0): Output VGA-1 has no monitor section
[    27.323] (II) modeset(0): EDID for output DVI-D-1
[    27.323] (II) modeset(0): Manufacturer: AOC  Model: 2202  Serial#: 7995
[    27.323] (II) modeset(0): Year: 2020  Week: 28
[    27.323] (II) modeset(0): EDID Version: 1.3
[    27.323] (II) modeset(0): Digital Display Input
[    27.323] (II) modeset(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    27.323] (II) modeset(0): Gamma: 2.20
[    27.323] (II) modeset(0): DPMS capabilities: Off
[    27.323] (II) modeset(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.323] (II) modeset(0): First detailed timing is preferred mode
[    27.323] (II) modeset(0): redX: 0.656 redY: 0.334   greenX: 0.315 greenY: 0.616
[    27.323] (II) modeset(0): blueX: 0.149 blueY: 0.063   whiteX: 0.313 whiteY: 0.329
[    27.323] (II) modeset(0): Supported established timings:
[    27.323] (II) modeset(0): 720x400@70Hz
[    27.323] (II) modeset(0): 640x480@60Hz
[    27.323] (II) modeset(0): 640x480@67Hz
[    27.323] (II) modeset(0): 640x480@72Hz
[    27.323] (II) modeset(0): 640x480@75Hz
[    27.323] (II) modeset(0): 800x600@56Hz
[    27.323] (II) modeset(0): 800x600@60Hz
[    27.323] (II) modeset(0): 800x600@72Hz
[    27.323] (II) modeset(0): 800x600@75Hz
[    27.323] (II) modeset(0): 832x624@75Hz
[    27.323] (II) modeset(0): 1024x768@60Hz
[    27.323] (II) modeset(0): 1024x768@70Hz
[    27.323] (II) modeset(0): 1024x768@75Hz
[    27.323] (II) modeset(0): 1280x1024@75Hz
[    27.323] (II) modeset(0): Manufacturer's mask: 0
[    27.323] (II) modeset(0): Supported standard timings:
[    27.323] (II) modeset(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    27.323] (II) modeset(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    27.323] (II) modeset(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    27.323] (II) modeset(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.323] (II) modeset(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    27.323] (II) modeset(0): #5: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    27.323] (II) modeset(0): Supported detailed timing:
[    27.323] (II) modeset(0): clock: 148.5 MHz   Image Size:  476 x 268 mm
[    27.323] (II) modeset(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    27.323] (II) modeset(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    27.323] (II) modeset(0): Supported detailed timing:
[    27.323] (II) modeset(0): clock: 174.5 MHz   Image Size:  476 x 268 mm
[    27.323] (II) modeset(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    27.323] (II) modeset(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1119 v_border: 0
[    27.323] (II) modeset(0): Monitor name: 22B2W
[    27.323] (II) modeset(0): Ranges: V min: 48 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 185 MHz
[    27.323] (II) modeset(0): Supported detailed timing:
[    27.323] (II) modeset(0): clock: 148.5 MHz   Image Size:  476 x 268 mm
[    27.323] (II) modeset(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    27.323] (II) modeset(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    27.323] (II) modeset(0): Supported detailed timing:
[    27.323] (II) modeset(0): clock: 74.2 MHz   Image Size:  476 x 268 mm
[    27.323] (II) modeset(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    27.323] (II) modeset(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    27.323] (II) modeset(0): Supported detailed timing:
[    27.323] (II) modeset(0): clock: 27.0 MHz   Image Size:  476 x 268 mm
[    27.323] (II) modeset(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    27.323] (II) modeset(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    27.323] (II) modeset(0): Supported detailed timing:
[    27.323] (II) modeset(0): clock: 27.0 MHz   Image Size:  476 x 268 mm
[    27.323] (II) modeset(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    27.323] (II) modeset(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    27.323] (II) modeset(0): Number of EDID sections to follow: 1
[    27.323] (II) modeset(0): EDID (in hex):
[    27.323] (II) modeset(0):     00ffffffffffff0005e302223b1f0000
[    27.323] (II) modeset(0):     1c1e010380301b782a2f55a855509d26
[    27.323] (II) modeset(0):     105054bfef00d1c0b300950081808140
[    27.323] (II) modeset(0):     81c001010101023a801871382d40582c
[    27.323] (II) modeset(0):     4500dc0c1100001e2a4480a070382740
[    27.323] (II) modeset(0):     30203500dc0c1100001a000000fc0032
[    27.323] (II) modeset(0):     324232570a20202020202020000000fd
[    27.323] (II) modeset(0):     00304b1e5512000a2020202020200143
[    27.323] (II) modeset(0):     02031ef14b101f051404130312021101
[    27.323] (II) modeset(0):     230907078301000065030c001000023a
[    27.323] (II) modeset(0):     801871382d40582c4500dc0c1100001e
[    27.323] (II) modeset(0):     011d007251d01e206e285500dc0c1100
[    27.323] (II) modeset(0):     001e8c0ad08a20e02d10103e9600dc0c
[    27.323] (II) modeset(0):     110000188c0ad090204031200c405500
[    27.323] (II) modeset(0):     dc0c1100001800000000000000000000
[    27.323] (II) modeset(0):     000000000000000000000000000000a1
[    27.323] (II) modeset(0): Printing probed modes for output DVI-D-1
[    27.323] (II) modeset(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    27.323] (II) modeset(0): Modeline "1920x1080"x75.0  174.50  1920 1968 2000 2080  1080 1083 1088 1119 +hsync -vsync (83.9 kHz e)
[    27.323] (II) modeset(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    27.323] (II) modeset(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    27.323] (II) modeset(0): Modeline "1920x1080"x60.0  138.65  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz d)
[    27.323] (II) modeset(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    27.323] (II) modeset(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    27.323] (II) modeset(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    27.323] (II) modeset(0): Modeline "1680x1050"x60.0  119.23  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.8 kHz d)
[    27.323] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    27.323] (II) modeset(0): Modeline "1400x1050"x60.0  122.05  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    27.323] (II) modeset(0): Modeline "1600x900"x60.0   97.78  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.6 kHz d)
[    27.323] (II) modeset(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    27.323] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    27.323] (II) modeset(0): Modeline "1280x1024"x60.0  107.96  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    27.323] (II) modeset(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    27.323] (II) modeset(0): Modeline "1400x900"x60.0   86.67  1400 1448 1480 1560  900 903 913 926 +hsync -vsync (55.6 kHz d)
[    27.323] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    27.323] (II) modeset(0): Modeline "1440x810"x60.0  151.94  1440 1464 1480 1520  810 811 814 833 doublescan +hsync -vsync (100.0 kHz d)
[    27.323] (II) modeset(0): Modeline "1368x768"x60.0   72.43  1368 1416 1448 1528  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    27.323] (II) modeset(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.4 kHz d)
[    27.323] (II) modeset(0): Modeline "1152x864"x60.0   86.40  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (54.0 kHz d)
[    27.323] (II) modeset(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    27.323] (II) modeset(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    27.323] (II) modeset(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    27.323] (II) modeset(0): Modeline "1280x720"x60.0   64.02  1280 1328 1360 1440  720 723 728 741 +hsync -vsync (44.5 kHz d)
[    27.323] (II) modeset(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    27.323] (II) modeset(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    27.323] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    27.323] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    27.323] (II) modeset(0): Modeline "960x720"x60.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    27.323] (II) modeset(0): Modeline "928x696"x60.0  109.06  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.3 kHz d)
[    27.323] (II) modeset(0): Modeline "896x672"x60.0  102.38  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.6 kHz d)
[    27.323] (II) modeset(0): Modeline "1024x576"x60.0   42.13  1024 1072 1104 1184  576 579 584 593 +hsync -vsync (35.6 kHz d)
[    27.323] (II) modeset(0): Modeline "960x600"x60.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    27.323] (II) modeset(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    27.323] (II) modeset(0): Modeline "832x624"x60.0   46.10  832 864 928 1152  624 625 628 667 -hsync -vsync (40.0 kHz d)
[    27.323] (II) modeset(0): Modeline "960x540"x60.0   37.36  960 1008 1040 1120  540 543 548 556 +hsync -vsync (33.4 kHz d)
[    27.323] (II) modeset(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    27.323] (II) modeset(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    27.323] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    27.323] (II) modeset(0): Modeline "800x600"x60.0   38.40  800 824 896 1024  600 601 603 625 +hsync +vsync (37.5 kHz d)
[    27.323] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    27.323] (II) modeset(0): Modeline "840x525"x60.0   59.62  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.8 kHz d)
[    27.323] (II) modeset(0): Modeline "864x486"x60.0   30.72  864 912 944 1024  486 489 494 500 +hsync -vsync (30.0 kHz d)
[    27.323] (II) modeset(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    27.323] (II) modeset(0): Modeline "700x525"x60.0   61.02  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    27.323] (II) modeset(0): Modeline "800x450"x60.0   48.89  800 824 840 880  450 451 454 463 doublescan +hsync -vsync (55.6 kHz d)
[    27.323] (II) modeset(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    27.323] (II) modeset(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    27.323] (II) modeset(0): Modeline "640x512"x60.0   53.98  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    27.323] (II) modeset(0): Modeline "700x450"x60.0   43.34  700 724 740 780  450 451 456 463 doublescan +hsync -vsync (55.6 kHz d)
[    27.323] (II) modeset(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    27.323] (II) modeset(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    27.323] (II) modeset(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    27.323] (II) modeset(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.323] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.323] (II) modeset(0): Modeline "720x405"x60.0   22.12  720 768 800 880  405 408 413 419 +hsync -vsync (25.1 kHz d)
[    27.323] (II) modeset(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    27.323] (II) modeset(0): Modeline "684x384"x60.0   36.21  684 708 724 764  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    27.323] (II) modeset(0): Modeline "576x432"x60.0   43.20  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (54.0 kHz d)
[    27.323] (II) modeset(0): Modeline "640x360"x60.0   17.95  640 688 720 800  360 363 368 374 +hsync -vsync (22.4 kHz d)
[    27.323] (II) modeset(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    27.323] (II) modeset(0): Modeline "512x288"x60.0   21.03  512 536 552 592  288 289 292 296 doublescan +hsync -vsync (35.5 kHz d)
[    27.323] (II) modeset(0): Modeline "416x312"x60.0   23.02  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (40.0 kHz d)
[    27.323] (II) modeset(0): Modeline "480x270"x60.0   18.68  480 504 520 560  270 271 274 278 doublescan +hsync -vsync (33.4 kHz d)
[    27.323] (II) modeset(0): Modeline "400x300"x60.0   19.17  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (37.4 kHz d)
[    27.323] (II) modeset(0): Modeline "432x243"x60.0   15.36  432 456 472 512  243 244 247 250 doublescan +hsync -vsync (30.0 kHz d)
[    27.323] (II) modeset(0): Modeline "320x240"x60.0   12.58  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.4 kHz d)
[    27.323] (II) modeset(0): Modeline "360x202"x60.0   11.04  360 384 400 440  202 204 206 209 doublescan +hsync -vsync (25.1 kHz d)
[    27.323] (II) modeset(0): Modeline "320x180"x60.0    8.98  320 344 360 400  180 181 184 187 doublescan +hsync -vsync (22.4 kHz d)
[    27.388] (II) modeset(0): EDID for output HDMI-1
[    27.388] (II) modeset(0): Manufacturer: AOC  Model: 2202  Serial#: 8005
[    27.388] (II) modeset(0): Year: 2020  Week: 28
[    27.388] (II) modeset(0): EDID Version: 1.3
[    27.388] (II) modeset(0): Digital Display Input
[    27.388] (II) modeset(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    27.388] (II) modeset(0): Gamma: 2.20
[    27.388] (II) modeset(0): DPMS capabilities: Off
[    27.388] (II) modeset(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.388] (II) modeset(0): First detailed timing is preferred mode
[    27.388] (II) modeset(0): redX: 0.656 redY: 0.334   greenX: 0.315 greenY: 0.616
[    27.388] (II) modeset(0): blueX: 0.149 blueY: 0.063   whiteX: 0.313 whiteY: 0.329
[    27.388] (II) modeset(0): Supported established timings:
[    27.388] (II) modeset(0): 720x400@70Hz
[    27.388] (II) modeset(0): 640x480@60Hz
[    27.388] (II) modeset(0): 640x480@67Hz
[    27.388] (II) modeset(0): 640x480@72Hz
[    27.388] (II) modeset(0): 640x480@75Hz
[    27.388] (II) modeset(0): 800x600@56Hz
[    27.388] (II) modeset(0): 800x600@60Hz
[    27.388] (II) modeset(0): 800x600@72Hz
[    27.389] (II) modeset(0): 800x600@75Hz
[    27.389] (II) modeset(0): 832x624@75Hz
[    27.389] (II) modeset(0): 1024x768@60Hz
[    27.389] (II) modeset(0): 1024x768@70Hz
[    27.389] (II) modeset(0): 1024x768@75Hz
[    27.389] (II) modeset(0): 1280x1024@75Hz
[    27.389] (II) modeset(0): Manufacturer's mask: 0
[    27.389] (II) modeset(0): Supported standard timings:
[    27.389] (II) modeset(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    27.389] (II) modeset(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    27.389] (II) modeset(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    27.389] (II) modeset(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.389] (II) modeset(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    27.389] (II) modeset(0): #5: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    27.389] (II) modeset(0): Supported detailed timing:
[    27.389] (II) modeset(0): clock: 148.5 MHz   Image Size:  476 x 268 mm
[    27.389] (II) modeset(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    27.389] (II) modeset(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    27.389] (II) modeset(0): Supported detailed timing:
[    27.389] (II) modeset(0): clock: 174.5 MHz   Image Size:  476 x 268 mm
[    27.389] (II) modeset(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    27.389] (II) modeset(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1119 v_border: 0
[    27.389] (II) modeset(0): Monitor name: 22B2W
[    27.389] (II) modeset(0): Ranges: V min: 48 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 185 MHz
[    27.389] (II) modeset(0): Supported detailed timing:
[    27.389] (II) modeset(0): clock: 148.5 MHz   Image Size:  476 x 268 mm
[    27.389] (II) modeset(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    27.389] (II) modeset(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    27.389] (II) modeset(0): Supported detailed timing:
[    27.389] (II) modeset(0): clock: 74.2 MHz   Image Size:  476 x 268 mm
[    27.389] (II) modeset(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    27.389] (II) modeset(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    27.389] (II) modeset(0): Supported detailed timing:
[    27.389] (II) modeset(0): clock: 27.0 MHz   Image Size:  476 x 268 mm
[    27.389] (II) modeset(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    27.389] (II) modeset(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    27.389] (II) modeset(0): Supported detailed timing:
[    27.389] (II) modeset(0): clock: 27.0 MHz   Image Size:  476 x 268 mm
[    27.389] (II) modeset(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    27.389] (II) modeset(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    27.389] (II) modeset(0): Number of EDID sections to follow: 1
[    27.389] (II) modeset(0): EDID (in hex):
[    27.389] (II) modeset(0):     00ffffffffffff0005e30222451f0000
[    27.389] (II) modeset(0):     1c1e010380301b782a2f55a855509d26
[    27.389] (II) modeset(0):     105054bfef00d1c0b300950081808140
[    27.389] (II) modeset(0):     81c001010101023a801871382d40582c
[    27.389] (II) modeset(0):     4500dc0c1100001e2a4480a070382740
[    27.389] (II) modeset(0):     30203500dc0c1100001a000000fc0032
[    27.389] (II) modeset(0):     324232570a20202020202020000000fd
[    27.389] (II) modeset(0):     00304b1e5512000a2020202020200139
[    27.389] (II) modeset(0):     02031ef14b101f051404130312021101
[    27.389] (II) modeset(0):     230907078301000065030c001000023a
[    27.389] (II) modeset(0):     801871382d40582c4500dc0c1100001e
[    27.389] (II) modeset(0):     011d007251d01e206e285500dc0c1100
[    27.389] (II) modeset(0):     001e8c0ad08a20e02d10103e9600dc0c
[    27.389] (II) modeset(0):     110000188c0ad090204031200c405500
[    27.389] (II) modeset(0):     dc0c1100001800000000000000000000
[    27.389] (II) modeset(0):     000000000000000000000000000000a1
[    27.389] (II) modeset(0): Printing probed modes for output HDMI-1
[    27.389] (II) modeset(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    27.389] (II) modeset(0): Modeline "1920x1080"x75.0  174.50  1920 1968 2000 2080  1080 1083 1088 1119 +hsync -vsync (83.9 kHz e)
[    27.389] (II) modeset(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    27.389] (II) modeset(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    27.389] (II) modeset(0): Modeline "1920x1080"x60.0  138.65  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz d)
[    27.389] (II) modeset(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    27.389] (II) modeset(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    27.389] (II) modeset(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    27.389] (II) modeset(0): Modeline "1680x1050"x60.0  119.23  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.8 kHz d)
[    27.389] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    27.389] (II) modeset(0): Modeline "1400x1050"x60.0  122.05  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    27.389] (II) modeset(0): Modeline "1600x900"x60.0   97.78  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.6 kHz d)
[    27.389] (II) modeset(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    27.389] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    27.389] (II) modeset(0): Modeline "1280x1024"x60.0  107.96  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    27.389] (II) modeset(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    27.389] (II) modeset(0): Modeline "1400x900"x60.0   86.67  1400 1448 1480 1560  900 903 913 926 +hsync -vsync (55.6 kHz d)
[    27.389] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    27.389] (II) modeset(0): Modeline "1440x810"x60.0  151.94  1440 1464 1480 1520  810 811 814 833 doublescan +hsync -vsync (100.0 kHz d)
[    27.389] (II) modeset(0): Modeline "1368x768"x60.0   72.43  1368 1416 1448 1528  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    27.389] (II) modeset(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.4 kHz d)
[    27.389] (II) modeset(0): Modeline "1152x864"x60.0   86.40  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (54.0 kHz d)
[    27.389] (II) modeset(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    27.389] (II) modeset(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    27.389] (II) modeset(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    27.389] (II) modeset(0): Modeline "1280x720"x60.0   64.02  1280 1328 1360 1440  720 723 728 741 +hsync -vsync (44.5 kHz d)
[    27.389] (II) modeset(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    27.389] (II) modeset(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    27.389] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    27.389] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    27.389] (II) modeset(0): Modeline "960x720"x60.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    27.389] (II) modeset(0): Modeline "928x696"x60.0  109.06  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.3 kHz d)
[    27.389] (II) modeset(0): Modeline "896x672"x60.0  102.38  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.6 kHz d)
[    27.389] (II) modeset(0): Modeline "1024x576"x60.0   42.13  1024 1072 1104 1184  576 579 584 593 +hsync -vsync (35.6 kHz d)
[    27.389] (II) modeset(0): Modeline "960x600"x60.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    27.389] (II) modeset(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    27.389] (II) modeset(0): Modeline "832x624"x60.0   46.10  832 864 928 1152  624 625 628 667 -hsync -vsync (40.0 kHz d)
[    27.389] (II) modeset(0): Modeline "960x540"x60.0   37.36  960 1008 1040 1120  540 543 548 556 +hsync -vsync (33.4 kHz d)
[    27.389] (II) modeset(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    27.389] (II) modeset(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    27.389] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    27.389] (II) modeset(0): Modeline "800x600"x60.0   38.40  800 824 896 1024  600 601 603 625 +hsync +vsync (37.5 kHz d)
[    27.389] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    27.389] (II) modeset(0): Modeline "840x525"x60.0   59.62  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.8 kHz d)
[    27.389] (II) modeset(0): Modeline "864x486"x60.0   30.72  864 912 944 1024  486 489 494 500 +hsync -vsync (30.0 kHz d)
[    27.389] (II) modeset(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    27.389] (II) modeset(0): Modeline "700x525"x60.0   61.02  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    27.389] (II) modeset(0): Modeline "800x450"x60.0   48.89  800 824 840 880  450 451 454 463 doublescan +hsync -vsync (55.6 kHz d)
[    27.389] (II) modeset(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    27.389] (II) modeset(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    27.389] (II) modeset(0): Modeline "640x512"x60.0   53.98  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    27.389] (II) modeset(0): Modeline "700x450"x60.0   43.34  700 724 740 780  450 451 456 463 doublescan +hsync -vsync (55.6 kHz d)
[    27.389] (II) modeset(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    27.389] (II) modeset(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    27.389] (II) modeset(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    27.389] (II) modeset(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.389] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.389] (II) modeset(0): Modeline "720x405"x60.0   22.12  720 768 800 880  405 408 413 419 +hsync -vsync (25.1 kHz d)
[    27.389] (II) modeset(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    27.389] (II) modeset(0): Modeline "684x384"x60.0   36.21  684 708 724 764  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    27.389] (II) modeset(0): Modeline "576x432"x60.0   43.20  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (54.0 kHz d)
[    27.389] (II) modeset(0): Modeline "640x360"x60.0   17.95  640 688 720 800  360 363 368 374 +hsync -vsync (22.4 kHz d)
[    27.389] (II) modeset(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    27.389] (II) modeset(0): Modeline "512x288"x60.0   21.03  512 536 552 592  288 289 292 296 doublescan +hsync -vsync (35.5 kHz d)
[    27.389] (II) modeset(0): Modeline "416x312"x60.0   23.02  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (40.0 kHz d)
[    27.389] (II) modeset(0): Modeline "480x270"x60.0   18.68  480 504 520 560  270 271 274 278 doublescan +hsync -vsync (33.4 kHz d)
[    27.389] (II) modeset(0): Modeline "400x300"x60.0   19.17  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (37.4 kHz d)
[    27.389] (II) modeset(0): Modeline "432x243"x60.0   15.36  432 456 472 512  243 244 247 250 doublescan +hsync -vsync (30.0 kHz d)
[    27.389] (II) modeset(0): Modeline "320x240"x60.0   12.58  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.4 kHz d)
[    27.389] (II) modeset(0): Modeline "360x202"x60.0   11.04  360 384 400 440  202 204 206 209 doublescan +hsync -vsync (25.1 kHz d)
[    27.389] (II) modeset(0): Modeline "320x180"x60.0    8.98  320 344 360 400  180 181 184 187 doublescan +hsync -vsync (22.4 kHz d)
[    27.400] (II) modeset(0): EDID for output VGA-1
[    27.400] (II) modeset(0): Output DVI-D-1 connected
[    27.400] (II) modeset(0): Output HDMI-1 connected
[    27.400] (II) modeset(0): Output VGA-1 disconnected
[    27.400] (II) modeset(0): Using spanning desktop for initial modes
[    27.400] (II) modeset(0): Output DVI-D-1 using initial mode 1920x1080 +0+0
[    27.400] (II) modeset(0): Output HDMI-1 using initial mode 1920x1080 +1920+0
[    27.400] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.400] (==) modeset(0): DPI set to (96, 96)
[    27.400] (II) Loading sub module "fb"
[    27.400] (II) LoadModule: "fb"
[    27.400] (II) Module "fb" already built-in
[    27.400] (II) UnloadModule: "fbdev"
[    27.400] (II) Unloading fbdev
[    27.400] (II) UnloadSubModule: "fbdevhw"
[    27.400] (II) Unloading fbdevhw
[    27.400] (II) UnloadModule: "vesa"
[    27.400] (II) Unloading vesa
[    27.607] (==) modeset(0): Backing store enabled
[    27.607] (==) modeset(0): Silken mouse enabled
[    27.639] (II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
[    27.639] (==) modeset(0): DPMS enabled
[    27.639] (II) modeset(0): [DRI2] Setup complete
[    27.639] (II) modeset(0): [DRI2]   DRI driver: nouveau
[    27.639] (II) modeset(0): [DRI2]   VDPAU driver: nouveau
[    27.639] (II) Initializing extension Generic Event Extension
[    27.639] (II) Initializing extension SHAPE
[    27.639] (II) Initializing extension MIT-SHM
[    27.639] (II) Initializing extension XInputExtension
[    27.639] (II) Initializing extension XTEST
[    27.640] (II) Initializing extension BIG-REQUESTS
[    27.640] (II) Initializing extension SYNC
[    27.640] (II) Initializing extension XKEYBOARD
[    27.640] (II) Initializing extension XC-MISC
[    27.640] (II) Initializing extension SECURITY
[    27.640] (II) Initializing extension XFIXES
[    27.640] (II) Initializing extension RENDER
[    27.640] (II) Initializing extension RANDR
[    27.640] (II) Initializing extension COMPOSITE
[    27.641] (II) Initializing extension DAMAGE
[    27.641] (II) Initializing extension MIT-SCREEN-SAVER
[    27.641] (II) Initializing extension DOUBLE-BUFFER
[    27.641] (II) Initializing extension RECORD
[    27.641] (II) Initializing extension DPMS
[    27.641] (II) Initializing extension Present
[    27.641] (II) Initializing extension DRI3
[    27.641] (II) Initializing extension X-Resource
[    27.641] (II) Initializing extension XVideo
[    27.641] (II) Initializing extension XVideo-MotionCompensation
[    27.641] (II) Initializing extension SELinux
[    27.641] (II) SELinux: Disabled on system
[    27.641] (II) Initializing extension GLX
[    27.648] (II) AIGLX: Loaded and initialized nouveau
[    27.648] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.648] (II) Initializing extension XFree86-VidModeExtension
[    27.648] (II) Initializing extension XFree86-DGA
[    27.648] (II) Initializing extension XFree86-DRI
[    27.648] (II) Initializing extension DRI2
[    27.648] (II) modeset(0): Damage tracking initialized
[    27.648] (II) modeset(0): Setting screen physical size to 1016 x 285
[    27.825] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.825] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    27.825] (II) LoadModule: "libinput"
[    27.825] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    27.868] (II) Module libinput: vendor="X.Org Foundation"
[    27.868]     compiled for 1.20.14, module version = 1.2.1
[    27.868]     Module class: X.Org XInput Driver
[    27.868]     ABI class: X.Org XInput driver, version 24.1
[    27.868] (II) Using input driver 'libinput' for 'Power Button'
[    27.868] (**) Power Button: always reports core events
[    27.868] (**) Option "Device" "/dev/input/event2"
[    27.892] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    27.892] (II) event2  - Power Button: device is a keyboard
[    27.892] (II) event2  - Power Button: device removed
[    27.917] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    27.917] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.917] (**) Option "xkb_model" "pc105"
[    27.917] (**) Option "xkb_layout" "us"
[    27.918] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    27.918] (II) event2  - Power Button: device is a keyboard
[    27.918] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.918] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    27.918] (II) Using input driver 'libinput' for 'Power Button'
[    27.918] (**) Power Button: always reports core events
[    27.918] (**) Option "Device" "/dev/input/event1"
[    27.919] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    27.919] (II) event1  - Power Button: device is a keyboard
[    27.919] (II) event1  - Power Button: device removed
[    27.949] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    27.949] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    27.949] (**) Option "xkb_model" "pc105"
[    27.949] (**) Option "xkb_layout" "us"
[    27.950] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    27.950] (II) event1  - Power Button: device is a keyboard
[    27.950] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    27.950] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    27.950] (II) Using input driver 'libinput' for 'Sleep Button'
[    27.950] (**) Sleep Button: always reports core events
[    27.950] (**) Option "Device" "/dev/input/event0"
[    27.951] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[    27.951] (II) event0  - Sleep Button: device is a keyboard
[    27.951] (II) event0  - Sleep Button: device removed
[    27.981] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    27.981] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    27.981] (**) Option "xkb_model" "pc105"
[    27.981] (**) Option "xkb_layout" "us"
[    27.982] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[    27.982] (II) event0  - Sleep Button: device is a keyboard
[    27.982] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[    27.982] (II) No input driver specified, ignoring this device.
[    27.982] (II) This device may have been added with another device file.
[    27.983] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event8)
[    27.983] (II) No input driver specified, ignoring this device.
[    27.983] (II) This device may have been added with another device file.
[    27.983] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event9)
[    27.983] (II) No input driver specified, ignoring this device.
[    27.983] (II) This device may have been added with another device file.
[    27.983] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    27.983] (II) No input driver specified, ignoring this device.
[    27.983] (II) This device may have been added with another device file.
[    27.984] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    27.984] (**)   USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    27.984] (II) Using input driver 'libinput' for '  USB Keyboard'
[    27.984] (**)   USB Keyboard: always reports core events
[    27.984] (**) Option "Device" "/dev/input/event3"
[    27.985] (II) event3  -   USB Keyboard: is tagged by udev as: Keyboard
[    27.985] (II) event3  -   USB Keyboard: device is a keyboard
[    27.985] (II) event3  -   USB Keyboard: device removed
[    28.005] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04D9:1503.0001/input/input3/event3"
[    28.005] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 9)
[    28.005] (**) Option "xkb_model" "pc105"
[    28.005] (**) Option "xkb_layout" "us"
[    28.006] (II) event3  -   USB Keyboard: is tagged by udev as: Keyboard
[    28.007] (II) event3  -   USB Keyboard: device is a keyboard
[    28.007] (II) config/udev: Adding input device   USB Keyboard System Control (/dev/input/event4)
[    28.007] (**)   USB Keyboard System Control: Applying InputClass "libinput keyboard catchall"
[    28.007] (II) Using input driver 'libinput' for '  USB Keyboard System Control'
[    28.007] (**)   USB Keyboard System Control: always reports core events
[    28.007] (**) Option "Device" "/dev/input/event4"
[    28.008] (II) event4  -   USB Keyboard System Control: is tagged by udev as: Keyboard
[    28.008] (II) event4  -   USB Keyboard System Control: device is a keyboard
[    28.009] (II) event4  -   USB Keyboard System Control: device removed
[    28.033] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input4/event4"
[    28.033] (II) XINPUT: Adding extended input device "  USB Keyboard System Control" (type: KEYBOARD, id 10)
[    28.033] (**) Option "xkb_model" "pc105"
[    28.033] (**) Option "xkb_layout" "us"
[    28.034] (II) event4  -   USB Keyboard System Control: is tagged by udev as: Keyboard
[    28.035] (II) event4  -   USB Keyboard System Control: device is a keyboard
[    28.035] (II) config/udev: Adding input device   USB Keyboard Consumer Control (/dev/input/event5)
[    28.035] (**)   USB Keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    28.035] (II) Using input driver 'libinput' for '  USB Keyboard Consumer Control'
[    28.035] (**)   USB Keyboard Consumer Control: always reports core events
[    28.035] (**) Option "Device" "/dev/input/event5"
[    28.036] (II) event5  -   USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    28.036] (II) event5  -   USB Keyboard Consumer Control: device is a keyboard
[    28.037] (II) event5  -   USB Keyboard Consumer Control: device removed
[    28.063] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input5/event5"
[    28.063] (II) XINPUT: Adding extended input device "  USB Keyboard Consumer Control" (type: KEYBOARD, id 11)
[    28.063] (**) Option "xkb_model" "pc105"
[    28.063] (**) Option "xkb_layout" "us"
[    28.064] (II) event5  -   USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    28.064] (II) event5  -   USB Keyboard Consumer Control: device is a keyboard
[    28.065] (II) config/udev: Adding input device Logitech Wireless Mouse M560 (/dev/input/event6)
[    28.065] (**) Logitech Wireless Mouse M560: Applying InputClass "libinput pointer catchall"
[    28.065] (II) Using input driver 'libinput' for 'Logitech Wireless Mouse M560'
[    28.065] (**) Logitech Wireless Mouse M560: always reports core events
[    28.065] (**) Option "Device" "/dev/input/event6"
[    28.066] (II) event6  - Logitech Wireless Mouse M560: is tagged by udev as: Mouse
[    28.066] (II) event6  - Logitech Wireless Mouse M560: device is a pointer
[    28.066] (II) event6  - Logitech Wireless Mouse M560: device removed
[    28.129] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input16/event6"
[    28.129] (II) XINPUT: Adding extended input device "Logitech Wireless Mouse M560" (type: MOUSE, id 12)
[    28.129] (**) Option "AccelerationScheme" "none"
[    28.129] (**) Logitech Wireless Mouse M560: (accel) selected scheme none/0
[    28.129] (**) Logitech Wireless Mouse M560: (accel) acceleration factor: 2.000
[    28.129] (**) Logitech Wireless Mouse M560: (accel) acceleration threshold: 4
[    28.130] (II) event6  - Logitech Wireless Mouse M560: is tagged by udev as: Mouse
[    28.130] (II) event6  - Logitech Wireless Mouse M560: device is a pointer
[    28.131] (II) config/udev: Adding input device Logitech Wireless Mouse M560 (/dev/input/mouse0)
[    28.131] (II) No input driver specified, ignoring this device.
[    28.131] (II) This device may have been added with another device file.
[    28.131] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event11)
[    28.131] (II) No input driver specified, ignoring this device.
[    28.131] (II) This device may have been added with another device file.
[    28.131] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event12)
[    28.131] (II) No input driver specified, ignoring this device.
[    28.131] (II) This device may have been added with another device file.
[    28.131] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event13)
[    28.131] (II) No input driver specified, ignoring this device.
[    28.131] (II) This device may have been added with another device file.
[    28.131] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event14)
[    28.131] (II) No input driver specified, ignoring this device.
[    28.131] (II) This device may have been added with another device file.
[    28.132] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event15)
[    28.132] (II) No input driver specified, ignoring this device.
[    28.132] (II) This device may have been added with another device file.
[    34.292] (II) modeset(0): EDID vendor "AOC", prod id 8706
[    34.292] (II) modeset(0): Using EDID range info for horizontal sync
[    34.292] (II) modeset(0): Using EDID range info for vertical refresh
[    34.292] (II) modeset(0): Printing DDC gathered Modelines:
[    34.292] (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    34.292] (II) modeset(0): Modeline "1920x1080"x0.0  174.50  1920 1968 2000 2080  1080 1083 1088 1119 +hsync -vsync (83.9 kHz e)
[    34.292] (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    34.292] (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    34.292] (II) modeset(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    34.292] (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    34.292] (II) modeset(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    34.292] (II) modeset(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    34.292] (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    34.292] (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    34.292] (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    34.292] (II) modeset(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    34.292] (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    34.292] (II) modeset(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    34.292] (II) modeset(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    34.292] (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    34.292] (II) modeset(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    34.292] (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    34.292] (II) modeset(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    34.292] (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    34.292] (II) modeset(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    34.292] (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    34.292] (II) modeset(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    34.292] (II) modeset(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    34.292] (II) modeset(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    34.292] (II) modeset(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    34.292] (II) modeset(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    55.955] (II) config/udev: Adding input device Logitech Wireless Mouse M560 (/dev/input/mouse0)
[    55.955] (II) No input driver specified, ignoring this device.
[    55.955] (II) This device may have been added with another device file.
[    55.972] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event15)
[    55.972] (II) No input driver specified, ignoring this device.
[    55.972] (II) This device may have been added with another device file.
[    55.972] (II) config/udev: removing device Power Button
[    55.972] (II) event2  - Power Button: device removed
[    55.997] (II) UnloadModule: "libinput"
[    55.998] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    55.998] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    55.998] (II) Using input driver 'libinput' for 'Power Button'
[    55.998] (**) Power Button: always reports core events
[    55.998] (**) Option "Device" "/dev/input/event2"
[    55.998] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    55.998] (II) event2  - Power Button: device is a keyboard
[    55.998] (II) event2  - Power Button: device removed
[    56.021] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    56.021] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    56.021] (**) Option "xkb_model" "pc105"
[    56.021] (**) Option "xkb_layout" "us"
[    56.021] (WW) Option "xkb_variant" requires a string value
[    56.021] (WW) Option "xkb_options" requires a string value
[    56.022] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    56.022] (II) event2  - Power Button: device is a keyboard
[    56.022] (II) config/udev: removing device   USB Keyboard Consumer Control
[    56.022] (II) event5  -   USB Keyboard Consumer Control: device removed
[    56.057] (II) UnloadModule: "libinput"
[    56.058] (II) config/udev: Adding input device   USB Keyboard Consumer Control (/dev/input/event5)
[    56.058] (**)   USB Keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    56.058] (II) Using input driver 'libinput' for '  USB Keyboard Consumer Control'
[    56.058] (**)   USB Keyboard Consumer Control: always reports core events
[    56.058] (**) Option "Device" "/dev/input/event5"
[    56.058] (II) event5  -   USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    56.058] (II) event5  -   USB Keyboard Consumer Control: device is a keyboard
[    56.058] (II) event5  -   USB Keyboard Consumer Control: device removed
[    56.077] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input5/event5"
[    56.077] (II) XINPUT: Adding extended input device "  USB Keyboard Consumer Control" (type: KEYBOARD, id 11)
[    56.077] (**) Option "xkb_model" "pc105"
[    56.077] (**) Option "xkb_layout" "us"
[    56.077] (WW) Option "xkb_variant" requires a string value
[    56.077] (WW) Option "xkb_options" requires a string value
[    56.078] (II) event5  -   USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    56.078] (II) event5  -   USB Keyboard Consumer Control: device is a keyboard
[    56.079] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    56.079] (II) No input driver specified, ignoring this device.
[    56.079] (II) This device may have been added with another device file.
[    56.079] (II) config/udev: removing device   USB Keyboard
[    56.079] (II) event3  -   USB Keyboard: device removed
[    56.102] (II) UnloadModule: "libinput"
[    56.102] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    56.102] (**)   USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    56.102] (II) Using input driver 'libinput' for '  USB Keyboard'
[    56.102] (**)   USB Keyboard: always reports core events
[    56.102] (**) Option "Device" "/dev/input/event3"
[    56.103] (II) event3  -   USB Keyboard: is tagged by udev as: Keyboard
[    56.103] (II) event3  -   USB Keyboard: device is a keyboard
[    56.103] (II) event3  -   USB Keyboard: device removed
[    56.125] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04D9:1503.0001/input/input3/event3"
[    56.125] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 9)
[    56.125] (**) Option "xkb_model" "pc105"
[    56.125] (**) Option "xkb_layout" "us"
[    56.125] (WW) Option "xkb_variant" requires a string value
[    56.125] (WW) Option "xkb_options" requires a string value
[    56.126] (II) event3  -   USB Keyboard: is tagged by udev as: Keyboard
[    56.126] (II) event3  -   USB Keyboard: device is a keyboard
[    56.127] (II) config/udev: removing device Sleep Button
[    56.127] (II) event0  - Sleep Button: device removed
[    56.141] (II) UnloadModule: "libinput"
[    56.142] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    56.142] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    56.142] (II) Using input driver 'libinput' for 'Sleep Button'
[    56.142] (**) Sleep Button: always reports core events
[    56.142] (**) Option "Device" "/dev/input/event0"
[    56.142] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[    56.142] (II) event0  - Sleep Button: device is a keyboard
[    56.142] (II) event0  - Sleep Button: device removed
[    56.161] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    56.161] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    56.161] (**) Option "xkb_model" "pc105"
[    56.161] (**) Option "xkb_layout" "us"
[    56.161] (WW) Option "xkb_variant" requires a string value
[    56.161] (WW) Option "xkb_options" requires a string value
[    56.162] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[    56.162] (II) event0  - Sleep Button: device is a keyboard
[    56.162] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[    56.162] (II) No input driver specified, ignoring this device.
[    56.162] (II) This device may have been added with another device file.
[    56.162] (II) config/udev: removing device Power Button
[    56.162] (II) event1  - Power Button: device removed
[    56.177] (II) UnloadModule: "libinput"
[    56.178] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    56.178] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    56.178] (II) Using input driver 'libinput' for 'Power Button'
[    56.178] (**) Power Button: always reports core events
[    56.178] (**) Option "Device" "/dev/input/event1"
[    56.178] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    56.178] (II) event1  - Power Button: device is a keyboard
[    56.178] (II) event1  - Power Button: device removed
[    56.193] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    56.193] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    56.193] (**) Option "xkb_model" "pc105"
[    56.193] (**) Option "xkb_layout" "us"
[    56.193] (WW) Option "xkb_variant" requires a string value
[    56.193] (WW) Option "xkb_options" requires a string value
[    56.194] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    56.194] (II) event1  - Power Button: device is a keyboard
[    56.194] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event14)
[    56.194] (II) No input driver specified, ignoring this device.
[    56.194] (II) This device may have been added with another device file.
[    56.194] (II) config/udev: removing device Logitech Wireless Mouse M560
[    56.194] (II) event6  - Logitech Wireless Mouse M560: device removed
[    56.254] (II) UnloadModule: "libinput"
[    56.254] (II) config/udev: Adding input device Logitech Wireless Mouse M560 (/dev/input/event6)
[    56.254] (**) Logitech Wireless Mouse M560: Applying InputClass "libinput pointer catchall"
[    56.254] (II) Using input driver 'libinput' for 'Logitech Wireless Mouse M560'
[    56.254] (**) Logitech Wireless Mouse M560: always reports core events
[    56.254] (**) Option "Device" "/dev/input/event6"
[    56.255] (II) event6  - Logitech Wireless Mouse M560: is tagged by udev as: Mouse
[    56.255] (II) event6  - Logitech Wireless Mouse M560: device is a pointer
[    56.255] (II) event6  - Logitech Wireless Mouse M560: device removed
[    56.301] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input16/event6"
[    56.301] (II) XINPUT: Adding extended input device "Logitech Wireless Mouse M560" (type: MOUSE, id 12)
[    56.301] (**) Option "AccelerationScheme" "none"
[    56.302] (**) Logitech Wireless Mouse M560: (accel) selected scheme none/0
[    56.302] (**) Logitech Wireless Mouse M560: (accel) acceleration factor: 2.000
[    56.302] (**) Logitech Wireless Mouse M560: (accel) acceleration threshold: 4
[    56.302] (II) event6  - Logitech Wireless Mouse M560: is tagged by udev as: Mouse
[    56.302] (II) event6  - Logitech Wireless Mouse M560: device is a pointer
[    56.303] (II) config/udev: removing device   USB Keyboard System Control
[    56.303] (II) event4  -   USB Keyboard System Control: device removed
[    56.325] (II) UnloadModule: "libinput"
[    56.326] (II) config/udev: Adding input device   USB Keyboard System Control (/dev/input/event4)
[    56.326] (**)   USB Keyboard System Control: Applying InputClass "libinput keyboard catchall"
[    56.326] (II) Using input driver 'libinput' for '  USB Keyboard System Control'
[    56.326] (**)   USB Keyboard System Control: always reports core events
[    56.326] (**) Option "Device" "/dev/input/event4"
[    56.326] (II) event4  -   USB Keyboard System Control: is tagged by udev as: Keyboard
[    56.326] (II) event4  -   USB Keyboard System Control: device is a keyboard
[    56.327] (II) event4  -   USB Keyboard System Control: device removed
[    56.353] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input4/event4"
[    56.353] (II) XINPUT: Adding extended input device "  USB Keyboard System Control" (type: KEYBOARD, id 10)
[    56.353] (**) Option "xkb_model" "pc105"
[    56.353] (**) Option "xkb_layout" "us"
[    56.353] (WW) Option "xkb_variant" requires a string value
[    56.353] (WW) Option "xkb_options" requires a string value
[    56.354] (II) event4  -   USB Keyboard System Control: is tagged by udev as: Keyboard
[    56.354] (II) event4  -   USB Keyboard System Control: device is a keyboard
[    56.355] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event12)
[    56.355] (II) No input driver specified, ignoring this device.
[    56.355] (II) This device may have been added with another device file.
[    56.355] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event13)
[    56.355] (II) No input driver specified, ignoring this device.
[    56.355] (II) This device may have been added with another device file.
[    56.355] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event8)
[    56.355] (II) No input driver specified, ignoring this device.
[    56.355] (II) This device may have been added with another device file.
[    56.355] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event9)
[    56.355] (II) No input driver specified, ignoring this device.
[    56.355] (II) This device may have been added with another device file.
[    56.355] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event11)
[    56.355] (II) No input driver specified, ignoring this device.
[    56.355] (II) This device may have been added with another device file.
[    56.850] (II) modeset(0): Disabling kernel dirty updates, not required.
[    56.884] (II) event2  - Power Button: device removed
[    56.913] (II) event5  -   USB Keyboard Consumer Control: device removed
[    56.953] (II) event3  -   USB Keyboard: device removed
[    56.973] (II) event0  - Sleep Button: device removed
[    56.989] (II) event1  - Power Button: device removed
[    57.009] (II) event6  - Logitech Wireless Mouse M560: device removed
[    57.057] (II) event4  -   USB Keyboard System Control: device removed
[    57.074] (II) UnloadModule: "libinput"
[    57.074] (II) UnloadModule: "libinput"
[    57.074] (II) UnloadModule: "libinput"
[    57.074] (II) UnloadModule: "libinput"
[    57.074] (II) UnloadModule: "libinput"
[    57.074] (II) UnloadModule: "libinput"
[    57.074] (II) UnloadModule: "libinput"
[    57.252] (II) Server terminated successfully (0). Closing log file.


```

---

### Post by MAFoElffen on 2024-01-12
This is what I want you to do from the LiveUSB:
```

sudo su -
mount /dev/sda2 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot /mnt /bin/bash --login
mount -a
apt update
apt remove --purge nvidia* libnvidia*
apt install nvidia-driver-470
exit
umount /mnt
reboot

```

---

### Post by kotgc on 2024-01-12
Yes, I figured out the correct code and ran the commands, however same issue.
I even added a new command: update-initramfs-u

---

### Post by MAFoElffen on 2024-01-12
While chrooted it...

What does this list?
```

ubuntu-drivers list

```

---

### Post by kotgc on 2024-01-12
```
root@ubuntu:/# ubuntu-drivers list
nvidia-driver-390, (kernel modules provided by nvidia-dkms-390)
nvidia-driver-470-server, (kernel modules provided by linux-modules-nvidia-470-server-generic-hwe-22.04)
nvidia-driver-470, (kernel modules provided by linux-modules-nvidia-470-generic-hwe-22.04)
nvidia-driver-418-server, (kernel modules provided by nvidia-dkms-418-server)
nvidia-driver-450-server, (kernel modules provided by nvidia-dkms-450-server)


```

---

### Post by kotgc on 2024-01-12
I ran a Boot Repair, with this output:

Boot successfully repaired.

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/NfGJbdQNss/](https://paste.ubuntu.com/p/NfGJbdQNss/)


In case you still experience boot problem, indicate this URL to:
(boot.repair email) or to your favorite support forum.

Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !


** I rebooted and still a black screen.**


```
boot-repair-4ppa2075                                              [20240113_0030]

============================= Boot Repair Summary ==============================





modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file


Mount /dev/sda1 on /mnt/boot-sav/sda2/boot/efi

Unhide GRUB boot menu in sda2/etc/default/grub

===================== Reinstall the grub-efi of /dev/sda2 ======================

chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/sda2 modprobe efivars

chroot /mnt/boot-sav/sda2 efibootmgr -v before grub install
EFI variables are not supported on this system.


chroot /mnt/boot-sav/sda2 uname -r
6.2.0-26-generic

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda2 efibootmgr -v after grub install
EFI variables are not supported on this system.

Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sde and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sde: /dev/sde already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GK208B [GeForce GT 710] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: P1.10(5.17) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0001
Boot0001* ubuntu    HD(1,GPT,bd0686e0-0be9-4701-8c97-d23439b37efd,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0002* UEFI: TOSHIBA TOSHIBA USB DRV PMAP, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,GPT,f45e2fa1-c5a6-4d79-876d-c8245af921e0,0x95f864,0x2754)..BO

64349b3622c65f495a99dbf6102496e3   sda1/BOOT/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sda1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdd    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdd1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdd1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdd1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd

fdisk -l (filtered): ___________________________________________________________

Disk sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk identifier: F67B32DF-306B-4B7B-B8D3-EB99025AEC95
       Start       End   Sectors   Size Type
sda1     2048   1050623   1048576   512M EFI System
sda2  1050624 468860927 467810304 223.1G Linux filesystem
Disk sdb: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 8DFA5813-3BD3-49F1-BEEF-4F3B697026BF
     Start       End   Sectors   Size Type
sdb1   2048 234440703 234438656 111.8G Linux filesystem
Disk sdc: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 781288B8-D088-4C28-8D0D-44F603F4475A
     Start       End   Sectors   Size Type
sdc1   2048 234440703 234438656 111.8G Linux filesystem
Disk sdd: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 480BBA39-4051-4EDA-939B-28AEEC589F50
     Start       End   Sectors   Size Type
sdd1   2048 234440703 234438656 111.8G Linux filesystem
Disk sde: 14.44 GiB, 15506341888 bytes, 30285824 sectors
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0
       Start      End  Sectors  Size Type
sde1       64  9828451  9828388  4.7G Microsoft basic data
sde2  9828452  9838519    10068  4.9M EFI System
sde3  9838520  9839119      600  300K Microsoft basic data
sde4  9842688 30285760 20443073  9.7G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:240GB:scsi:512:512:gpt:ATA INTEL SSDSC2KW24:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:240GB:240GB:ext4::;
sdb:120GB:scsi:512:512:gpt:ATA INTEL SSDSC2BW12:;
1:1049kB:120GB:120GB:ext4::;
sdc:120GB:scsi:512:512:gpt:ATA INTEL SSDSC2BW12:;
1:1049kB:120GB:120GB:ext4::;
sdd:120GB:scsi:512:512:gpt:ATA INTEL SSDSC2BW12:;
1:1049kB:120GB:120GB:ext4::;
sde:15.5GB:scsi:512:512:gpt:TOSHIBA TOSHIBA USB DRV:;
1:32.8kB:5032MB:5032MB::ISO9660:hidden, msftdata;
2:5032MB:5037MB:5155kB::Appended2:boot, esp;
3:5037MB:5038MB:307kB::Gap1:hidden, msftdata;
4:5039MB:15.5GB:10.5GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     89BB-BA8F                            bd0686e0-0be9-4701-8c97-d23439b37efd                          EFI System Partition
&#9492;&#9472;sda2 ext4     2d562fa8-4427-451c-b9d8-98cb7882012d c638e404-24b6-41be-a2ae-ffe02b4c1123                          
sdb                                                                                                                
&#9492;&#9472;sdb1 ext4     827eac09-9086-4f4b-8239-26ccfe66a8e1 d3017330-9f67-467c-8d12-67c7434caea2                          
sdc                                                                                                                
&#9492;&#9472;sdc1 ext4     6a0d5b2c-0102-42fa-9c73-bb80b421e1a7 e89b2561-1cea-4bb5-9353-1e041f2ab026                          
sdd                                                                                                                
&#9492;&#9472;sdd1 ext4     8b6dc8bf-2418-4b2f-8df2-39837c95b47c 9981eccf-5e00-4f1a-afff-c84589e6b64e                          
sde    iso9660  2023-08-08-01-19-05-00                                                    Ubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sde1 iso9660  2023-08-08-01-19-05-00               f45e2fa1-c5a6-4d79-876e-c8245af921e0 Ubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sde2 vfat     F7DB-4D56                            f45e2fa1-c5a6-4d79-876d-c8245af921e0 ESP                      Appended2
&#9500;&#9472;sde3                                               f45e2fa1-c5a6-4d79-876c-c8245af921e0                          Gap1
&#9492;&#9472;sde4 ext4     00e50e44-75db-43b0-9088-4d3e792e4e70 88c30865-84f7-784b-b35d-9a6085c25064 writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/sda1                                                       504M   1% /mnt/boot-sav/sda1
/dev/sda2                                                      64.8G  65% /mnt/boot-sav/sda2
/dev/sdb1                                                      40.2G  58% /mnt/boot-sav/sdb1
/dev/sdc1                                                      40.2G  58% /mnt/boot-sav/sdc1
/dev/sdd1                                                     103.9G   0% /mnt/boot-sav/sdd1
/dev/sde1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2                                                     ext4            rw,relatime
/dev/sdb1                                                     ext4            rw,relatime
/dev/sdc1                                                     ext4            rw,relatime
/dev/sdd1                                                     ext4            rw,relatime
/dev/sde1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 2d562fa8-4427-451c-b9d8-98cb7882012d root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   2d562fa8-4427-451c-b9d8-98cb7882012d
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=2d562fa8-4427-451c-b9d8-98cb7882012d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=89BB-BA8F  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  96.052886963 = 103.136002048  boot/vmlinuz                                   1
  37.638824463 = 40.414380032   boot/vmlinuz-6.2.0-37-generic                  1
  96.052886963 = 103.136002048  boot/vmlinuz-6.2.0-39-generic                  1
  37.638824463 = 40.414380032   boot/vmlinuz.old                               1
  26.398101807 = 28.344745984   boot/initrd.img                                3
  39.230606079 = 42.123542528   boot/initrd.img-6.2.0-26-generic               3
  39.750972748 = 42.682281984   boot/initrd.img-6.2.0-37-generic               4
  26.398101807 = 28.344745984   boot/initrd.img-6.2.0-39-generic               3
  39.750972748 = 42.682281984   boot/initrd.img.old                            4

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom
```

---

### Post by kotgc on 2024-01-12
I ran Boot Repair again, this time with 2, 3 and 4 of 4 SSD disks removed, leaving only SSD1 with Ubuntu on it.

** I rebooted and still a black screen.**


```
boot-repair-4ppa2075                                              [20240113_0100]

============================= Boot Repair Summary ==============================





modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Mount /dev/sda1 on /mnt/boot-sav/sda2/boot/efi

===================== Reinstall the grub-efi of /dev/sda2 ======================

chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/sda2 modprobe efivars

chroot /mnt/boot-sav/sda2 efibootmgr -v before grub install
EFI variables are not supported on this system.


chroot /mnt/boot-sav/sda2 uname -r
6.2.0-26-generic

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda2 efibootmgr -v after grub install
EFI variables are not supported on this system.

Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GK208B [GeForce GT 710] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: P1.10(5.17) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0001
Boot0001* ubuntu    HD(1,GPT,bd0686e0-0be9-4701-8c97-d23439b37efd,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0002* UEFI: TOSHIBA TOSHIBA USB DRV PMAP, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,GPT,f45e2fa1-c5a6-4d79-876d-c8245af921e0,0x95f864,0x2754)..BO

64349b3622c65f495a99dbf6102496e3   sda1/BOOT/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sda1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk identifier: F67B32DF-306B-4B7B-B8D3-EB99025AEC95
       Start       End   Sectors   Size Type
sda1     2048   1050623   1048576   512M EFI System
sda2  1050624 468860927 467810304 223.1G Linux filesystem
Disk sdb: 14.44 GiB, 15506341888 bytes, 30285824 sectors
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0
       Start      End  Sectors  Size Type
sdb1       64  9828451  9828388  4.7G Microsoft basic data
sdb2  9828452  9838519    10068  4.9M EFI System
sdb3  9838520  9839119      600  300K Microsoft basic data
sdb4  9842688 30285760 20443073  9.7G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:240GB:scsi:512:512:gpt:ATA INTEL SSDSC2KW24:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:240GB:240GB:ext4::;
sdb:15.5GB:scsi:512:512:gpt:TOSHIBA TOSHIBA USB DRV:;
1:32.8kB:5032MB:5032MB::ISO9660:hidden, msftdata;
2:5032MB:5037MB:5155kB::Appended2:boot, esp;
3:5037MB:5038MB:307kB::Gap1:hidden, msftdata;
4:5039MB:15.5GB:10.5GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     89BB-BA8F                            bd0686e0-0be9-4701-8c97-d23439b37efd                          EFI System Partition
&#9492;&#9472;sda2 ext4     2d562fa8-4427-451c-b9d8-98cb7882012d c638e404-24b6-41be-a2ae-ffe02b4c1123                          
sdb    iso9660  2023-08-08-01-19-05-00                                                    Ubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2023-08-08-01-19-05-00               f45e2fa1-c5a6-4d79-876e-c8245af921e0 Ubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sdb2 vfat     F7DB-4D56                            f45e2fa1-c5a6-4d79-876d-c8245af921e0 ESP                      Appended2
&#9500;&#9472;sdb3                                               f45e2fa1-c5a6-4d79-876c-c8245af921e0                          Gap1
&#9492;&#9472;sdb4 ext4     00e50e44-75db-43b0-9088-4d3e792e4e70 88c30865-84f7-784b-b35d-9a6085c25064 writable                 

Mount points (filtered): _______________________________________________________

                                                              Avail Use% Mounted on
/dev/sda1                                                      504M   1% /mnt/boot-sav/sda1
/dev/sda2                                                     64.8G  65% /mnt/boot-sav/sda2
/dev/sdb1                                                         0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 2d562fa8-4427-451c-b9d8-98cb7882012d root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   2d562fa8-4427-451c-b9d8-98cb7882012d
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=2d562fa8-4427-451c-b9d8-98cb7882012d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=89BB-BA8F  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  96.052886963 = 103.136002048  boot/vmlinuz                                   1
  37.638824463 = 40.414380032   boot/vmlinuz-6.2.0-37-generic                  1
  96.052886963 = 103.136002048  boot/vmlinuz-6.2.0-39-generic                  1
  37.638824463 = 40.414380032   boot/vmlinuz.old                               1
  26.398101807 = 28.344745984   boot/initrd.img                                3
  39.230606079 = 42.123542528   boot/initrd.img-6.2.0-26-generic               3
  39.750972748 = 42.682281984   boot/initrd.img-6.2.0-37-generic               4
  26.398101807 = 28.344745984   boot/initrd.img-6.2.0-39-generic               3
  39.750972748 = 42.682281984   boot/initrd.img.old                            4

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom
```

---

### Post by MAFoElffen on 2024-01-12
So this is fixed now?

---

### Post by kotgc on 2024-01-12
Please read again, post #27 and #28.

---

### Post by kotgc on 2024-01-12
[https://ubuntuforums.org/showthread.php?t=2489582](https://ubuntuforums.org/showthread.php?t=2489582) -> post #2 suggests # fsck.
Can I run # fsck from the LiveUSB in chroot, or do I need to boot into the machine's grub?

---

### Post by MAFoElffen on 2024-01-13
Both those say you are booting as it's not finding EFIVARS...

Boot on your installer LiveUSB. Open a terminal and please post the results of this within Codes tags
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```

---

### Post by kotgc on 2024-01-13
Just ran fsck, see what happens with  reboot?
```
ubuntu@ubuntu:~$ fdisk -l
fdisk: cannot open /dev/loop0: Permission denied
fdisk: cannot open /dev/loop1: Permission denied
fdisk: cannot open /dev/loop2: Permission denied
fdisk: cannot open /dev/loop3: Permission denied
fdisk: cannot open /dev/loop4: Permission denied
fdisk: cannot open /dev/loop5: Permission denied
fdisk: cannot open /dev/loop6: Permission denied
fdisk: cannot open /dev/loop7: Permission denied
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/sdb: Permission denied
fdisk: cannot open /dev/loop8: Permission denied
fdisk: cannot open /dev/loop9: Permission denied
fdisk: cannot open /dev/loop10: Permission denied
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# fdisk -l
Disk /dev/loop0: 3.02 GiB, 3241230336 bytes, 6330528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 237.21 MiB, 248729600 bytes, 485800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 53.26 MiB, 55844864 bytes, 109072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: INTEL SSDSC2KW24
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F67B32DF-306B-4B7B-B8D3-EB99025AEC95

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 468860927 467810304 223.1G Linux filesystem


Disk /dev/sdb: 14.44 GiB, 15506341888 bytes, 30285824 sectors
Disk model: TOSHIBA USB DRV 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0

Device       Start      End  Sectors  Size Type
/dev/sdb1       64  9828451  9828388  4.7G Microsoft basic data
/dev/sdb2  9828452  9838519    10068  4.9M EFI System
/dev/sdb3  9838520  9839119      600  300K Microsoft basic data
/dev/sdb4  9842688 30285760 20443073  9.7G Linux filesystem


Disk /dev/loop8: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
root@ubuntu:~# fsck /dev/sda2 
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/sda2: clean, 342280/14622720 files, 38560058/58476288 blocks

```

---

### Post by kotgc on 2024-01-13
** I rebooted and still a black screen.**

---

### Post by kotgc on 2024-01-13
Rebooted into grub -> selected 'e' -> appended the linux line with: systemd.unit=multi-user.target -> Ctrl+x -> Ubuntu login: -> logged in -> ran command$ sudo systemctl set-default graphical.target -> Enter -> Created symlink /etc/systemd/system/default.target->/lib/systemd/system/graphical.target -> **I rebooted and still a black screen.**
It appears the GUI cannot be activated, there is a configuration issue in starting the GUI.

---

### Post by kotgc on 2024-01-13
Checked with Gnome support about why Gnome won't start the GUI, but Ubuntu 22.04.3's Gnome version is too old and not supported anymore by upstream GNOME.

---

### Post by kotgc on 2024-01-13
If it helps here's the LiveUSB's journal control:
```
ubuntu@ubuntu:~$ journalctl 
Jan 13 05:47:36 ubuntu kernel: microcode: microcode updated early to revision 0>
Jan 13 05:47:36 ubuntu kernel: Linux version 6.2.0-26-generic (buildd@bos03-amd>
Jan 13 05:47:36 ubuntu kernel: Command line: BOOT_IMAGE=/casper/vmlinuz file=/c>
Jan 13 05:47:36 ubuntu kernel: KERNEL supported cpus:
Jan 13 05:47:36 ubuntu kernel:   Intel GenuineIntel
Jan 13 05:47:36 ubuntu kernel:   AMD AuthenticAMD
Jan 13 05:47:36 ubuntu kernel:   Hygon HygonGenuine
Jan 13 05:47:36 ubuntu kernel:   Centaur CentaurHauls
Jan 13 05:47:36 ubuntu kernel:   zhaoxin   Shanghai  
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 fl>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE re>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX re>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x008: 'MPX bo>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x010: 'MPX CS>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]>
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Enabled xstate features 0x1f, context s>
Jan 13 05:47:36 ubuntu kernel: signal: max sigframe size: 2032
Jan 13 05:47:36 ubuntu kernel: BIOS-provided physical RAM map:
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000000000000-0x00000000000>
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000000009e000-0x00000000000>
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000000009f000-0x00000000000>
lines 1-23...skipping...
Jan 13 05:47:36 ubuntu kernel: microcode: microcode updated early to revision 0xf4, date = 2022-07-31
Jan 13 05:47:36 ubuntu kernel: Linux version 6.2.0-26-generic (buildd@bos03-amd64-042) (x86_64-linux-gnu-gcc-11 (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #26~22.04.1-Ubun>
Jan 13 05:47:36 ubuntu kernel: Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash ---
Jan 13 05:47:36 ubuntu kernel: KERNEL supported cpus:
Jan 13 05:47:36 ubuntu kernel:   Intel GenuineIntel
Jan 13 05:47:36 ubuntu kernel:   AMD AuthenticAMD
Jan 13 05:47:36 ubuntu kernel:   Hygon HygonGenuine
Jan 13 05:47:36 ubuntu kernel:   Centaur CentaurHauls
Jan 13 05:47:36 ubuntu kernel:   zhaoxin   Shanghai  
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
Jan 13 05:47:36 ubuntu kernel: signal: max sigframe size: 2032
Jan 13 05:47:36 ubuntu kernel: BIOS-provided physical RAM map:
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000000009e000-0x000000000009efff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000000100000-0x000000003fffffff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000040000000-0x00000000403fffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000040400000-0x000000008d84cfff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008d84e000-0x000000008e9abfff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008e9ad000-0x000000009b845fff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b847000-0x000000009b869fff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b86a000-0x000000009b86afff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b86b000-0x000000009b9aefff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009dcff000-0x000000009effefff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009efff000-0x000000009effffff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009f000000-0x000000009fffffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000100000000-0x000000045dffffff] usable
Jan 13 05:47:36 ubuntu kernel: NX (Execute Disable) protection: active
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x966ac018-0x966cc657] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x966ac018-0x966cc657] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x9669d018-0x966ab057] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x9669d018-0x966ab057] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: extended physical RAM map:
Jan 13 05:47:36 ubuntu kernel: reserve setup_data: [mem 0x0000000000000000-0x000000000009dfff] usable
Jan 13 05:47:36 ubuntu kernel: reserve setup_data: [mem 0x000000000009e000-0x000000000009efff] reserved
Jan 13 05:47:36 ubuntu kernel: reserve setup_data: [mem 0x000000000009f000-0x000000000009ffff] usable
Jan 13 05:47:36 ubuntu kernel: reserve setup_data: [mem 0x00000000000a0000-0x00000000000fffff] reserved
lines 1-57























































Jan 13 05:47:36 ubuntu kernel: microcode: microcode updated early to revision 0xf4, date = 2022-07-31
Jan 13 05:47:36 ubuntu kernel: Linux version 6.2.0-26-generic (buildd@bos03-amd64-042) (x86_64-linux-gnu-gcc-11 (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #26~22.04.1>
Jan 13 05:47:36 ubuntu kernel: Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash ---
Jan 13 05:47:36 ubuntu kernel: KERNEL supported cpus:
Jan 13 05:47:36 ubuntu kernel:   Intel GenuineIntel
Jan 13 05:47:36 ubuntu kernel:   AMD AuthenticAMD
Jan 13 05:47:36 ubuntu kernel:   Hygon HygonGenuine
Jan 13 05:47:36 ubuntu kernel:   Centaur CentaurHauls
Jan 13 05:47:36 ubuntu kernel:   zhaoxin   Shanghai  
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
Jan 13 05:47:36 ubuntu kernel: x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
Jan 13 05:47:36 ubuntu kernel: x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
Jan 13 05:47:36 ubuntu kernel: signal: max sigframe size: 2032
Jan 13 05:47:36 ubuntu kernel: BIOS-provided physical RAM map:
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000000009e000-0x000000000009efff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000000100000-0x000000003fffffff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000040000000-0x00000000403fffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000040400000-0x000000008d84cfff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008d84e000-0x000000008e9abfff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000008e9ad000-0x000000009b845fff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b847000-0x000000009b869fff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b86a000-0x000000009b86afff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b86b000-0x000000009b9aefff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009dcff000-0x000000009effefff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009efff000-0x000000009effffff] usable
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x000000009f000000-0x000000009fffffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Jan 13 05:47:36 ubuntu kernel: BIOS-e820: [mem 0x0000000100000000-0x000000045dffffff] usable
Jan 13 05:47:36 ubuntu kernel: NX (Execute Disable) protection: active
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x966ac018-0x966cc657] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x966ac018-0x966cc657] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x9669d018-0x966ab057] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: e820: update [mem 0x9669d018-0x966ab057] usable ==> usable
Jan 13 05:47:36 ubuntu kernel: extended physical RAM map:
Jan 13 05:47:36 ubuntu kernel: reserve setup_data: [mem 0x0000000000000000-0x000000000009dfff] usable

```

---

### Post by kotgc on 2024-01-13
I'm unsure that's the right information needed to show Ubuntu 22.04.3 booting to a black screen and not starting the Gnome GUI?
Is there a way to copy journalctl output from grub?

---

### Post by MAFoElffen on 2024-01-13
Did you not see Post #32? What was the output of that?

---

### Post by kotgc on 2024-01-13
ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
UEFI Firmware mode

---

### Post by kotgc on 2024-01-14
Any suggestions how to do this:
1: reach into grub/recovery mode (this step is ok holding Shift at boot) and fix broken packages from there, to make sure the system is up to date (grub has no network, only the LiveUSB) and get into the Desktop with fail safe graphics?
2: logout to gdm to pick Xorg to boot in?
3: doublecheck which graphics drivers are loaded, nouveau vs nvidia?

---

### Post by kotgc on 2024-01-14
Maybe I should use liveusb to mount the /boot dir and copy the files needed? e.g. Linux VM et al? How would I do that?

---

### Post by BicyclerBoy on 2024-01-14
If you try to use an other live system you must "chroot" into the target to be able to repair it.
Else all the target mountpoints & locations are all wrong.
And it is vital that the EFI partition is mounted into the chroot correctly else grub install/updates are all wrong.
And the initramfs can be copied to wrong location.

You are far better rebooting to your "black screen" & then switching to a console terminal (<ctrl> +<alt>+<F1>).
But does this result in no network connectivity? Get a wifi dongle ? switch onboard wifi?

I would purge nvidia rebuild initramfs then reboot. Any better?
Blacklist nouveau, rebuild initramfs & reboot. Any better?
See what driver is used in Xorg.0.log..

Grub kernel cmd line option "nomodeset" should stop most of video drivers but I'm not so sure this works. 

If PC works okay then do NOT install nvidia driver.

---

### Post by kotgc on 2024-01-14
Why is it far better to reboot to "black screen"?
Terminal (Ctrl+Alt+F1) doesn't bring up Terminal.
I would have to buy a Wi-Fi USB dongle at the shops, which are notorious for not working with Linux and most shops don't accept refunds or replacements.

I think LiveUSB with "chroot" is best, however I need help with the commands.
I'm confused about what is the root to mount.../dev/sda or /dev/sda2?

---

### Post by kotgc on 2024-01-14
As per LiveUSB Terminal, looks like /dev/sda1 is the EFI:

My understanding is EFI is just for booting and is not the root.
Therefore, the root must be /dev/sda2.

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 3.02 GiB, 3241230336 bytes, 6330528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 237.21 MiB, 248729600 bytes, 485800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: INTEL SSDSC2KW24
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F67B32DF-306B-4B7B-B8D3-EB99025AEC95

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 468860927 467810304 223.1G Linux filesystem


Disk /dev/sdb: 14.44 GiB, 15506341888 bytes, 30285824 sectors
Disk model: TOSHIBA USB DRV 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0

Device       Start      End  Sectors  Size Type
/dev/sdb1       64  9828451  9828388  4.7G Microsoft basic data
/dev/sdb2  9828452  9838519    10068  4.9M EFI System
/dev/sdb3  9838520  9839119      600  300K Microsoft basic data
/dev/sdb4  9842688 30285760 20443073  9.7G Linux filesystem


Disk /dev/loop8: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 53.26 MiB, 55844864 bytes, 109072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by MAFoElffen on 2024-01-14
From the Grub2 menu, press the <E> key. <Arrow-Down> to the line that starts with the word "linux". <Arrow-Right> until you get the the words "quiet splash". Replace that with "--- nomodeset". Press <Cntrl><X> to boot.

That will boot into safe graphics mode. That is also the same mode the Recovery Menu boots into using that same boot parameter. So when you go to the Recovery Menu, then use Resume, that is the mode. Not what someone mentioned a few posts ago.

*** Alternate to that, use the boot parameters I told you to use in Post #2.

Either way, tell me what this says:
```

uname -r

```
If it says: "6.5.0-14-generic", then this is what I what you to try... Reboot. Press the shift key repeatedly to get back to the Grub2 Menu...

Select "Advanced options for Ubuntu" > Select Ubuntu with a 6.2.0-X kernel. Boot. If it boots, the problem is with the 6.5.0-14 kernel... Which since it hit 22.04.3 this last week, no NVidia drivers have been able to compile with that kernel. This has been reported to NVidia, and there is a thread on their Forum on this, for this kernel.
RE: [https://forums.developer.nvidia.com/t/linux-new-kernel-6-5-0-14-ubuntu-22-04-can-not-compile-nvidia-display-card-driver/278553](https://forums.developer.nvidia.com/t/linux-new-kernel-6-5-0-14-ubuntu-22-04-can-not-compile-nvidia-display-card-driver/278553)

I, myself, have Linux kernel 6.5.0-14 uninstalled, kernel 6.2.0-39 reinstalled, so that all the headers files & such are there, and that kernel pinned... I'm running NVidia and Cuda with kernel 6.2.0-39 until they get that fixed. For both nvidia drivers nvidia-drver-525, and nvidia-driver-390...
RE: [https://ubuntuforums.org/showthread.php?t=2494349&p=14174974#post14174974](https://ubuntuforums.org/showthread.php?t=2494349&p=14174974#post14174974)

---

### Post by kotgc on 2024-01-14
No, if you read post #20, I already tried --nomodeset and Ubuntu still boots into a black screen.
I tested --- nomodeset and also ---nomodeset and Ubuntu still boots into a black screen.

You suggested in post #2 to use --- 3, however Ubuntu still boots into a black screen.

As per post #1 point 1, I have booted to the recovery mode text menu and selected "resume", however Ubuntu still boots into a black screen.

LiveUSB -> ubuntu@ubuntu:~$ uname -r
6.2.0-26-generic

---

### Post by BicyclerBoy on 2024-01-14
Sorry did not find where you had tried (Ctrl+Alt+F1)..
That dead state suggests the video driver has crashed/locked the xserver.

I understand that nomodeset option is used without any "--" or "---".
Any preceding "--- "  may interfere...

But "nomodeset" only delays any problem driver until later in xserver startup.
I don't think it has any effect on nvidia proprietary module/driver.

Can you "ssh" into the PC (stuck on blank screen) from another computer?
Is possible xorg xserver is locked up but computer is still functioning.

The GT710 is barely more than a framebuffer text screen for a server install..
Is it possible to remove the nvidia card & plug in Intel or AMD card. Or use Intel iGPU?

It's no help to you now but:
Nvidia users learn from years of pain to NEVER update a kernel & graphics driver at the same time.
Always do one or the other & reboot test & decide..
And in this case it maybe the change in gcc / libc versions.

---

### Post by kotgc on 2024-01-14
Thanks for the timely reply!
Yes, you're right, I hadn't tried the Ctrl+Alt+F1 before your helpful suggestion :-)

Tried the nomodeset option without any "--" or "---", however Ubuntu 22.04.3 still boots to a black screen.

My Ubuntu 22.04.3 configuration has no network until the VMM has started the KVM router.
Therefore, LiveUSB is the only networked controller during this black screen challenge.

I could remove the NVIDIA card, which is there to enable 3 monitors. I trust the MOBO graphics card can still run 1 monitor?

Ok, so I'll try to figure out how to update the kernel and then the graphics driver, however these updates can only be done in the LiveUSB chroot. So once 1 driver is updated and I boot into the black screen, I then I have reboot into the LiveUSB, which will have lost update1 I think?

---

### Post by MAFoElffen on 2024-01-14
If you refer to my Graphics Resolution Sticky in my signature line...

"--" or "---" preceding the boot parameters, you'll find that in many grub boot menu items... That is often used with "3" which tells it to go into rc user mode 3, or whne you use "single". I've been doing Linux Graphics Layer Support since 2005, since Alan Coopersimth Taught me about taking my XServer skills (since 1988) and applying them to Xorg support. What those dashes do is that it often helps parameters given after that to not be "ignored".

As I mention in my Sticky, if you used "--- 3" and it doesn't go to a text console (you said it still goes to blackscreen)... If you used "nomodeset" and it goes to a blackscreen... Didn't you also say you tried "Recovery" and it goes to blackscreen... (recovery is mostly 'nomodeset' for the graphics side of that mode)... Then you have bigger problems.

You did to say if you tried to use an earlier kernel...

You say you booted from an Ubuntu 22.04.2 LiveUSB... But you do not have networking, because your router is running on that machine, from KVM right? Did it have good graphics? What kernel was running on that? What was the boot parameters from the Grub2 menu option that it starts from?

---

### Post by kotgc on 2024-01-14
I tried both recovery kernels:
Linux 6.2.0-39-generic (recovery mode)
Linux 6.2.0-37-generic (recovery mode); I guess this can be considered trying to use an earlier kernel?

LiveUSB is booting Ubuntu 22.04.3 LTS with Kernel 6.2.0-26-generic.
LiveUSB has networking.
Ubuntu 22.04.3 doesn't have networking until Ubuntu's VMM starts the KVM router.

Graphics have always been fine until I changed SSD disk 3 of 4, as per post #1.
I have no idea what kernel the graphics were running on, however I do know I was using Ubuntu 22.04.3 LTS with the latest updates.
I have no idea what was the boot parameters from the Grub2 menu option that it (what is it?) starts from?

---

### Post by kotgc on 2024-01-15
Well, I disconnected the 3 monitors from the GPU -> removed the GPU from the MOBO -> connected 1 HDMI monitor to the MOBO -> powered on and blackscreens, not even boot.
I then powered the machine off -> disconnected the HDMI monitor -> connected the VGA monitor -> powered on and blackscreens, not even boot.
I then powered the machine off -> disconnected the VGA monitor from the MOBO -> reconnected the GPU -> reconnected the HDMI, DVI-D and VGA monitors -> powered on and black screen.
I then powered the machine off -> inserted the LiveUSB -> powered on -> the 2 monitors HDMI and DVI-D that have always been showing, show Ubuntu LiveUSB.
```
ubuntu@ubuntu:~$ sudo dmidecode -t 2
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASRock
    Product Name: H470M-HVS
    Version:                       
    Serial Number: M80-E1006100869
    Asset Tag:                       
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis:                       
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

ubuntu@ubuntu:~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 710]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 resolution=1920,1080
       resources: irq:128 memory:aa000000-aaffffff memory:a0000000-a7ffffff memory:a8000000-a9ffffff ioport:5000(size=128) memory:c0000-dffff

ubuntu@ubuntu:~$ xrandr 
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384
DVI-D-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+  74.97    50.00    59.94    60.00  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     60.00    59.88  
   1400x1050     60.00  
   1600x900      60.00  
   1280x1024     75.02    60.02    60.00  
   1440x900      59.90  
   1400x900      60.00  
   1280x960      60.00  
   1440x810      60.00  
   1368x768      60.00  
   1280x800      60.00  
   1152x864      60.00  
   1280x720      60.00    50.00    59.94    60.00  
   1024x768      75.03    70.07    60.00    60.00  
   960x720       60.00  
   928x696       60.00  
   896x672       60.00  
   1024x576      60.00  
   960x600       60.00  
   832x624       74.55    60.00  
   960x540       60.00  
   800x600       72.19    75.00    60.32    60.00    56.25  
   840x525       60.00  
   864x486       60.00  
   720x576       50.00  
   700x525       60.00  
   800x450       60.00  
   720x480       60.00    59.94  
   640x512       60.00  
   700x450       60.00  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x405       60.00  
   720x400       70.08  
   684x384       60.00  
   576x432       60.00  
   640x360       60.00  
   512x384       60.00  
   512x288       60.00  
   416x312       60.00  
   480x270       60.00  
   400x300       60.00  
   432x243       60.00  
   320x240       60.00  
   360x202       60.00  
   320x180       60.00  
HDMI-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080     60.00*+  74.97    50.00    59.94    60.00  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     60.00    59.88  
   1400x1050     60.00  
   1600x900      60.00  
   1280x1024     75.02    60.02    60.00  
   1440x900      59.90  
   1400x900      60.00  
   1280x960      60.00  
   1440x810      60.00  
   1368x768      60.00  
   1280x800      60.00  
   1152x864      60.00  
   1280x720      60.00    50.00    59.94    60.00  
   1024x768      75.03    70.07    60.00    60.00  
   960x720       60.00  
   928x696       60.00  
   896x672       60.00  
   1024x576      60.00  
   960x600       60.00  
   832x624       74.55    60.00  
   960x540       60.00  
   800x600       72.19    75.00    60.32    60.00    56.25  
   840x525       60.00  
   864x486       60.00  
   720x576       50.00  
   700x525       60.00  
   800x450       60.00  
   720x480       60.00    59.94  
   640x512       60.00  
   700x450       60.00  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x405       60.00  
   720x400       70.08  
   684x384       60.00  
   576x432       60.00  
   640x360       60.00  
   512x384       60.00  
   512x288       60.00  
   416x312       60.00  
   480x270       60.00  
   400x300       60.00  
   432x243       60.00  
   320x240       60.00  
   360x202       60.00  
   320x180       60.00  
VGA-1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by kotgc on 2024-01-15
I'm working on post #43, but I'm unsure on what code to use, as this has to run from LiveUSB chroot?
1: I would purge nvidia rebuild initramfs then reboot. Any better?
2: Blacklist nouveau, rebuild initramfs & reboot. Any better?
3: See what driver is used in Xorg.0.log..

---

### Post by BicyclerBoy on 2024-01-15
You may have to enable the mobo iGPU in UEFI-BIOS.
Does your CPU have integrated graphics?

That approach is far safer & direct than learning about chrooting.

The Nvidia GK104 & GK208 are supposed to be the sweet spot for legacy nouveau.
Close to closed driver performance & features.

---

### Post by kotgc on 2024-01-15
According to [Intel]("https://www.intel.com/content/www/us/en/products/sku/203474/intel-core-i310105f-processor-6m-cache-up-to-4-40-ghz/specifications.html"): "this processor, like all F-Series processors, has no integrated graphics chipset (Intel UHD Graphics). The graphics output of your motherboard will therefore be inoperative. The use of a dedicated graphics card will be mandatory to benefit from a display".

```
ubuntu@ubuntu:~$ lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         39 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  8
  On-line CPU(s) list:   0-7
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM) i3-10105F CPU @ 3.70GHz
    CPU family:          6
    Model:               165
    Thread(s) per core:  2
    Core(s) per socket:  4
    Socket(s):           1
    Stepping:            3
    CPU max MHz:         4400.0000
    CPU min MHz:         800.0000
    BogoMIPS:            7399.70
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon 
                         pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt 
                         tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_
                         ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts md_clear flush_l1d arch_capa
                         bilities
Virtualization features: 
  Virtualization:        VT-x
Caches (sum of all):     
  L1d:                   128 KiB (4 instances)
  L1i:                   128 KiB (4 instances)
  L2:                    1 MiB (4 instances)
  L3:                    6 MiB (1 instance)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-7
Vulnerabilities:         
  Itlb multihit:         KVM: Mitigation: VMX disabled
  L1tf:                  Not affected
  Mds:                   Not affected
  Meltdown:              Not affected
  Mmio stale data:       Mitigation; Clear CPU buffers; SMT vulnerable
  Retbleed:              Mitigation; Enhanced IBRS
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:            Mitigation; Enhanced IBRS, IBPB conditional, RSB filling, PBRSB-eIBRS SW sequence
  Srbds:                 Mitigation; Microcode
  Tsx async abort:       Not affected

```

UEFI version:
sudo dmidecode | less
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.
Table at 0x9EB72000.

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
        Vendor: American Megatrends Inc.
        Version: P1.10
        Release Date: 01/11/2021
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 16 MB
        Characteristics:
                PCI is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 5.17

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: To Be Filled By O.E.M.
        Product Name: To Be Filled By O.E.M.
        Version: To Be Filled By O.E.M.
        Serial Number: To Be Filled By O.E.M.
        UUID: 6e59a1a8-8b1f-0000-0000-000000000000
        Wake-up Type: Power Switch
        SKU Number: To Be Filled By O.E.M.
        Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASRock
        Product Name: H470M-HVS
        Version:                       
        Serial Number: M80-E1006100869
        Asset Tag:                       
        Features:
                Board is a hosting board
                Board is replaceable

---

### Post by BicyclerBoy on 2024-01-15
You are 100% sure your GT710 has UEFI GOP & can boot in EFI mode?
This model was made around period of transition.

I think most of the Kepler cards shipped without any EFI support.
I modified the VBIOS on Kepler GK104 GTX660ti to work in UEFI system.
But the GT710 may have been a later model based on the older series (600) so shipped with EFI GOP.

You have tried turning OFF FastBoot & SecureBoot in UEFI-BIOS ?

Seems to have been some history of early UEFI videocards (including GT710) having problems with black screen in some mobos & especially with FastBoot &/or SecureBoot enabled.

Are you sure the system is not busy doing disk check/scan?

---

### Post by kotgc on 2024-01-15
All I know is the card worked fine before.
There must be some settings that can be corrected?

---

### Post by MAFoElffen on 2024-01-15
@BicyclerBoy ---

If you look at his output
```

Base Board Information
    Manufacturer: ASRock
    Product Name: H470M-HVS

```
That board's BIOS has EFI framebuffer support, even if his old NVidia GPU doesn't. That GPU is supported by both nouveau and nvidia-driver-470...

If his kernel is currently 6.5.0-14, that does not currently work with building Nvidia drivers... Especial legacy NVidia drivers.

It does work with his 22.04.3 Kernel on his LiveUSB...

Here is the plan. Boot from your LiveUSB. Chroot into your installed system.
```

sudo su -
mount /dev/sda2 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot /mnt /bin/bash --login
mount -a

```
Remove any NVidia drivers
```

apt update
apt remove --purge nvidia* libnvidia*

```
Add a few edits to your Grub Menu so it's easier to work with during this
```

sudo nano /etc/defaults/grub

```
Make these edits
```

GRUB_DEFAULT=0
[COLOR=#ff0000]GRUB_TIMEOUT_STYLE=show
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=#ff0000]GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid nomodeset"[/COLOR]
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]GRUB_GFXMODE=1920x1080x24[/COLOR]

```
Pick up the changes
```

sudo update-grub

```
Uninstall the 6.5 kernel, which does not work for your GPU right now...
```

sudo apt remove --purge --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt install --yes linux-headers-6.2.0-26-generic linux-image-6.2.0-26-generic linux-modules-6.2.0-26-generic linux-modules-extra-6.2.0-26-generic
sudo apt-mark hold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```
Exit the chroot
```

exit
umount /mnt
reboot

```
Test...

---

### Post by BicyclerBoy on 2024-01-15
He never posted that he had kernel 6.5, only 6.2.

I believe vesafb can not run on a EFI system.
I know GT710 Kepler is supported by nvidia-470 & knew of the gcc mismatch problem & kernel 6.5.
Just don't see any upside to using nvidia for this card unless nouveau is unstable.

---

### Post by MAFoElffen on 2024-01-15
> **BicyclerBoy said:**
> He never posted that he had kernel 6.5, only 6.2.

I believe vesafb can not run on a EFI system.
I know GT710 Kepler is supported by nvidia-470 & knew of the gcc mismatch problem & kernel 6.5.
Just don't see any upside to using nvidia for this card unless nouveau is unstable.
@BicyclerBoy ---
uvesafb and vesafb works on all 5 of my UEFI machines (and one of those is 32bit UEFI). vesafb works better on Intel chipsets. But that is just to help give the graphics layer a bit of help, before it transitions from the framebuffer to the graphics driver stage in the graphics layer. That seems to help sometimes. At right now, with what he has been through with this, he seems to need some kind of, any kind of help with his graphics. We need to give it a fighting chance. But that only comes in after the grub boot stage of graphics... That earlier stage is were the efi graphics exists...

'efi' graphics drivers were sparse before 2016. If you pester some GPU card vendors, like EVGA and you have one of their GPU cards made after 2016, sometimes they'll give you a link to download an efi driver for 'that' card... But his is old. That's not going to happen for him.

But that is not where is having the problem... He gets his UEFI settings, the Grub2 menu... He loses it and it goes to a black screen when the Linux Graphics Layer comes up during the DE init. In that transition.

If you look at what I posted, I posted as starting out with just 'nomodest' to get it to come up with the nouveau driver. Lets get him working with at least that before trying to install nvidia-driver-470... That way, if later, nvidia-driver-470 doesn't work, then he has something that works to fall back to. 

His problem started about 5 days ago. About the same time that 6.5.0 released to 22.04.3. If he was up on updates, then we know that doesn't work with his NVidia 470 driver. Right?

If you have some ideas, speak up. I'm listening. I have an open mind. I try to learn new things all the time.

I don't mind explaining what I am recommending to the OP, "kotg", to you, so that you understand. I do things for the good of Linux, Ubuntu, and the Forum members here. If I can help other members to be able to support others in need, that just helps us all. That is just the right thing to do.

---

### Post by kotgc on 2024-01-15
Still a black screen.
The Ubuntu boot with dmesg in a font size ~60 instead of the usual font size 5.
The Ubuntu loading splash screen appears, however, then it's still a black screen.

---

### Post by MAFoElffen on 2024-01-15
Did the Grub2 menu show?

---

### Post by kotgc on 2024-01-15
What's Grub2? Is Grub2 different to grub?
I saw no grub, as Ubuntu 22.04.3 LTS Desktop booted through the usual Ubuntu 22.04.3 LTS Desktop dmesg (which has only been showing 3 lines with this black screen challenge and now shows dmesg with a fontsize ~60 rather than the usual ~5?) and splash loading screen, but then went to black screen.

---

### Post by MAFoElffen on 2024-01-15
So you didn't chroot into it and do any of the edits to the /etc/default/grub file did you? I'm now assuming that the answer to that is no, as if you did follow those instructions it would have forced the Grub2 menu to show at least for 5 seconds...

So that begs to ask what of those instructions did you follow, and what else didn't you do?

---

### Post by kotgc on 2024-01-15
I used post #58's code.
See output in posts  #65-#67.
Post #67 does show an anomaly, which I fixed with some added code.

"Here is the plan. Boot from your LiveUSB. Chroot into your installed system."
```

ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# mount /dev/sda2 /mnt/
root@ubuntu:~# mount --make-private --rbind /dev/ /mnt/dev/
root@ubuntu:~# mount --make-private --rbind /proc/ /mnt/proc/
root@ubuntu:~# mount --make-private --rbind /sys/ /mnt/sys/
root@ubuntu:~# mount --make-private --rbind /run/ /mnt/run/
root@ubuntu:~# cd /mnt/
root@ubuntu:/mnt# chroot /mnt/ /bin/bash --login
root@ubuntu:/# mount -a

```

"Remove any NVidia drivers"
```

root@ubuntu:/# apt update 
Running in chroot, ignoring command 'start'
Hit:1 http://au.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://au.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                           
Hit:3 http://au.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                           
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                                                     
Get:5 http://au.archive.ubuntu.com/ubuntu jammy-updates/multiverse i386 Packages [4,184 B]                                                              
Get:6 http://au.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [42.1 kB]                                                                         
Hit:7 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu jammy InRelease                                                                                                                      
Hit:8 https://apt.syncthing.net syncthing InRelease
Fetched 275 kB in 2s (122 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
41 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@ubuntu:/# apt remove --purge nvidia* libnvidia*
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'nvidia-cuda-toolkit-doc' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit-gcc' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-430' for glob 'nvidia*'
Note, selecting 'nvidia-headless-435' for glob 'nvidia*'
Note, selecting 'nvidia-headless-440' for glob 'nvidia*'
Note, selecting 'nvidia-headless-450' for glob 'nvidia*'
Note, selecting 'nvidia-headless-455' for glob 'nvidia*'
Note, selecting 'nvidia-headless-460' for glob 'nvidia*'
Note, selecting 'nvidia-headless-465' for glob 'nvidia*'
Note, selecting 'nvidia-headless-470' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-495' for glob 'nvidia*'
Note, selecting 'nvidia-headless-510' for glob 'nvidia*'
Note, selecting 'nvidia-headless-515' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-520' for glob 'nvidia*'
Note, selecting 'nvidia-headless-525' for glob 'nvidia*'
Note, selecting 'nvidia-headless-530' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535' for glob 'nvidia*'
Note, selecting 'nvidia-driver-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-primus-vk-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-driver-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-headless-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-utils' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-435' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-440' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-450' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-455' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-460' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-465' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-470' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-495' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-510' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-515' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-520' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-525' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-530' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-535' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-435' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-440' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-450' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-455' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-460' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-465' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-470' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-495' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-510' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-515' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-520' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-525' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-530' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535' for glob 'nvidia*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia*'
Note, selecting 'nvidia-driver-410' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418' for glob 'nvidia*'
Note, selecting 'nvidia-driver-430' for glob 'nvidia*'
Note, selecting 'nvidia-driver-435' for glob 'nvidia*'
Note, selecting 'nvidia-driver-440' for glob 'nvidia*'
Note, selecting 'nvidia-driver-450' for glob 'nvidia*'
Note, selecting 'nvidia-driver-455' for glob 'nvidia*'
Note, selecting 'nvidia-driver-460' for glob 'nvidia*'
Note, selecting 'nvidia-driver-465' for glob 'nvidia*'
Note, selecting 'nvidia-driver-470' for glob 'nvidia*'
Note, selecting 'nvidia-driver-495' for glob 'nvidia*'
Note, selecting 'nvidia-driver-510' for glob 'nvidia*'
Note, selecting 'nvidia-driver-515' for glob 'nvidia*'
Note, selecting 'nvidia-driver-520' for glob 'nvidia*'
Note, selecting 'nvidia-driver-525' for glob 'nvidia*'
Note, selecting 'nvidia-driver-530' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-utils-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-primus-vk-wrapper' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless' for glob 'nvidia*'
Note, selecting 'nvidia-utils-430' for glob 'nvidia*'
Note, selecting 'nvidia-utils-435' for glob 'nvidia*'
Note, selecting 'nvidia-utils-440' for glob 'nvidia*'
Note, selecting 'nvidia-utils-450' for glob 'nvidia*'
Note, selecting 'nvidia-utils-455' for glob 'nvidia*'
Note, selecting 'nvidia-utils-460' for glob 'nvidia*'
Note, selecting 'nvidia-utils-465' for glob 'nvidia*'
Note, selecting 'nvidia-utils-470' for glob 'nvidia*'
Note, selecting 'nvidia-utils-495' for glob 'nvidia*'
Note, selecting 'nvidia-utils-510' for glob 'nvidia*'
Note, selecting 'nvidia-utils-515' for glob 'nvidia*'
Note, selecting 'nvidia-utils-520' for glob 'nvidia*'
Note, selecting 'nvidia-utils-525' for glob 'nvidia*'
Note, selecting 'nvidia-utils-530' for glob 'nvidia*'
Note, selecting 'nvidia-utils-535' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-egl-wayland-common' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.146.02' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.146.02' for glob 'nvidia*'
Note, selecting 'nvidia-utils-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-390xx-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.54.03' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-418' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-430' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-435' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-440' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-450' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-455' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-460' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-465' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-470' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-495' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-390xx-smi' for glob 'nvidia*'
Note, selecting 'nvidia-prebuilt-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-510' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-515' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-520' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-525' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-530' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-535' for glob 'nvidia*'
Note, selecting 'nvidia-driver-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils' for glob 'nvidia*'
Note, selecting 'nvidia-driver-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-fs-modules' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-headless-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-515-open' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-390' for glob 'nvidia*'
Note, selecting 'nvidia-fs-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-headless-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-fs-prebuilt-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-460-server' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-418' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-430' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-435' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-440' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-450' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-455' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-460' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-465' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-470' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-495' for glob 'nvidia*'
Note, selecting 'nvidia-cudnn' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-510' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-515' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-520' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-525' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-530' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-535' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.113.01' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-450' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-460' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-470' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-510' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-515' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-525' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-dev-535' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.113.01' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-530-open' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-510-server' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-450' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-460' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-470' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-510' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-515' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-525' for glob 'nvidia*'
Note, selecting 'nvidia-fabricmanager-535' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-utils-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.129.03' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-515-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-440-server' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-418' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-430' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-435' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-440' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-450' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-455' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-460' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-465' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-470' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-495' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-510' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-515' for glob 'nvidia*'
Note, selecting 'nvidia-headless-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535-server' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-520' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-525' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-530' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-535' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-460-server' for glob 'nvidia*'
Note, selecting 'nvidia-driver-520-open' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.129.03' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.104.05' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.104.12' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535-server-open' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.104.05' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.104.12' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-535.86.05' for glob 'nvidia*'
Note, selecting 'nvidia-driver-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-firmware-535-server-535.54.03' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-418-server' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-525-server' for glob 'nvidia*'
Note, selecting 'nvidia-utils-450-server' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-utils-470-server' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-535-open' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-525-open' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-driver-510-server' for glob 'nvidia*'
Package 'nvidia-egl-wayland-common' is not installed, so not removed
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-390' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-driver-410' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-legacy-390xx-opencl-icd' is not installed, so not removed
Package 'nvidia-legacy-390xx-smi' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.113.01' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.146.02' is not installed, so not removed
Package 'nvidia-firmware-535-535.104.12' is not installed, so not removed
Note, selecting 'libnvidia-egl-gbm1' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-410' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-any' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-tesla-cuda1' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-legacy-390xx-egl-wayland1' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-495-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-egl-wayland1' for glob 'libnvidia*'
Note, selecting 'libnvidia-ml1' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode1' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-ml-dev' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-nscq' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-ml.so.1' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-510-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-gl' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-egl-wayland-dev' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-cfg1-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-440-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-390' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-418' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-430' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-435' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-440' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-450' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-455' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-460' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-465' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-470' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-495' for glob 'libnvidia*'
Note, selecting 'libnvidia-encode-460-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-510' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-515' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-520' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-525' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-530' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-535' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-decode' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute' for glob 'libnvidia*'
Note, selecting 'libnvidia-compute-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-515-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-450-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-extra-535-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-418-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-fbc1-525-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-ifr1-470-server' for glob 'libnvidia*'
Note, selecting 'libnvidia-common' for glob 'libnvidia*'
Package 'libnvidia-gl-410' is not installed, so not removed
Package 'libnvidia-legacy-390xx-egl-wayland1' is not installed, so not removed
Package 'libnvidia-encode1' is not installed, so not removed
Package 'libnvidia-tesla-cuda1' is not installed, so not removed
Package 'libnvidia-compute-495-server' is not installed, so not removed
Package 'libnvidia-egl-wayland-dev' is not installed, so not removed
Package 'libnvidia-egl-wayland1' is not installed, so not removed
Package 'nvidia-prime' is not installed, so not removed
Package 'nvidia-settings' is not installed, so not removed
Package 'libnvidia-cfg1-418' is not installed, so not removed
Package 'libnvidia-cfg1-430' is not installed, so not removed
Package 'libnvidia-cfg1-435' is not installed, so not removed
Package 'libnvidia-cfg1-440' is not installed, so not removed
Package 'libnvidia-cfg1-450' is not installed, so not removed
Package 'libnvidia-cfg1-455' is not installed, so not removed
Package 'libnvidia-common-418' is not installed, so not removed
Package 'libnvidia-common-430' is not installed, so not removed
Package 'libnvidia-common-435' is not installed, so not removed
Package 'libnvidia-common-440' is not installed, so not removed
Package 'libnvidia-common-450' is not installed, so not removed
Package 'libnvidia-common-455' is not installed, so not removed
Package 'libnvidia-compute-418' is not installed, so not removed
Package 'libnvidia-compute-430' is not installed, so not removed
Package 'libnvidia-compute-435' is not installed, so not removed
Package 'libnvidia-compute-440' is not installed, so not removed
Package 'libnvidia-compute-450' is not installed, so not removed
Package 'libnvidia-compute-455' is not installed, so not removed
Package 'libnvidia-decode-418' is not installed, so not removed
Package 'libnvidia-decode-430' is not installed, so not removed
Package 'libnvidia-decode-435' is not installed, so not removed
Package 'libnvidia-decode-440' is not installed, so not removed
Package 'libnvidia-decode-450' is not installed, so not removed
Package 'libnvidia-decode-455' is not installed, so not removed
Package 'libnvidia-encode-418' is not installed, so not removed
Package 'libnvidia-encode-430' is not installed, so not removed
Package 'libnvidia-encode-435' is not installed, so not removed
Package 'libnvidia-encode-440' is not installed, so not removed
Package 'libnvidia-encode-450' is not installed, so not removed
Package 'libnvidia-encode-455' is not installed, so not removed
Package 'libnvidia-extra-440' is not installed, so not removed
Package 'libnvidia-extra-450' is not installed, so not removed
Package 'libnvidia-extra-455' is not installed, so not removed
Package 'libnvidia-fbc1-418' is not installed, so not removed
Package 'libnvidia-fbc1-430' is not installed, so not removed
Package 'libnvidia-fbc1-435' is not installed, so not removed
Package 'libnvidia-fbc1-440' is not installed, so not removed
Package 'libnvidia-fbc1-450' is not installed, so not removed
Package 'libnvidia-fbc1-455' is not installed, so not removed
Package 'libnvidia-gl-418' is not installed, so not removed
Package 'libnvidia-gl-430' is not installed, so not removed
Package 'libnvidia-gl-435' is not installed, so not removed
Package 'libnvidia-gl-440' is not installed, so not removed
Package 'libnvidia-gl-450' is not installed, so not removed
Package 'libnvidia-gl-455' is not installed, so not removed
Package 'libnvidia-ifr1-418' is not installed, so not removed
Package 'libnvidia-ifr1-430' is not installed, so not removed
Package 'libnvidia-ifr1-435' is not installed, so not removed
Package 'libnvidia-ifr1-440' is not installed, so not removed
Package 'libnvidia-ifr1-450' is not installed, so not removed
Package 'libnvidia-ifr1-455' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-compute-utils-430' is not installed, so not removed
Package 'nvidia-compute-utils-435' is not installed, so not removed
Package 'nvidia-compute-utils-440' is not installed, so not removed
Package 'nvidia-compute-utils-450' is not installed, so not removed
Package 'nvidia-compute-utils-455' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-dkms-430' is not installed, so not removed
Package 'nvidia-dkms-435' is not installed, so not removed
Package 'nvidia-dkms-440' is not installed, so not removed
Package 'nvidia-dkms-450' is not installed, so not removed
Package 'nvidia-dkms-455' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-driver-430' is not installed, so not removed
Package 'nvidia-driver-435' is not installed, so not removed
Package 'nvidia-driver-440' is not installed, so not removed
Package 'nvidia-driver-450' is not installed, so not removed
Package 'nvidia-driver-455' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-435' is not installed, so not removed
Package 'nvidia-headless-440' is not installed, so not removed
Package 'nvidia-headless-450' is not installed, so not removed
Package 'nvidia-headless-455' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-435' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450' is not installed, so not removed
Package 'nvidia-headless-no-dkms-455' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-common-430' is not installed, so not removed
Package 'nvidia-kernel-common-435' is not installed, so not removed
Package 'nvidia-kernel-common-440' is not installed, so not removed
Package 'nvidia-kernel-common-450' is not installed, so not removed
Package 'nvidia-kernel-common-455' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-kernel-source-430' is not installed, so not removed
Package 'nvidia-kernel-source-435' is not installed, so not removed
Package 'nvidia-kernel-source-440' is not installed, so not removed
Package 'nvidia-kernel-source-450' is not installed, so not removed
Package 'nvidia-kernel-source-455' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
Package 'nvidia-utils-430' is not installed, so not removed
Package 'nvidia-utils-435' is not installed, so not removed
Package 'nvidia-utils-440' is not installed, so not removed
Package 'nvidia-utils-450' is not installed, so not removed
Package 'nvidia-utils-455' is not installed, so not removed
Package 'libnvidia-egl-gbm1' is not installed, so not removed
Package 'libnvidia-ml-dev' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-cuda-toolkit-doc' is not installed, so not removed
Package 'nvidia-cuda-toolkit-gcc' is not installed, so not removed
Package 'nvidia-cudnn' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-primus-vk-common' is not installed, so not removed
Package 'nvidia-primus-vk-wrapper' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'libnvidia-cfg1-390' is not installed, so not removed
Package 'libnvidia-cfg1-418-server' is not installed, so not removed
Package 'libnvidia-cfg1-440-server' is not installed, so not removed
Package 'libnvidia-cfg1-450-server' is not installed, so not removed
Package 'libnvidia-cfg1-460' is not installed, so not removed
Package 'libnvidia-cfg1-460-server' is not installed, so not removed
Package 'libnvidia-cfg1-465' is not installed, so not removed
Package 'libnvidia-cfg1-470' is not installed, so not removed
Package 'libnvidia-cfg1-470-server' is not installed, so not removed
Package 'libnvidia-cfg1-495' is not installed, so not removed
Package 'libnvidia-cfg1-510' is not installed, so not removed
Package 'libnvidia-cfg1-510-server' is not installed, so not removed
Package 'libnvidia-cfg1-515' is not installed, so not removed
Package 'libnvidia-cfg1-515-server' is not installed, so not removed
Package 'libnvidia-cfg1-520' is not installed, so not removed
Package 'libnvidia-cfg1-525' is not installed, so not removed
Package 'libnvidia-cfg1-525-server' is not installed, so not removed
Package 'libnvidia-cfg1-530' is not installed, so not removed
Package 'libnvidia-cfg1-535' is not installed, so not removed
Package 'libnvidia-cfg1-535-server' is not installed, so not removed
Package 'libnvidia-common-390' is not installed, so not removed
Package 'libnvidia-common-418-server' is not installed, so not removed
Package 'libnvidia-common-440-server' is not installed, so not removed
Package 'libnvidia-common-450-server' is not installed, so not removed
Package 'libnvidia-common-460' is not installed, so not removed
Package 'libnvidia-common-460-server' is not installed, so not removed
Package 'libnvidia-common-465' is not installed, so not removed
Package 'libnvidia-common-470' is not installed, so not removed
Package 'libnvidia-common-470-server' is not installed, so not removed
Package 'libnvidia-common-495' is not installed, so not removed
Package 'libnvidia-common-510' is not installed, so not removed
Package 'libnvidia-common-510-server' is not installed, so not removed
Package 'libnvidia-common-515' is not installed, so not removed
Package 'libnvidia-common-515-server' is not installed, so not removed
Package 'libnvidia-common-520' is not installed, so not removed
Package 'libnvidia-common-525' is not installed, so not removed
Package 'libnvidia-common-525-server' is not installed, so not removed
Package 'libnvidia-common-530' is not installed, so not removed
Package 'libnvidia-common-535' is not installed, so not removed
Package 'libnvidia-common-535-server' is not installed, so not removed
Package 'libnvidia-compute-390' is not installed, so not removed
Package 'libnvidia-compute-418-server' is not installed, so not removed
Package 'libnvidia-compute-440-server' is not installed, so not removed
Package 'libnvidia-compute-450-server' is not installed, so not removed
Package 'libnvidia-compute-460' is not installed, so not removed
Package 'libnvidia-compute-460-server' is not installed, so not removed
Package 'libnvidia-compute-465' is not installed, so not removed
Package 'libnvidia-compute-470' is not installed, so not removed. Did you mean 'libnvidia-compute-470:i386'?
Package 'libnvidia-compute-470-server' is not installed, so not removed
Package 'libnvidia-compute-495' is not installed, so not removed
Package 'libnvidia-compute-510' is not installed, so not removed
Package 'libnvidia-compute-510-server' is not installed, so not removed
Package 'libnvidia-compute-515' is not installed, so not removed
Package 'libnvidia-compute-515-server' is not installed, so not removed
Package 'libnvidia-compute-520' is not installed, so not removed
Package 'libnvidia-compute-525' is not installed, so not removed
Package 'libnvidia-compute-525-server' is not installed, so not removed
Package 'libnvidia-compute-530' is not installed, so not removed
Package 'libnvidia-compute-535' is not installed, so not removed
Package 'libnvidia-compute-535-server' is not installed, so not removed
Package 'libnvidia-decode-390' is not installed, so not removed
Package 'libnvidia-decode-418-server' is not installed, so not removed
Package 'libnvidia-decode-440-server' is not installed, so not removed
Package 'libnvidia-decode-450-server' is not installed, so not removed
Package 'libnvidia-decode-460' is not installed, so not removed
Package 'libnvidia-decode-460-server' is not installed, so not removed
Package 'libnvidia-decode-465' is not installed, so not removed
Package 'libnvidia-decode-470' is not installed, so not removed. Did you mean 'libnvidia-decode-470:i386'?
Package 'libnvidia-decode-470-server' is not installed, so not removed
Package 'libnvidia-decode-495' is not installed, so not removed
Package 'libnvidia-decode-510' is not installed, so not removed
Package 'libnvidia-decode-510-server' is not installed, so not removed
Package 'libnvidia-decode-515' is not installed, so not removed
Package 'libnvidia-decode-515-server' is not installed, so not removed
Package 'libnvidia-decode-520' is not installed, so not removed
Package 'libnvidia-decode-525' is not installed, so not removed
Package 'libnvidia-decode-525-server' is not installed, so not removed
Package 'libnvidia-decode-530' is not installed, so not removed
Package 'libnvidia-decode-535' is not installed, so not removed
Package 'libnvidia-decode-535-server' is not installed, so not removed
Package 'libnvidia-encode-390' is not installed, so not removed
Package 'libnvidia-encode-418-server' is not installed, so not removed
Package 'libnvidia-encode-440-server' is not installed, so not removed
Package 'libnvidia-encode-450-server' is not installed, so not removed
Package 'libnvidia-encode-460' is not installed, so not removed
Package 'libnvidia-encode-460-server' is not installed, so not removed
Package 'libnvidia-encode-465' is not installed, so not removed
Package 'libnvidia-encode-470' is not installed, so not removed. Did you mean 'libnvidia-encode-470:i386'?
Package 'libnvidia-encode-470-server' is not installed, so not removed
Package 'libnvidia-encode-495' is not installed, so not removed
Package 'libnvidia-encode-510' is not installed, so not removed
Package 'libnvidia-encode-510-server' is not installed, so not removed
Package 'libnvidia-encode-515' is not installed, so not removed
Package 'libnvidia-encode-515-server' is not installed, so not removed
Package 'libnvidia-encode-520' is not installed, so not removed
Package 'libnvidia-encode-525' is not installed, so not removed
Package 'libnvidia-encode-525-server' is not installed, so not removed
Package 'libnvidia-encode-530' is not installed, so not removed
Package 'libnvidia-encode-535' is not installed, so not removed
Package 'libnvidia-encode-535-server' is not installed, so not removed
Package 'libnvidia-extra-440-server' is not installed, so not removed
Package 'libnvidia-extra-450-server' is not installed, so not removed
Package 'libnvidia-extra-460' is not installed, so not removed
Package 'libnvidia-extra-460-server' is not installed, so not removed
Package 'libnvidia-extra-465' is not installed, so not removed
Package 'libnvidia-extra-470' is not installed, so not removed
Package 'libnvidia-extra-470-server' is not installed, so not removed
Package 'libnvidia-extra-495' is not installed, so not removed
Package 'libnvidia-extra-510' is not installed, so not removed
Package 'libnvidia-extra-510-server' is not installed, so not removed
Package 'libnvidia-extra-515' is not installed, so not removed
Package 'libnvidia-extra-515-server' is not installed, so not removed
Package 'libnvidia-extra-520' is not installed, so not removed
Package 'libnvidia-extra-525' is not installed, so not removed
Package 'libnvidia-extra-525-server' is not installed, so not removed
Package 'libnvidia-extra-530' is not installed, so not removed
Package 'libnvidia-extra-535' is not installed, so not removed
Package 'libnvidia-extra-535-server' is not installed, so not removed
Package 'libnvidia-fbc1-390' is not installed, so not removed
Package 'libnvidia-fbc1-418-server' is not installed, so not removed
Package 'libnvidia-fbc1-440-server' is not installed, so not removed
Package 'libnvidia-fbc1-450-server' is not installed, so not removed
Package 'libnvidia-fbc1-460' is not installed, so not removed
Package 'libnvidia-fbc1-460-server' is not installed, so not removed
Package 'libnvidia-fbc1-465' is not installed, so not removed
Package 'libnvidia-fbc1-470' is not installed, so not removed. Did you mean 'libnvidia-fbc1-470:i386'?
Package 'libnvidia-fbc1-470-server' is not installed, so not removed
Package 'libnvidia-fbc1-495' is not installed, so not removed
Package 'libnvidia-fbc1-510' is not installed, so not removed
Package 'libnvidia-fbc1-510-server' is not installed, so not removed
Package 'libnvidia-fbc1-515' is not installed, so not removed
Package 'libnvidia-fbc1-515-server' is not installed, so not removed
Package 'libnvidia-fbc1-520' is not installed, so not removed
Package 'libnvidia-fbc1-525' is not installed, so not removed
Package 'libnvidia-fbc1-525-server' is not installed, so not removed
Package 'libnvidia-fbc1-530' is not installed, so not removed
Package 'libnvidia-fbc1-535' is not installed, so not removed
Package 'libnvidia-fbc1-535-server' is not installed, so not removed
Package 'libnvidia-gl-390' is not installed, so not removed
Package 'libnvidia-gl-418-server' is not installed, so not removed
Package 'libnvidia-gl-440-server' is not installed, so not removed
Package 'libnvidia-gl-450-server' is not installed, so not removed
Package 'libnvidia-gl-460' is not installed, so not removed
Package 'libnvidia-gl-460-server' is not installed, so not removed
Package 'libnvidia-gl-465' is not installed, so not removed
Package 'libnvidia-gl-470' is not installed, so not removed
Package 'libnvidia-gl-470-server' is not installed, so not removed
Package 'libnvidia-gl-495' is not installed, so not removed
Package 'libnvidia-gl-510' is not installed, so not removed
Package 'libnvidia-gl-510-server' is not installed, so not removed
Package 'libnvidia-gl-515' is not installed, so not removed
Package 'libnvidia-gl-515-server' is not installed, so not removed
Package 'libnvidia-gl-520' is not installed, so not removed
Package 'libnvidia-gl-525' is not installed, so not removed
Package 'libnvidia-gl-525-server' is not installed, so not removed
Package 'libnvidia-gl-530' is not installed, so not removed
Package 'libnvidia-gl-535' is not installed, so not removed
Package 'libnvidia-gl-535-server' is not installed, so not removed
Package 'libnvidia-ifr1-390' is not installed, so not removed
Package 'libnvidia-ifr1-418-server' is not installed, so not removed
Package 'libnvidia-ifr1-440-server' is not installed, so not removed
Package 'libnvidia-ifr1-450-server' is not installed, so not removed
Package 'libnvidia-ifr1-460' is not installed, so not removed
Package 'libnvidia-ifr1-460-server' is not installed, so not removed
Package 'libnvidia-ifr1-465' is not installed, so not removed
Package 'libnvidia-ifr1-470' is not installed, so not removed
Package 'libnvidia-ifr1-470-server' is not installed, so not removed
Package 'libnvidia-nscq-515' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-418-server' is not installed, so not removed
Package 'nvidia-compute-utils-440-server' is not installed, so not removed
Package 'nvidia-compute-utils-450-server' is not installed, so not removed
Package 'nvidia-compute-utils-460' is not installed, so not removed
Package 'nvidia-compute-utils-460-server' is not installed, so not removed
Package 'nvidia-compute-utils-465' is not installed, so not removed
Package 'nvidia-compute-utils-470' is not installed, so not removed
Package 'nvidia-compute-utils-470-server' is not installed, so not removed
Package 'nvidia-compute-utils-495' is not installed, so not removed
Package 'nvidia-compute-utils-510' is not installed, so not removed
Package 'nvidia-compute-utils-510-server' is not installed, so not removed
Package 'nvidia-compute-utils-515' is not installed, so not removed
Package 'nvidia-compute-utils-515-server' is not installed, so not removed
Package 'nvidia-compute-utils-520' is not installed, so not removed
Package 'nvidia-compute-utils-525' is not installed, so not removed
Package 'nvidia-compute-utils-525-server' is not installed, so not removed
Package 'nvidia-compute-utils-530' is not installed, so not removed
Package 'nvidia-compute-utils-535' is not installed, so not removed
Package 'nvidia-compute-utils-535-server' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-418-server' is not installed, so not removed
Package 'nvidia-dkms-440-server' is not installed, so not removed
Package 'nvidia-dkms-450-server' is not installed, so not removed
Package 'nvidia-dkms-460' is not installed, so not removed
Package 'nvidia-dkms-460-server' is not installed, so not removed
Package 'nvidia-dkms-465' is not installed, so not removed
Package 'nvidia-dkms-470' is not installed, so not removed
Package 'nvidia-dkms-470-server' is not installed, so not removed
Package 'nvidia-dkms-495' is not installed, so not removed
Package 'nvidia-dkms-510' is not installed, so not removed
Package 'nvidia-dkms-510-server' is not installed, so not removed
Package 'nvidia-dkms-515' is not installed, so not removed
Package 'nvidia-dkms-515-open' is not installed, so not removed
Package 'nvidia-dkms-515-server' is not installed, so not removed
Package 'nvidia-dkms-520' is not installed, so not removed
Package 'nvidia-dkms-520-open' is not installed, so not removed
Package 'nvidia-dkms-525' is not installed, so not removed
Package 'nvidia-dkms-525-open' is not installed, so not removed
Package 'nvidia-dkms-525-server' is not installed, so not removed
Package 'nvidia-dkms-530' is not installed, so not removed
Package 'nvidia-dkms-530-open' is not installed, so not removed
Package 'nvidia-dkms-535' is not installed, so not removed
Package 'nvidia-dkms-535-open' is not installed, so not removed
Package 'nvidia-dkms-535-server' is not installed, so not removed
Package 'nvidia-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-418-server' is not installed, so not removed
Package 'nvidia-driver-440-server' is not installed, so not removed
Package 'nvidia-driver-450-server' is not installed, so not removed
Package 'nvidia-driver-460' is not installed, so not removed
Package 'nvidia-driver-460-server' is not installed, so not removed
Package 'nvidia-driver-465' is not installed, so not removed
Package 'nvidia-driver-470' is not installed, so not removed
Package 'nvidia-driver-470-server' is not installed, so not removed
Package 'nvidia-driver-495' is not installed, so not removed
Package 'nvidia-driver-510' is not installed, so not removed
Package 'nvidia-driver-510-server' is not installed, so not removed
Package 'nvidia-driver-515' is not installed, so not removed
Package 'nvidia-driver-515-open' is not installed, so not removed
Package 'nvidia-driver-515-server' is not installed, so not removed
Package 'nvidia-driver-520' is not installed, so not removed
Package 'nvidia-driver-520-open' is not installed, so not removed
Package 'nvidia-driver-525' is not installed, so not removed
Package 'nvidia-driver-525-open' is not installed, so not removed
Package 'nvidia-driver-525-server' is not installed, so not removed
Package 'nvidia-driver-530' is not installed, so not removed
Package 'nvidia-driver-530-open' is not installed, so not removed
Package 'nvidia-driver-535' is not installed, so not removed
Package 'nvidia-driver-535-open' is not installed, so not removed
Package 'nvidia-driver-535-server' is not installed, so not removed
Package 'nvidia-driver-535-server-open' is not installed, so not removed
Package 'nvidia-fabricmanager-515' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-515' is not installed, so not removed
Package 'nvidia-firmware-535-535.104.05' is not installed, so not removed
Package 'nvidia-firmware-535-535.113.01' is not installed, so not removed
Package 'nvidia-firmware-535-535.129.03' is not installed, so not removed
Package 'nvidia-firmware-535-535.146.02' is not installed, so not removed
Package 'nvidia-firmware-535-535.54.03' is not installed, so not removed
Package 'nvidia-firmware-535-535.86.05' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.104.05' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.104.12' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.129.03' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.54.03' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-418-server' is not installed, so not removed
Package 'nvidia-headless-440-server' is not installed, so not removed
Package 'nvidia-headless-450-server' is not installed, so not removed
Package 'nvidia-headless-460' is not installed, so not removed
Package 'nvidia-headless-460-server' is not installed, so not removed
Package 'nvidia-headless-465' is not installed, so not removed
Package 'nvidia-headless-470' is not installed, so not removed
Package 'nvidia-headless-470-server' is not installed, so not removed
Package 'nvidia-headless-495' is not installed, so not removed
Package 'nvidia-headless-510' is not installed, so not removed
Package 'nvidia-headless-510-server' is not installed, so not removed
Package 'nvidia-headless-515' is not installed, so not removed
Package 'nvidia-headless-515-open' is not installed, so not removed
Package 'nvidia-headless-515-server' is not installed, so not removed
Package 'nvidia-headless-520' is not installed, so not removed
Package 'nvidia-headless-520-open' is not installed, so not removed
Package 'nvidia-headless-525' is not installed, so not removed
Package 'nvidia-headless-525-open' is not installed, so not removed
Package 'nvidia-headless-525-server' is not installed, so not removed
Package 'nvidia-headless-530' is not installed, so not removed
Package 'nvidia-headless-530-open' is not installed, so not removed
Package 'nvidia-headless-535' is not installed, so not removed
Package 'nvidia-headless-535-open' is not installed, so not removed
Package 'nvidia-headless-535-server' is not installed, so not removed
Package 'nvidia-headless-535-server-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-495' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-common-418-server' is not installed, so not removed
Package 'nvidia-kernel-common-440-server' is not installed, so not removed
Package 'nvidia-kernel-common-450-server' is not installed, so not removed
Package 'nvidia-kernel-common-460' is not installed, so not removed
Package 'nvidia-kernel-common-460-server' is not installed, so not removed
Package 'nvidia-kernel-common-465' is not installed, so not removed
Package 'nvidia-kernel-common-470' is not installed, so not removed
Package 'nvidia-kernel-common-470-server' is not installed, so not removed
Package 'nvidia-kernel-common-495' is not installed, so not removed
Package 'nvidia-kernel-common-510' is not installed, so not removed
Package 'nvidia-kernel-common-510-server' is not installed, so not removed
Package 'nvidia-kernel-common-515' is not installed, so not removed
Package 'nvidia-kernel-common-515-server' is not installed, so not removed
Package 'nvidia-kernel-common-520' is not installed, so not removed
Package 'nvidia-kernel-common-525' is not installed, so not removed
Package 'nvidia-kernel-common-525-server' is not installed, so not removed
Package 'nvidia-kernel-common-530' is not installed, so not removed
Package 'nvidia-kernel-common-535' is not installed, so not removed
Package 'nvidia-kernel-common-535-server' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-kernel-source-418-server' is not installed, so not removed
Package 'nvidia-kernel-source-440-server' is not installed, so not removed
Package 'nvidia-kernel-source-450-server' is not installed, so not removed
Package 'nvidia-kernel-source-460' is not installed, so not removed
Package 'nvidia-kernel-source-460-server' is not installed, so not removed
Package 'nvidia-kernel-source-465' is not installed, so not removed
Package 'nvidia-kernel-source-470' is not installed, so not removed
Package 'nvidia-kernel-source-470-server' is not installed, so not removed
Package 'nvidia-kernel-source-495' is not installed, so not removed
Package 'nvidia-kernel-source-510' is not installed, so not removed
Package 'nvidia-kernel-source-510-server' is not installed, so not removed
Package 'nvidia-kernel-source-515' is not installed, so not removed
Package 'nvidia-kernel-source-515-open' is not installed, so not removed
Package 'nvidia-kernel-source-515-server' is not installed, so not removed
Package 'nvidia-kernel-source-520' is not installed, so not removed
Package 'nvidia-kernel-source-520-open' is not installed, so not removed
Package 'nvidia-kernel-source-525' is not installed, so not removed
Package 'nvidia-kernel-source-525-open' is not installed, so not removed
Package 'nvidia-kernel-source-525-server' is not installed, so not removed
Package 'nvidia-kernel-source-530' is not installed, so not removed
Package 'nvidia-kernel-source-530-open' is not installed, so not removed
Package 'nvidia-kernel-source-535' is not installed, so not removed
Package 'nvidia-kernel-source-535-open' is not installed, so not removed
Package 'nvidia-kernel-source-535-server' is not installed, so not removed
Package 'nvidia-kernel-source-535-server-open' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-utils-418-server' is not installed, so not removed
Package 'nvidia-utils-440-server' is not installed, so not removed
Package 'nvidia-utils-450-server' is not installed, so not removed
Package 'nvidia-utils-460' is not installed, so not removed
Package 'nvidia-utils-460-server' is not installed, so not removed
Package 'nvidia-utils-465' is not installed, so not removed
Package 'nvidia-utils-470' is not installed, so not removed
Package 'nvidia-utils-470-server' is not installed, so not removed
Package 'nvidia-utils-495' is not installed, so not removed
Package 'nvidia-utils-510' is not installed, so not removed
Package 'nvidia-utils-510-server' is not installed, so not removed
Package 'nvidia-utils-515' is not installed, so not removed
Package 'nvidia-utils-515-server' is not installed, so not removed
Package 'nvidia-utils-520' is not installed, so not removed
Package 'nvidia-utils-525' is not installed, so not removed
Package 'nvidia-utils-525-server' is not installed, so not removed
Package 'nvidia-utils-530' is not installed, so not removed
Package 'nvidia-utils-535' is not installed, so not removed
Package 'nvidia-utils-535-server' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'libnvidia-nscq-450' is not installed, so not removed
Package 'libnvidia-nscq-460' is not installed, so not removed
Package 'libnvidia-nscq-470' is not installed, so not removed
Package 'libnvidia-nscq-510' is not installed, so not removed
Package 'libnvidia-nscq-525' is not installed, so not removed
Package 'libnvidia-nscq-535' is not installed, so not removed
Package 'nvidia-fabricmanager-450' is not installed, so not removed
Package 'nvidia-fabricmanager-460' is not installed, so not removed
Package 'nvidia-fabricmanager-470' is not installed, so not removed
Package 'nvidia-fabricmanager-510' is not installed, so not removed
Package 'nvidia-fabricmanager-525' is not installed, so not removed
Package 'nvidia-fabricmanager-535' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-450' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-460' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-470' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-510' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-525' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-535' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386
  libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386 libnvidia-compute-470:i386 libnvidia-decode-470:i386
  libnvidia-encode-470:i386 libnvidia-fbc1-470:i386 libpciaccess0:i386 libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0 libxshmfence1:i386
  libxxf86vm1:i386 linux-headers-6.2.0-37-generic linux-hwe-6.2-headers-6.2.0-37 linux-image-6.2.0-37-generic linux-modules-6.2.0-37-generic linux-modules-extra-6.2.0-37-generic
  linux-objects-nvidia-470-6.2.0-37-generic linux-signatures-nvidia-6.2.0-37-generic pkg-config screen-resolution-extra
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.

```

"Add a few edits to your Grub Menu so it's easier to work with during this"
```

root@ubuntu:/# sudo vi /etc/default/grub

```

Make these edits
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=show
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid nomodeset"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1928X1000X24

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

```

"Pick up the changes"
```

root@ubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
done

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

```

---

### Post by kotgc on 2024-01-16
"Uninstall the 6.5 kernel, which does not work for your GPU right now..."
1/4
```

root@ubuntu:/# sudo apt remove --purge --yes  linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic  linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'linux-headers-6.5.0-14-generic' is not installed, so not removed
Package 'linux-image-6.5.0-14-generic' is not installed, so not removed
Package 'linux-modules-6.5.0-14-generic' is not installed, so not removed
Package 'linux-modules-extra-6.5.0-14-generic' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386  libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386
  libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386  libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386  libnvidia-compute-470:i386 libnvidia-decode-470:i386
  libnvidia-encode-470:i386 libnvidia-fbc1-470:i386 libpciaccess0:i386  libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386  libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0  libxshmfence1:i386
  libxxf86vm1:i386 linux-headers-6.2.0-37-generic  linux-hwe-6.2-headers-6.2.0-37 linux-image-6.2.0-37-generic  linux-modules-6.2.0-37-generic linux-modules-extra-6.2.0-37-generic
  linux-objects-nvidia-470-6.2.0-37-generic linux-signatures-nvidia-6.2.0-37-generic pkg-config screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 41 not to upgrade.

```

2/4
```

root@ubuntu:/# sudo apt remove --purge  --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic  linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'linux-headers-6.5.0-14-generic' is not installed, so not removed
Package 'linux-image-6.5.0-14-generic' is not installed, so not removed
Package 'linux-modules-6.5.0-14-generic' is not installed, so not removed
Package 'linux-modules-extra-6.5.0-14-generic' is not installed, so not removed
The following packages were automatically installed and are no longer required:
   dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386  libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386
  libgl1:i386  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386  libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386  libnvidia-compute-470:i386 libnvidia-decode-470:i386
   libnvidia-encode-470:i386 libnvidia-fbc1-470:i386 libpciaccess0:i386  libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
   libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386  libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0  libxshmfence1:i386
  libxxf86vm1:i386 linux-headers-6.2.0-37-generic  linux-hwe-6.2-headers-6.2.0-37 linux-image-6.2.0-37-generic  linux-modules-6.2.0-37-generic linux-modules-extra-6.2.0-37-generic
  linux-objects-nvidia-470-6.2.0-37-generic linux-signatures-nvidia-6.2.0-37-generic pkg-config screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 41 not to upgrade.
root@ubuntu:/#  sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic  linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic  linux-modules-extra-6.2.0-39-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
   dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386  libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386
  libgl1:i386  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386  libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386  libnvidia-compute-470:i386 libnvidia-decode-470:i386
   libnvidia-encode-470:i386 libnvidia-fbc1-470:i386 libpciaccess0:i386  libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
   libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386  libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0  libxshmfence1:i386
  libxxf86vm1:i386 linux-headers-6.2.0-37-generic  linux-hwe-6.2-headers-6.2.0-37 linux-image-6.2.0-37-generic  linux-modules-6.2.0-37-generic linux-modules-extra-6.2.0-37-generic
  linux-objects-nvidia-470-6.2.0-37-generic linux-signatures-nvidia-6.2.0-37-generic pkg-config screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 4 to reinstall, 0 to remove and 41 not to upgrade.
Need to get 116 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1  http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64  linux-headers-6.2.0-39-generic amd64 6.2.0-39.40~22.04.1 [3,392 kB]
Get:2  http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64  linux-image-6.2.0-39-generic amd64 6.2.0-39.40~22.04.1 [13.6  MB]                                                                         
Get:3 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64  linux-modules-6.2.0-39-generic amd64 6.2.0-39.40~22.04.1 [25.8  MB]                                                                      
Get:4  http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64  linux-modules-extra-6.2.0-39-generic amd64 6.2.0-39.40~22.04.1 [73.4  MB]                                                                
Fetched  116 MB in 1min 27s (1,333  kB/s)                                                                                                                                                                     
(Reading database ... 256663 files and directories currently installed.)
Preparing to unpack .../linux-headers-6.2.0-39-generic_6.2.0-39.40~22.04.1_amd64.deb ...
Unpacking linux-headers-6.2.0-39-generic (6.2.0-39.40~22.04.1) over (6.2.0-39.40~22.04.1) ...
Preparing to unpack .../linux-image-6.2.0-39-generic_6.2.0-39.40~22.04.1_amd64.deb ...
Unpacking linux-image-6.2.0-39-generic (6.2.0-39.40~22.04.1) over (6.2.0-39.40~22.04.1) ...
Preparing to unpack .../linux-modules-6.2.0-39-generic_6.2.0-39.40~22.04.1_amd64.deb ...
Unpacking linux-modules-6.2.0-39-generic (6.2.0-39.40~22.04.1) over (6.2.0-39.40~22.04.1) ...
Preparing to unpack .../linux-modules-extra-6.2.0-39-generic_6.2.0-39.40~22.04.1_amd64.deb ...
Unpacking linux-modules-extra-6.2.0-39-generic (6.2.0-39.40~22.04.1) over (6.2.0-39.40~22.04.1) ...
Setting up linux-modules-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
Setting up linux-headers-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-39-generic
   ...done.
Setting up linux-image-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
Setting up linux-modules-extra-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
Processing triggers for linux-image-6.2.0-39-generic (6.2.0-39.40~22.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-39-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.2.0-39-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
done

```

3/4
```

root@ubuntu:/#  sudo apt install --yes linux-headers-6.2.0-26-generic  linux-image-6.2.0-26-generic linux-modules-6.2.0-26-generic  linux-modules-extra-6.2.0-26-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
linux-headers-6.2.0-26-generic is already the newest version (6.2.0-26.26~22.04.1).
linux-image-6.2.0-26-generic is already the newest version (6.2.0-26.26~22.04.1).
linux-modules-6.2.0-26-generic is already the newest version (6.2.0-26.26~22.04.1).
linux-modules-extra-6.2.0-26-generic is already the newest version (6.2.0-26.26~22.04.1).
The following packages were automatically installed and are no longer required:
   dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386  libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386
  libgl1:i386  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386  libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386  libnvidia-compute-470:i386 libnvidia-decode-470:i386
   libnvidia-encode-470:i386 libnvidia-fbc1-470:i386 libpciaccess0:i386  libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
   libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386  libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0  libxshmfence1:i386
  libxxf86vm1:i386 linux-headers-6.2.0-37-generic  linux-hwe-6.2-headers-6.2.0-37 linux-image-6.2.0-37-generic  linux-modules-6.2.0-37-generic linux-modules-extra-6.2.0-37-generic
  linux-objects-nvidia-470-6.2.0-37-generic linux-signatures-nvidia-6.2.0-37-generic pkg-config screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 41 not to upgrade.
root@ubuntu:/# 

```

4/4
```

root@ubuntu:/#  sudo apt-mark hold linux-headers-6.2.0-39-generic  linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic  linux-modules-extra-6.2.0-39-generic
linux-headers-6.2.0-39-generic set on hold.
linux-image-6.2.0-39-generic set on hold.
linux-modules-6.2.0-39-generic set on hold.
linux-modules-extra-6.2.0-39-generic set on hold.

```

---

### Post by kotgc on 2024-01-16
"Exit the chroot"
```

root@ubuntu:/mnt# umount /mnt
umount: /mnt: target is busy.
root@ubuntu:/mnt# lsof /dev/sda2 
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/999/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.portal file system /run/user/999/doc
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /mnt/run/user/999/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.portal file system /mnt/run/user/999/doc
      Output information may be incomplete.
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
bash     9709 root  cwd    DIR    8,2     4096    2 /mnt
lsof    20946 root  cwd    DIR    8,2     4096    2 /mnt
lsof    20947 root  cwd    DIR    8,2     4096    2 /mnt
root@ubuntu:/mnt# kill -9 9709
Killed
ubuntu@ubuntu:~$ reboot

```

---

### Post by kotgc on 2024-01-16
After a few more tests of your code and reboots, Ubuntu shows what you were calling Grub2 in post #62.
This black boot screen with white text appears briefly:

                                     GNU GRUB version 2.06
--------------------------------------------------------------------------------------------------------
| *Ubuntu (highlighted white)
|  Advanced options for Ubuntu
|  UEFI Firmware Settings
|
|
|
|
|
|
|
--------------------------------------------------------------------------------------------------------
      
Use the ^ and v keys to select which entry is highlighted.
      Press enter to boot the selected OS, 'e' to edit the commands
      before booting or 'c' for a command-line. ESC to return previous
      menu.
The highlighted entry will be executed automatically in 1s.

---

### Post by MAFoElffen on 2024-01-16
What kernels does it say you have as options to boot from under the menu Option "Advanced options for Ubuntu"?

---

### Post by kotgc on 2024-01-16
Similar to post #51 (with the new addition of lines 5 and 6):
*Ubuntu, with Linux 6.2.0-39-generic
  Ubuntu, with Linux 6.2.0-39-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-37-generic
  Ubuntu, with Linux 6.2.0-37-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-26-generic
  Ubuntu, with Linux 6.2.0-26-generic (recovery mode)

---

### Post by MAFoElffen on 2024-01-16
And what happens if you boot from 6.2.0-26 (Which is the same kernel version as your LiveUSB, which displays for you when booted from that?

---

### Post by kotgc on 2024-01-16
Ubuntu, with Linux 6.2.0-26-generic boots through dmesg, the loading screen, then black screen.
Ubuntu, with Linux 6.2.0-26-generic (recovery mode) boots to text menu, then selecting resume boots to black screen with a blinking underscore in the top left.

---

### Post by MAFoElffen on 2024-01-16
There is something wrong there, possibly in the foundation of the graphics layer... That should be the same as what it would be in the LiveUSB.

What happens if you chroot into the installed system and do?
```

sudo apt update
sudo apt install --reinstall ubuntu-desktop xserver-xorg-core linux-generic

```

---

### Post by kotgc on 2024-01-16
```
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# mount /dev/sda2 /mnt/
root@ubuntu:~# mount --make-private --rbind /dev/ /mnt/dev/
root@ubuntu:~# mount --make-private --rbind /proc/ /mnt/proc/
root@ubuntu:~# mount --make-private --rbind /sys/ /mnt/sys/
root@ubuntu:~# mount --make-private --rbind /run/ /mnt/run/
root@ubuntu:~# cd /mnt/
root@ubuntu:/mnt# chroot /mnt/ /bin/bash --login
root@ubuntu:/# mount -a
root@ubuntu:/# apt update 
Running in chroot, ignoring command 'start'
Hit:1 http://au.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://au.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                           
Hit:3 http://au.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                                     
Get:4 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [1,280 kB]                                                                    
Get:5 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                                                                            
Get:6 http://au.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [550 kB]                                                                                               
Get:7 http://au.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [262 kB]                                                                                                                   
Get:8 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [1,276 kB]                                                                                                                 
Get:9 http://au.archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [208 kB]                                                                                                               
Get:10 http://au.archive.ubuntu.com/ubuntu jammy-updates/multiverse i386 Packages [4,184 B]                                                                            
Get:11 http://au.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [42.1 kB]                                                           
Hit:12 https://ppa.launchpadcontent.net/obsproject/obs-studio/ubuntu jammy InRelease                                                                                     
Get:13 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [827 kB]
Hit:14 https://apt.syncthing.net syncthing InRelease    
Get:15 http://security.ubuntu.com/ubuntu jammy-security/universe i386 Packages [583 kB]
Get:16 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [157 kB]
Fetched 5,417 kB in 3s (1,727 kB/s)                              
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
42 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@ubuntu:/# apt install --reinstall ubuntu-desktop xserver-xorg-core linux-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi8:i386 libgl1:i386
  libgl1-mesa-dri:i386 libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm15:i386 libmd0:i386 libnvidia-compute-470:i386 libnvidia-decode-470:i386 libnvidia-encode-470:i386
  libnvidia-fbc1-470:i386 libpciaccess0:i386 libsensors5:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-randr0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0 libxshmfence1:i386 libxxf86vm1:i386
  linux-headers-6.2.0-37-generic linux-hwe-6.2-headers-6.2.0-37 linux-image-6.2.0-37-generic linux-modules-6.2.0-37-generic linux-modules-extra-6.2.0-37-generic linux-objects-nvidia-470-6.2.0-37-generic
  linux-signatures-nvidia-6.2.0-37-generic pkg-config screen-resolution-extra
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-5.15.0-91 linux-headers-5.15.0-91-generic linux-headers-generic linux-image-5.15.0-91-generic linux-image-generic linux-modules-5.15.0-91-generic linux-modules-extra-5.15.0-91-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-headers-5.15.0-91 linux-headers-5.15.0-91-generic linux-headers-generic linux-image-5.15.0-91-generic linux-image-generic linux-modules-5.15.0-91-generic
  linux-modules-extra-5.15.0-91-generic
0 upgraded, 8 newly installed, 2 reinstalled, 0 to remove and 42 not upgraded.
Need to get 114 MB of archives.
After this operation, 582 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-modules-5.15.0-91-generic amd64 5.15.0-91.101 [22.5 MB]
Get:2 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-5.15.0-91-generic amd64 5.15.0-91.101 [11.5 MB]
Get:3 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-modules-extra-5.15.0-91-generic amd64 5.15.0-91.101 [63.8 MB]
Get:4 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-generic amd64 5.15.0.91.88 [2,488 B]
Get:5 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-5.15.0-91 all 5.15.0-91.101 [12.3 MB]
Get:6 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-5.15.0-91-generic amd64 5.15.0-91.101 [2,860 kB]
Get:7 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-generic amd64 5.15.0.91.88 [2,342 B]
Get:8 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-generic amd64 5.15.0.91.88 [1,700 B]
Get:9 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 ubuntu-desktop amd64 1.481.1 [2,604 B]
Get:10 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 xserver-xorg-core amd64 2:21.1.4-2ubuntu1.7~22.04.5 [1,476 kB]
Fetched 114 MB in 4s (27.3 MB/s)              
Selecting previously unselected package linux-modules-5.15.0-91-generic.
(Reading database ... 256663 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.15.0-91-generic_5.15.0-91.101_amd64.deb ...
Unpacking linux-modules-5.15.0-91-generic (5.15.0-91.101) ...
Selecting previously unselected package linux-image-5.15.0-91-generic.
Preparing to unpack .../1-linux-image-5.15.0-91-generic_5.15.0-91.101_amd64.deb ...
Unpacking linux-image-5.15.0-91-generic (5.15.0-91.101) ...
Selecting previously unselected package linux-modules-extra-5.15.0-91-generic.
Preparing to unpack .../2-linux-modules-extra-5.15.0-91-generic_5.15.0-91.101_amd64.deb ...
Unpacking linux-modules-extra-5.15.0-91-generic (5.15.0-91.101) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../3-linux-image-generic_5.15.0.91.88_amd64.deb ...
Unpacking linux-image-generic (5.15.0.91.88) ...
Selecting previously unselected package linux-headers-5.15.0-91.
Preparing to unpack .../4-linux-headers-5.15.0-91_5.15.0-91.101_all.deb ...
Unpacking linux-headers-5.15.0-91 (5.15.0-91.101) ...
Selecting previously unselected package linux-headers-5.15.0-91-generic.
Preparing to unpack .../5-linux-headers-5.15.0-91-generic_5.15.0-91.101_amd64.deb ...
Unpacking linux-headers-5.15.0-91-generic (5.15.0-91.101) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../6-linux-headers-generic_5.15.0.91.88_amd64.deb ...
Unpacking linux-headers-generic (5.15.0.91.88) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../7-linux-generic_5.15.0.91.88_amd64.deb ...
Unpacking linux-generic (5.15.0.91.88) ...
Preparing to unpack .../8-ubuntu-desktop_1.481.1_amd64.deb ...
Unpacking ubuntu-desktop (1.481.1) over (1.481.1) ...
Preparing to unpack .../9-xserver-xorg-core_2%3a21.1.4-2ubuntu1.7~22.04.5_amd64.deb ...
Unpacking xserver-xorg-core (2:21.1.4-2ubuntu1.7~22.04.5) over (2:21.1.4-2ubuntu1.7~22.04.5) ...
Setting up ubuntu-desktop (1.481.1) ...
Setting up xserver-xorg-core (2:21.1.4-2ubuntu1.7~22.04.5) ...
Setting up linux-headers-5.15.0-91 (5.15.0-91.101) ...
Setting up linux-headers-5.15.0-91-generic (5.15.0-91.101) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-91-generic
   ...done.
Setting up linux-headers-generic (5.15.0.91.88) ...
Setting up linux-image-5.15.0-91-generic (5.15.0-91.101) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-6.2.0-26-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-6.2.0-26-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.15.0-91-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-91-generic
Setting up linux-modules-extra-5.15.0-91-generic (5.15.0-91.101) ...
Setting up linux-image-generic (5.15.0.91.88) ...
Setting up linux-modules-5.15.0-91-generic (5.15.0-91.101) ...
Setting up linux-generic (5.15.0.91.88) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for linux-image-5.15.0-91-generic (5.15.0-91.101) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-91-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-91-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-39-generic
Found initrd image: /boot/initrd.img-6.2.0-39-generic
Found linux image: /boot/vmlinuz-6.2.0-37-generic
Found initrd image: /boot/initrd.img-6.2.0-37-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Found linux image: /boot/vmlinuz-5.15.0-91-generic
Found initrd image: /boot/initrd.img-5.15.0-91-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
done
root@ubuntu:/# umount /mnt
umount: /mnt: not mounted.
root@ubuntu:/# reboot
Running in chroot, ignoring request.

```

---

### Post by BicyclerBoy on 2024-01-16
Interesting that OS prober is finding kernels 6.2.0-26 6.2.0-37 & 6.2.0-39 after you just un-installed 6.2.0-37.

Do you have another installed system with /boot folder & multiple linux kernel images?

It could be you have been booting into a different install than the above chroot (sda2).

---

### Post by kotgc on 2024-01-16
I'm not aware of another installed system with /boot folder & multiple linux kernel images?
3 other storage SSD 120GB disks have been physically disconnected.
There's only 1 SSD 240GB disk physically connected to the MOBO.

---

### Post by MAFoElffen on 2024-01-16
He removed kernel 6.5.0-14... He had 6.2.0-39 & 6.2.0-37. I had him install 6.2.0-26, as that was what he said he had on the LiveUSB that worked...

I'm a little wary of having him reinstall linux-generic-hwe-22.04 yet. I'm not positive what that will do if you have an HWE kernel pinned, and I'd like to test that to see what it actually does do (good or bad) before I ask someone else to do that. I try not to have others do something that I am not sure about.

The 2 errors at the end were because you didn't escape out of the chroot via 'exit' before doing the umount & reboot commands. Nothing major there.

Did you reboot and test it yet?

---

### Post by kotgc on 2024-01-16
As per post #74, I am unable to exit chroot.

---

### Post by MAFoElffen on 2024-01-16
I don't see anywhere in your output where you typed the word "exit"... Try that first
```

[COLOR=#ff0000]exit[/COLOR]
umount /mnt
reboot

```

---

### Post by kotgc on 2024-01-16
```

umount: /mnt: not mounted.
root@ubuntu:/# exit
logout
root@ubuntu:/mnt# unmount /mnt/
Command 'unmount' not found, did you mean:
  command 'umount' from deb mount (2.37.2-4ubuntu3)
Try: apt install <deb name>
root@ubuntu:/mnt# umount /mnt
umount: /mnt: target is busy.
root@ubuntu:/# reboot

```

---

### Post by kotgc on 2024-01-16
Reboot worked.
Ubuntu still has a black screen.
Selecting Advanced options for Ubuntu shows:

*Ubuntu, with Linux 6.2.0-39-generic
  Ubuntu, with Linux 6.2.0-39-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-37-generic
  Ubuntu, with Linux 6.2.0-37-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-26-generic
  Ubuntu, with Linux 6.2.0-26-generic (recovery mode)
Ubuntu, with Linux 5.15.0-91-generic <- this boots through dmesg and shows a black screen with the ASRock and Ubuntu logos.
Ubuntu, with Linux 5.15.0-91-generic (recovery mode) <- this boots to the text menu -> I select resume -> boots to black screen with a blinking underscore in the top left.

---

### Post by BicyclerBoy on 2024-01-16
Sorry. I now see you did **not** run apt autoremove or "apt-get autoremove" in the chroot.

---

### Post by kotgc on 2024-01-16
Am I doing something wrong? I'm trying to follow the code instructions.
I think you're referring to post #75, which in turn is referring to post #74. My understanding in post #74 is to run the code suggested in post #73, which I show output in post #74.

---

### Post by BicyclerBoy on 2024-01-16
My post #82 was to answer my question in post #75..
(why were all these kernels showing in grub's OS-prober?)

I assumed you would be removing the known problem kernel packages/images. But that was not the provided instruction..

There seems to be lots of "Black Screen" issues appearing in these forums..

---

### Post by kotgc on 2024-01-16
Ok, I just wanted to be clear I haven't missed anything.
I don't know if this has anything to do with Ubuntu changing from X to Wayland, but it's an incredible waste of time and resources.
Thanks to all those volunteering their time to help, but I hope the issue can be solved so others can avoid this persistent and still is black screen issue.

---

### Post by MAFoElffen on 2024-01-16
This was before you reinstalled ubuntu-desktop & XServer...
> **kotgc said:**
> 
Selecting Advanced options for Ubuntu shows:

*Ubuntu, with Linux 6.2.0-39-generic
  Ubuntu, with Linux 6.2.0-39-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-37-generic
  Ubuntu, with Linux 6.2.0-37-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-26-generic
  Ubuntu, with Linux 6.2.0-26-generic (recovery mode)
Ubuntu, with Linux 5.15.0-91-generic 
Ubuntu, with Linux 5.15.0-91-generic (recovery mode) 

That last post was from booting from 6.2.0-39 right? Have you tried all the others again?
```

6.2.0-37-generic
6.2.0-37-generic (recovery mode)
  
6.2.0-26-generic
6.2.0-26-generic (recovery mode)

5.15.0-91-generic 
5.15.0-91-generic (recovery mode) 

```
If that does not work, the next step is going to be to a backup, then a non-destructive reinstall of the system.

*** You said that it goes to the Desktop fine with the 22.04.3 Installer LiveUSB running kernel 6.2.0-26-generic running Nouveau...

We have done everything else.

---

### Post by kotgc on 2024-01-16
Yes, all have been selected for boot.

*Ubuntu, with Linux 6.2.0-39-generic
  Ubuntu, with Linux 6.2.0-39-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-37-generic
  Ubuntu, with Linux 6.2.0-37-generic (recovery mode)
  Ubuntu, with Linux 6.2.0-26-generic
  Ubuntu, with Linux 6.2.0-26-generic (recovery mode)
Ubuntu, with Linux 5.15.0-91-generic -> this one is most successful, however sits on a black screen with the ASRock and Ubuntu logos on all 3 monitors and doesn't complete the boot.
Ubuntu, with Linux 5.15.0-91-generic (recovery mode)

---

### Post by MAFoElffen on 2024-01-16
Do a good backup. Make sure you have a copy of the fstab. Run the 'system-info' script from my signature line > Choose to upload the report to a pastebin.

Those steps abpve are for the just-in-cases...

I have done this with good success. guiverc has done the same and written a good writeup about it [HERE]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533").

Basically, you research and try to undertsand how the pieces of your installed system is put together before you start... When you have that down,then Install > Choose "other" to get into the manual partitioner > In the partitoner, choose the partitions & "select change". In the change dialog, "DO NOT SELECT FORMAT", In "Use As", you point to the mountpoints, where they should be...

For example in /dev/sda2 is your "/"... If there is a seprate Home, then point that to "Use As" '/home', etc. In the bottom, you point to where your EFI partition is... Then continue.

In the UserData, you fill out the same options you had. Continue with the install.

It will write the new system into the old system, overwriting the base system, which keeping everything there.

The 'system-info' report is used as a tool to figure out how that is laid out, and if one of the User Installed applications, for some reason needs to be reinstalled, that list of those is in that report. That should make that simple, if needed.

---

### Post by kotgc on 2024-01-16
How do I do a backup with a black screen? I'm not sure I can access whatever files from LiveUSB? Searches aren't showing clear enough instructions for me.
Then I might be able to figure the rest of post #88 out.

---

### Post by MAFoElffen on 2024-01-16
Deja Dup is the default installed backup software, that is also already on the Installer LiveUSB's. Nothing extra to install.

Tutorial: [How To Backup And Restore Files Using Deja Dup In Linux]("https://ostechnix.com/how-to-backup-and-restore-files-using-deja-dup-in-linux/#google_vignette")

YouTube Video: [Ubuntu's Backup Solution (Déjà Dup)]("https://www.youtube.com/watch?v=FhPkMEyL3ao")

There are two others that I might consider for "New To Backups" Users... which would be Clonezilla or TimeShift.

I use scripts using either rdiff-backup or rsync. But those are all commandline tools.

---

### Post by kotgc on 2024-01-16
I guess I need to mount the disk to be backed up: /dev/sda2. I reconnected 1 of the 3 disconnected storage disks.
I guess I need to mount the disk to store the back up: /dev/sdb1.
I'm not sure if I can mount /dev/sda2 and /dev/sdb1 to /mnt? Could someone clarify my command, as I am a bit confused? (I haven't pressed Enter on the last line of the code below).
Then, I plan to use rsync as per [https://ostechnix.com/backup-entire-linux-system-using-rsync/#google_vignette:](https://ostechnix.com/backup-entire-linux-system-using-rsync/#google_vignette:)
```

ubuntu@ubuntu:~$ which rsync
/usr/bin/rsync
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 3.02 GiB, 3241230336 bytes, 6330528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 237.21 MiB, 248729600 bytes, 485800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: INTEL SSDSC2KW24
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F67B32DF-306B-4B7B-B8D3-EB99025AEC95

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 468860927 467810304 223.1G Linux filesystem


Disk /dev/sdb: 111.79 GiB, 120034123776 bytes, 234441648 sectors
Disk model: INTEL SSDSC2BW12
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 480BBA39-4051-4EDA-939B-28AEEC589F50

Device     Start       End   Sectors   Size Type
/dev/sdb1   2048 234440703 234438656 111.8G Linux filesystem


Disk /dev/sdc: 14.44 GiB, 15506341888 bytes, 30285824 sectors
Disk model: TOSHIBA USB DRV 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0

Device       Start      End  Sectors  Size Type
/dev/sdc1       64  9828451  9828388  4.7G Microsoft basic data
/dev/sdc2  9828452  9838519    10068  4.9M EFI System
/dev/sdc3  9838520  9839119      600  300K Microsoft basic data
/dev/sdc4  9842688 30285760 20443073  9.7G Linux filesystem


Disk /dev/loop8: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 53.26 MiB, 55844864 bytes, 109072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/
ubuntu@ubuntu:~$ $ sudo rsync -aAXv / --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} /mnt

```

---

### Post by BicyclerBoy on 2024-01-16
If you going to reinstall then leave the storage disks UNCONNECTED.
Only your /home folder(s) really matter and maybe the content of /etc/fstab 

**AND any database files !!**

I use a summary sheet with each PC with disk info: 
$ lsblk -o name, label,fstype,UUID,mountpoint 
and 
$ df -h

and copy of /etc/fstab etc
Note the UUIDs (& potentially others) change if formatting partitions.

You can install without formatting partitions but with the problems you have it may be best to re-format the system "/" partition.

---

### Post by kotgc on 2024-01-16
Yes, I will only have 1 disk connected for the rescue.
Right now I'm before the rescue step, and need storage to save the backup of /dev/sda.

Checking storage disk is empty:
```

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0    7:0    0     3G  1 loop /rofs
loop1    7:1    0     4K  1 loop /snap/bare/5
loop2    7:2    0  63.4M  1 loop /snap/core20/1974
loop3    7:3    0  73.9M  1 loop /snap/core22/858
loop4    7:4    0 237.2M  1 loop /snap/firefox/2987
loop5    7:5    0 485.5M  1 loop /snap/gnome-42-2204/120
loop6    7:6    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop7    7:7    0 349.7M  1 loop /snap/gnome-3-38-2004/143
loop8    7:8    0  12.3M  1 loop /snap/snap-store/959
loop9    7:9    0  53.3M  1 loop /snap/snapd/19457
loop10   7:10   0   452K  1 loop /snap/snapd-desktop-integration/83
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part 
&#9492;&#9472;sda2   8:2    0 223.1G  0 part 
sdb      8:16   0 111.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 111.8G  0 part /mnt
sdc      8:32   1  14.4G  0 disk 
&#9500;&#9472;sdc1   8:33   1   4.7G  0 part /cdrom
&#9500;&#9472;sdc2   8:34   1   4.9M  0 part 
&#9500;&#9472;sdc3   8:35   1   300K  0 part 
&#9492;&#9472;sdc4   8:36   1   9.7G  0 part /var/crash
                                 /var/log

```

Checking root location of Ubuntu OS disk:
```

ubuntu@ubuntu:~$ ls -la /mnt/
total 0
drwxr-xr-x 2 root root   3 Aug  7 22:52 .
drwxr-xr-x 1 root root 220 Jan 17 06:46 ..
ubuntu@ubuntu:~$ mount |grep /mnt/
ubuntu@ubuntu:~$ sudo mount /dev/sda2 Documents/ && sudo du -h Documents/ | sort -nr | head
1020K    Documents/var/snap/brave/common
1020K    Documents/usr/lib/modules/5.15.0-91-generic/kernel/drivers/media/test-drivers
1020K    Documents/usr/lib/libreoffice/program/types
1020K    Documents/home/ubuntu/.logseq/plugins/logseq-kanban-board/dist
1016K    Documents/var/snap/brave/common/fontconfig
1016K    Documents/var/lib/flatpak/runtime/org.kde.Platform/x86_64/5.15-23.08/726e8b743596ab79235396e44d062cfd8d49111bf3273e8e5f5b02122876dda6/files/share/plasma/desktoptheme/air
1016K    Documents/var/lib/flatpak/runtime/org.kde.Platform/x86_64/5.15-23.08/726e8b743596ab79235396e44d062cfd8d49111bf3273e8e5f5b02122876dda6/files/share/icons/breeze-dark/mimetypes/32
1016K    Documents/usr/src/linux-headers-5.15.0-91/arch/ia64
1016K    Documents/usr/share/icons/Adwaita/48x48
1016K    Documents/usr/lib/python3/dist-packages/DistUpgrade
ubuntu@ubuntu:~$ sudo umount /dev/sda2 && sudo mount /dev/sda1 Documents/ && sudo du -h Documents/ | sort -nr
7.0M    Documents/EFI
7.0M    Documents/
4.3M    Documents/EFI/ubuntu
2.8M    Documents/EFI/BOOT

```

---

### Post by MAFoElffen on 2024-01-17
> **BicyclerBoy said:**
> You can install without formatting partitions but with the problems you have it may be best to re-format the system "/" partition.
A non-destructive reinstall is to NOT choose to format anything, and it write over the old base files on the existing filesyste without formating anything... So all the UUID's should remain. That is, as long as all goes well, and you choose the correct mountpoints for all the pieces.

Since you are going to a bit smaller target than the source, if you wanted to backup all, I would check the space used, then think about compression for the target:
```

cd / # THIS CD IS IMPORTANT THE FOLLOWING LONG COMMAND IS RUN FROM /
tar -cvpzf --one-file-system --checkpoint /backups/backup.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \ 
--exclude=/media \ 
--exclude=/var/log \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \ 
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \ 
--exclude=/home/*/.local/share/Trash /

```
That would be with the target mounted to a folder called /backups

---

### Post by kotgc on 2024-01-17
Ok, I'm writing a plan down here, to be clear.
1: Check which device needs the backup: probably /dev/sda1 or /dev/sda2, as per post #93; (/dev/sda1 is EFI, unsure if this needs to be backed up with  /dev/sda2 which is the OS and contents?)
2: Check which device is the storage for the backup, as per post #93; (/dev/sdb)
3: Check the Ubuntu OS backups size to be backed up; ($ df -h dev/sda2 Used 143G)
4: Check the storage device's capacity and that it's empty, as per post #93; (111.8G or 120G)
  4.1: If the storage device's capacity is too small, run compression code as per post #94;
  4.2: If the storage capacity is greater than the backup size, proceed to next step;
5:  Mount the device to be backed up. Unsure if this needs to include any  other devices for a proper backup, such as EFI files maybe?
6: Proceed with backup code, something like the code in post #91 and suggestions from post #88;
7: Once backed up, a non-destructive reinstall can proceed. Contact this forum post for how to do that.

---

### Post by MAFoElffen on 2024-01-17
Looks good. Good plan.

---

### Post by kotgc on 2024-01-18
I ran code as per post #94, as I am up to plan step 4.1 in post #95.
I'm unsure if the script ran properly and if /dev/sda2 is ready for backup as per steps 5-7?
```

ubuntu@ubuntu:/$ ls
bin   boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  media  mnt   opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var
ubuntu@ubuntu:/$ tar -cvpzf --one-file-system --checkpoint /backups/backup.tar.gz \
> --exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \ 
--exclude=/media \ 
--exclude=/var/log \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \ 
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \ 
--exclude=/home/*/.local/share/Trash /
tar: Removing leading `/' from member names
tar: /backups/backup.tar.gz: Cannot stat: No such file or directory
tar:  : Cannot stat: No such file or directory
tar (child): --one-file-system: Cannot open: Permission denied
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
bash: --exclude=/media: No such file or directory
bash: --exclude=/var/log: No such file or directory
bash: --exclude=/home/*/.gvfs: No such file or directory
bash: --exclude=/home/*/.local/share/Trash: No such file or directory

```

---

### Post by MAFoElffen on 2024-01-18
[LIST=1]
[*]Did you change directories to "/" first? The not found errors tell me you did not. 
[*]Where you running as root? (otherwise preface with 'sudo')... The permissions errors tell me you were not. 
[*]Did you create the folder /backups and mount your backup drive to that mountpoint? Otherwise change that part of the command to where the mountpoint is... 
[/LIST]
 
You can omit the "--one-file-system" flag...

So which drive/partition are you mounting where? Let's, for example, say /dev/sdz1...
```

sudo su -   # become root
mkdir /backups
mount /dev/sdz1 /backups
cd /
tar -cvpzf --checkpoint /backups/backup.tar.gz
ls -lah /backups/backup.tar.gz
du -H /backups

```

---

### Post by kotgc on 2024-01-18
I thought I did change to the root directory, although I did not run the sudo root command.
Here's the output from your code, I must have done something wrong again?
```

root@ubuntu:/# sudo su -
root@ubuntu:~# mkdir /backups
mkdir: cannot create directory &#8216;/backups&#8217;: File exists
root@ubuntu:~# mount /dev/sda2 /backups/
mount: /backups: /dev/sda2 already mounted on /home/ubuntu/Documents.
root@ubuntu:~# cd /
root@ubuntu:/# ls
backups  bin  boot  cdrom  --checkpoint  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var
root@ubuntu:/# tar -cvpzf --checkpoint /backups/backup.tar.gz
tar: Removing leading `/' from member names
tar: /backups/backup.tar.gz: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
root@ubuntu:/# ls -lah /backups/backup.tar.gz
ls: cannot access '/backups/backup.tar.gz': No such file or directory
root@ubuntu:/# du -H /backups/ |sort -nr | head
149644796    /backups/
73488104    /backups/home
73488100    /backups/home/ubuntu
66760388    /backups/home/ubuntu/Videos
62655948    /backups/var
50435696    /backups/var/log
12032444    /backups/var/lib
10707112    /backups/usr
7538424    /backups/usr/lib
6419924    /backups/var/lib/snapd

```

/dev/sda2 needed to be unmounted from ~/Documents
```

root@ubuntu:/# umount /dev/sda2 && sudo mount /dev/sda2 /backups
root@ubuntu:/# cd /
root@ubuntu:/# ls
backups  bin  boot  cdrom  --checkpoint  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var
root@ubuntu:/# cd backups/
root@ubuntu:/backups# ls
bin  boot  cdrom  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  swapfile  sys  tmp  usr  var
root@ubuntu:/backups# cd /
root@ubuntu:/# tar -cvpzf --checkpoint /backups/backup.tar.gz
tar: Removing leading `/' from member names
tar: /backups/backup.tar.gz: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
root@ubuntu:/# tar -cvpzf --checkpoint backups/backup.tar.gz
tar: backups/backup.tar.gz: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors

```

---

### Post by MAFoElffen on 2024-01-19
Sorry. I cut that command off short. The tar command should have been
```

cd / 
sudo tar -cvpzf /backups/backup.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \ 
--exclude=/media \ 
--exclude=/var/log \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \ 
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \ 
--exclude=/home/*/.local/share/Trash \
/

```

---

### Post by kotgc on 2024-01-19
Error still.

```

ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ ls
backups  bin  boot  cdrom  --checkpoint  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  rofs  root  run  sbin  snap  srv  sys  tmp  usr  var
ubuntu@ubuntu:/$ cd backups/
ubuntu@ubuntu:/backups$ 
ubuntu@ubuntu:/$ sudo tar -cvpzf /backups/backup.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \ 
--exclude=/media \ 
--exclude=/var/log \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \ 
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \ 
--exclude=/home/*/.local/share/Trash \
/
tar:  : Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
bash: --exclude=/media: No such file or directory
bash: --exclude=/var/log: No such file or directory
bash: --exclude=/home/*/.gvfs: No such file or directory
bash: --exclude=/home/*/.local/share/Trash: No such file or directory

```

---

### Post by MAFoElffen on 2024-01-19
Hmmm.

Try without the leading dash before the option "-cvpzf"... So try with "cvpzf' instead

And check the write permission of your mount /backups. Maybe do
```

sudo chown -R $USER:$USER /backups
sudo chmod -R 770 /backups

```
...as per this when i google that error: [https://unix.stackexchange.com/questions/149494/tar-exits-on-cannot-stat-no-such-file-of-directory-why](https://unix.stackexchange.com/questions/149494/tar-exits-on-cannot-stat-no-such-file-of-directory-why)

---

### Post by kotgc on 2024-01-19
Error still.
I'm concerned the tar is not picking up essential data as per errors? Shouldn't the root have a media, log and home directory?
If I remove lines 9, 10, 13-15 this may not backup the disk which needs backup of its data?
It appears that command intends **not** to include the non-existent targets. Eliminating the lines for them is a good thing if it allows your command to work, however it seems the next question is:
why does the OS sda2 not have the files and data?
```

ubuntu@ubuntu:~$ sudo chown -R $USER:$USER /backups
chown: cannot access '/backups': No such file or directory
ubuntu@ubuntu:~$ sudo chown -R $ubuntu:$ubuntu /backups
chown: cannot access '/backups': No such file or directory
ubuntu@ubuntu:~$ sudo chmod -R 770 /backups
chmod: cannot access '/backups': No such file or directory
ubuntu@ubuntu:/backups$ sudo tar cvpzf /backups/backup.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \ 
--exclude=/media \ 
--exclude=/var/log \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \ 
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \ 
--exclude=/home/*/.local/share/Trash \
/
tar:  : Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
bash: --exclude=/media: No such file or directory
bash: --exclude=/var/log: No such file or directory
bash: --exclude=/home/*/.gvfs: No such file or directory
bash: --exclude=/home/*/.local/share/Trash: No such file or directory

```

---

### Post by kotgc on 2024-01-20
Need some help with post #103 please?

---

### Post by MAFoElffen on 2024-01-21
I spun up a VM to try it and see if I could recreate the problem. I did.

It was a permissions problem, and an extraneous character in there somewhere. 

With the drive mounted to the /backups directory, do this
```

sudo chown -R $USER:$USER /backups
sudo chmod -R 777 /backups
sudo rm /backups/backup*.tar.gz
sudo rm /backups/error.log

```
Then cd to /, and do the tar command as this (updated from current Ubuntu)...
```

sudo su -
tar cvpzf /backups/backup1.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \
--exclude=/media \
--exclude=/swap.img \
--exclude=/snap \
--exclude=/var/log \
--exclude=/var/lib/snapd/* \
--exclude=/root/snap \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \
--exclude=/home/*/.local/share/Trash \
--exclude=home/*/snap \
/ 2>>/backups/error.log

```
Afterwards, confirmation of the backup...
```

root@lunar-lander-01:~# du -H /backups
16    /backups/lost+found
2780884    /backups
root@lunar-lander-01:~# ls -lah /backups
total 2.7G
drwxrwx---  3 mafoelffen mafoelffen 4.0K Jan 21 08:11 .
drwxr-xr-x 20 root       root       4.0K Jan 21 06:47 ..
-rw-r--r--  1 root       root       2.7G Jan 21 08:15 backup1.tar.gz
-rw-r--r--  1 root       root        337 Jan 21 08:12 error.log
drwxrwx---  2 mafoelffen mafoelffen  16K Jan 21 06:46 lost+found
root@lunar-lander-01:~# grep . /backups/error.log
tar: Removing leading `/' from member names
tar: /var/lib/gdm3/.cache/ibus/dbus-fwjIIAJi: socket ignored
tar: /var/lib/gdm3/.cache/ibus/dbus-r8nbGcEr: socket ignored
tar: /var/lib/gdm3/.cache/ibus/dbus-6Pyl1Lph: socket ignored
tar: /var/lib/gdm3/.cache/ibus/dbus-HDkyUCES: socket ignored
tar: Removing leading `/' from hard link targets

```
Tuning that made it faster, and ended up 60% less space...

I didn't feel you need to backup snaps, or the swap.img file.

---

### Post by kotgc on 2024-01-21
Did this compression work and is it ready for the next step 5 in post #95?

```

root@ubuntu:/# mount /dev/sda2 /backups/
root@ubuntu:/# ls
backups  boot   dev  home  lib32  libx32  mnt  proc  root  sbin  srv  tmp  var
bin      cdrom  etc  lib   lib64  media   opt  rofs  run   snap  sys  usr
root@ubuntu:/# chown -R $USER:$USER /backups/
root@ubuntu:/# chmod -R 777 /backups/
root@ubuntu:/# rm /backups/backup*.tar.gz
rm: cannot remove '/backups/backup*.tar.gz': No such file or directory
root@ubuntu:/# rm /backups/error.log
rm: cannot remove '/backups/error.log': No such file or directory
root@ubuntu:/# sudo su -
tar cvpzf /backups/backup1.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \
--exclude=/media \
--exclude=/swap.img \
--exclude=/snap \
--exclude=/var/log \
--exclude=/var/lib/snapd/* \
--exclude=/root/snap \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \
--exclude=/home/*/.local/share/Trash \
--exclude=home/*/snap \
/ 2>>/backups/error.log
root@ubuntu:~# du -H /backups/ | sort -rh | head -n 20
149644796    /backups/
73488104    /backups/home
73488100    /backups/home/ubuntu
66760388    /backups/home/ubuntu/Videos
62655948    /backups/var
50435696    /backups/var/log
12032444    /backups/var/lib
10707112    /backups/usr
7538424    /backups/usr/lib
6419924    /backups/var/lib/snapd
4851984    /backups/var/lib/snapd/snaps
3154312    /backups/var/log/journal
3154308    /backups/var/log/journal/1b0b850d6ff84782b89ec7d27059159c
3119772    /backups/home/ubuntu/Downloads
2851824    /backups/home/ubuntu/snap
2817492    /backups/home/ubuntu/snap/brave
2709416    /backups/var/lib/libvirt
2709344    /backups/var/lib/libvirt/images
2557852    /backups/usr/lib/x86_64-linux-gnu
2520880    /backups/usr/lib/modules
root@ubuntu:~# ls -lah /backups/
total 2.1G
drwxrwxrwx  20 root root 4.0K Jan 21 21:49 .
drwxr-xr-x   1 root root  240 Jan 21 22:14 ..
lrwxrwxrwx   1 root root    7 Dec  6 01:27 bin -> usr/bin
drwxrwxrwx   4 root root 4.0K Jan 16 14:24 boot
drwxrwxrwx   2 root root 4.0K Dec  6 01:30 cdrom
drwxrwxrwx   4 root root 4.0K Aug  7 22:52 dev
drwxrwxrwx 143 root root  12K Jan 15 19:15 etc
drwxrwxrwx   3 root root 4.0K Dec  6 01:30 home
lrwxrwxrwx   1 root root    7 Dec  6 01:27 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Dec  6 01:27 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Dec  6 01:27 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Dec  6 01:27 libx32 -> usr/libx32
drwxrwxrwx   2 root root  16K Dec  6 01:27 lost+found
drwxrwxrwx   4 root root 4.0K Dec 10 08:58 media
drwxrwxrwx   2 root root 4.0K Aug  7 22:52 mnt
drwxrwxrwx   3 root root 4.0K Jan  2 05:06 opt
drwxrwxrwx   2 root root 4.0K Apr 18  2022 proc
drwxrwxrwx   8 root root 4.0K Jan 16 04:53 root
drwxrwxrwx  13 root root 4.0K Dec  6 01:30 run
lrwxrwxrwx   1 root root    8 Dec  6 01:27 sbin -> usr/sbin
drwxrwxrwx  23 root root 4.0K Dec 31 06:08 snap
drwxrwxrwx   2 root root 4.0K Aug  7 22:52 srv
-rwxrwxrwx   1 root root 2.0G Dec  6 01:27 swapfile
drwxrwxrwx   2 root root 4.0K Apr 18  2022 sys
drwxrwxrwx  18 root root  12K Jan 17 01:17 tmp
drwxrwxrwx  14 root root 4.0K Jan  6 00:44 usr
drwxrwxrwx  15 root root 4.0K Dec 10 08:58 var
root@ubuntu:~# grep . /backups/error.log
grep: /backups/error.log: No such file or directory

```

---

### Post by MAFoElffen on 2024-01-22
???

No that didn't work.

After it was through, it should have only had 3 things i there... The lost and found directory, the backup1.tar file, and the error log.

IDK. I tested that and had it working. I would delete everything in that directory. and try again.

If after you do the tar command, it should show a long running list of everything it is adding to the archive file... until it is through. Should take a while.

---

### Post by kotgc on 2024-01-22
Not sure what happened, but after this below 1st code snippet, lots of code appeared for 5 minutes.
```

root@ubuntu:/# sudo su -
tar cvpzf /backups/backup1.tar.gz \
--exclude=/backups \
--exclude=/proc \
--exclude=/tmp \
--exclude=/mnt \
--exclude=/dev \
--exclude=/sys \
--exclude=/run \
--exclude=/media \
--exclude=/swap.img \
--exclude=/snap \
--exclude=/var/log \
--exclude=/var/lib/snapd/* \
--exclude=/root/snap \
--exclude=/var/cache/apt/archives \
--exclude=/usr/src/linux-headers* \
--exclude=/home/*/.gvfs \
--exclude=/home/*/.cache \
--exclude=/home/*/.local/share/Trash \
--exclude=home/*/snap \
/ 2>>/backups/error.log

```

After 5 minutes of output like this:
```

/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_dscp_bridge.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_dscp_router.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_ets_strict.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_headroom.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_lib.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_max_descriptors.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_mc_aware.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/qos_pfc.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/rif_counter_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/rif_mac_profile_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/rif_mac_profiles.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/rif_mac_profiles_occ.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/router_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/rtnetlink.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_ets.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_offload.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_red_core.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_red_ets.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_red_prio.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_red_root.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_tbf_ets.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_tbf_prio.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sch_tbf_root.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/sharedbuffer.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/devlink_lib_spectrum.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/devlink_resources.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/mirror_gre_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/port_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/q_in_vni_veto.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/resource_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/rif_counter_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/rif_mac_profile_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/router_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/tc_flower_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/tc_police_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum/vxlan_flooding_ipv6.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/mirror_gre_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/port_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/resource_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/rif_mac_profile_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/router_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/tc_flower.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/tc_flower_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/tc_police_scale.sh
/rofs/usr/src/linux-hwe-6.2-headers-6.2.0-26/tools/testing/selftests/drivers/net/mlxsw/spectrum-2/vxlan_flooding_ipv6.sh

```

I ran the below code:
```

root@ubuntu:/# du -H /backups/ | sort -rh | head -n 20
159791308    /backups/
73488104    /backups/home
73488100    /backups/home/ubuntu
66760388    /backups/home/ubuntu/Videos
62655948    /backups/var
50435696    /backups/var/log
12032444    /backups/var/lib
10707112    /backups/usr
7538424    /backups/usr/lib
6419924    /backups/var/lib/snapd
4851984    /backups/var/lib/snapd/snaps
3154312    /backups/var/log/journal
3154308    /backups/var/log/journal/1b0b850d6ff84782b89ec7d27059159c
3119772    /backups/home/ubuntu/Downloads
2851824    /backups/home/ubuntu/snap
2817492    /backups/home/ubuntu/snap/brave
2709416    /backups/var/lib/libvirt
2709344    /backups/var/lib/libvirt/images
2557852    /backups/usr/lib/x86_64-linux-gnu
2520880    /backups/usr/lib/modules
root@ubuntu:/# ls -lah /backups/
total 12G
drwxrwxrwx  20 root root 4.0K Jan 22 06:21 .
drwxr-xr-x   1 root root  240 Jan 22 06:20 ..
-rw-r--r--   1 root root 9.7G Jan 22 06:32 backup1.tar.gz
lrwxrwxrwx   1 root root    7 Dec  6 01:27 bin -> usr/bin
drwxrwxrwx   4 root root 4.0K Jan 16 14:24 boot
drwxrwxrwx   2 root root 4.0K Dec  6 01:30 cdrom
drwxrwxrwx   4 root root 4.0K Aug  7 22:52 dev
-rw-r--r--   1 root root   93 Jan 22 06:21 error.log
drwxrwxrwx 143 root root  12K Jan 15 19:15 etc
drwxrwxrwx   3 root root 4.0K Dec  6 01:30 home
lrwxrwxrwx   1 root root    7 Dec  6 01:27 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Dec  6 01:27 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Dec  6 01:27 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Dec  6 01:27 libx32 -> usr/libx32
drwxrwxrwx   2 root root  16K Dec  6 01:27 lost+found
drwxrwxrwx   4 root root 4.0K Dec 10 08:58 media
drwxrwxrwx   2 root root 4.0K Aug  7 22:52 mnt
drwxrwxrwx   3 root root 4.0K Jan  2 05:06 opt
drwxrwxrwx   2 root root 4.0K Apr 18  2022 proc
drwxrwxrwx   8 root root 4.0K Jan 16 04:53 root
drwxrwxrwx  13 root root 4.0K Dec  6 01:30 run
lrwxrwxrwx   1 root root    8 Dec  6 01:27 sbin -> usr/sbin
drwxrwxrwx  23 root root 4.0K Dec 31 06:08 snap
drwxrwxrwx   2 root root 4.0K Aug  7 22:52 srv
-rwxrwxrwx   1 root root 2.0G Dec  6 01:27 swapfile
drwxrwxrwx   2 root root 4.0K Apr 18  2022 sys
drwxrwxrwx  18 root root  12K Jan 17 01:17 tmp
drwxrwxrwx  14 root root 4.0K Jan  6 00:44 usr
drwxrwxrwx  15 root root 4.0K Dec 10 08:58 var
root@ubuntu:/# grep . /backups/error.log 
tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets

```

---

### Post by MAFoElffen on 2024-01-22
It fialed for you again... how is yours copying files instead of creating and archive and compressing the file inside that archive file?

Here is what I did again tonight. From start to finish. The folder was empty. Label on partition is "BACKUP":
```

root@noble00:~# history
sudo su -
mkdir /backups
mount LABEL="BACKUP" /backups
chown -R $USER:$USER /backups
chmod -R 700 /backups
tar cvpzf /backups/backup1.tar.gz --exclude=/backups --exclude=/proc --exclude=/tmp --exclude=/mnt --exclude=/dev --exclude=/sys --exclude=/run --exclude=/media --exclude=/swap.img --exclude=/snap --exclude=/var/log --exclude=/var/lib/snapd/* --exclude=/root/snap --exclude=/var/cache/apt/archives --exclude=/usr/src/linux-headers* --exclude=/home/*/.gvfs --exclude=/home/*/.cache --exclude=/home/*/.local/share/Trash --exclude=home/*/snap / 2>>/backups/error.log

```
Verify:
```

oot@noble00:~# du -H /backups
16    /backups/lost+found
2320176    /backups
root@noble00:~# ls -l /backups
total 2320172
-rw-r--r-- 1 root root 2375828079 Jan 21 23:32 backup1.tar.gz
-rw-r--r-- 1 root root       1130 Jan 21 23:30 error.log
drwx------ 2 root root      16384 Jan 21 23:22 lost+found
root@noble00:~# umount /backups
root@noble00:~# exit
logout

```

---

### Post by kotgc on 2024-01-22
```

root@ubuntu:/# history
    1  mount /dev/sda2 /backups
    2  clear
    3  cd /
    4  ls
    5  mkdir backups
    6  ls
    7  mount /dev/sda2 /backups/
    8  chown -R $USER:$USER /backups/
    9  chmod -R 777 /backups/
   10  rm /backups/backup1.tar.gz 
   11  rm /backups/error.log 
   12  tar cvpzf /backups/backup1.tar.gz --exclude=/backups --exclude=/proc --exclude=/tmp --exclude=/mnt --exclude=/dev --exclude=/sys --exclude=/run --exclude=/media --exclude=/swap.img --exclude=/snap --exclude=/var/log --exclude=/var/lib/snapd/* --exclude=/root/snap --exclude=/var/cache/apt/archives --exclude=/usr/src/linux-headers* --exclude=/home/*/.gvfs --exclude=/home/*/.cache --exclude=/home/*/.local/share/Trash --exclude=home/*/snap / 2>>/backups/error.log
   13  du -H /backups/ | sort -rh | head -n 20
   14  ls -lah /backups/
   15  grep . /backups/error.log 
   16  clear
   17  history
root@ubuntu:/# sudo su -
root@ubuntu:~# mkdir /backups/
mkdir: cannot create directory &#8216;/backups/&#8217;: File exists
root@ubuntu:~# mount LABEL="BACKUP" /backups/
mount: /backups/: can't find LABEL=BACKUP.
root@ubuntu:~# chown -R $USER:$USER /backups/
root@ubuntu:~# chmod -R 700 /backups/
tar cvpzf /backups/backup1.tar.gz --exclude=/backups --exclude=/proc --exclude=/tmp --exclude=/mnt --exclude=/dev --exclude=/sys --exclude=/run --exclude=/media --exclude=/swap.img --exclude=/snap --exclude=/var/log --exclude=/var/lib/snapd/* --exclude=/root/snap --exclude=/var/cache/apt/archives --exclude=/usr/src/linux-headers* --exclude=/home/*/.gvfs --exclude=/home/*/.cache --exclude=/home/*/.local/share/Trash --exclude=home/*/snap / 2>>/backups/error.log

```

Lots of code output for 5 minutes, then Ubuntu crashes to login screen -> I enter username Ubuntu -> I select Enter -> I open up Firefox to this cached page -> I open up Terminal -> I run the above code again and wait for 5 minutes of code output -> then I add this code:

```

root@ubuntu:/backups# du -H /backups/ | sort -rh | head -n 20
159797656    /backups/
73488104    /backups/home
73488100    /backups/home/ubuntu
66760388    /backups/home/ubuntu/Videos
62655948    /backups/var
50435696    /backups/var/log
12032444    /backups/var/lib
10707112    /backups/usr
7538424    /backups/usr/lib
6419924    /backups/var/lib/snapd
4851984    /backups/var/lib/snapd/snaps
3154312    /backups/var/log/journal
3154308    /backups/var/log/journal/1b0b850d6ff84782b89ec7d27059159c
3119772    /backups/home/ubuntu/Downloads
2851824    /backups/home/ubuntu/snap
2817492    /backups/home/ubuntu/snap/brave
2709416    /backups/var/lib/libvirt
2709344    /backups/var/lib/libvirt/images
2557852    /backups/usr/lib/x86_64-linux-gnu
2520880    /backups/usr/lib/modules
root@ubuntu:/backups# ls -lah /backups/
total 12G
drwx------  20 root root 4.0K Jan 22 06:21 .
drwxr-xr-x   1 root root  240 Jan 22 06:20 ..
-rwx------   1 root root 9.7G Jan 22 08:08 backup1.tar.gz
lrwxrwxrwx   1 root root    7 Dec  6 01:27 bin -> usr/bin
drwx------   4 root root 4.0K Jan 16 14:24 boot
drwx------   2 root root 4.0K Dec  6 01:30 cdrom
drwx------   4 root root 4.0K Aug  7 22:52 dev
-rwx------   1 root root  279 Jan 22 07:56 error.log
drwx------ 143 root root  12K Jan 15 19:15 etc
drwx------   3 root root 4.0K Dec  6 01:30 home
lrwxrwxrwx   1 root root    7 Dec  6 01:27 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Dec  6 01:27 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Dec  6 01:27 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Dec  6 01:27 libx32 -> usr/libx32
drwx------   2 root root  16K Dec  6 01:27 lost+found
drwx------   4 root root 4.0K Dec 10 08:58 media
drwx------   2 root root 4.0K Aug  7 22:52 mnt
drwx------   3 root root 4.0K Jan  2 05:06 opt
drwx------   2 root root 4.0K Apr 18  2022 proc
drwx------   8 root root 4.0K Jan 16 04:53 root
drwx------  13 root root 4.0K Dec  6 01:30 run
lrwxrwxrwx   1 root root    8 Dec  6 01:27 sbin -> usr/sbin
drwx------  23 root root 4.0K Dec 31 06:08 snap
drwx------   2 root root 4.0K Aug  7 22:52 srv
-rwx------   1 root root 2.0G Dec  6 01:27 swapfile
drwx------   2 root root 4.0K Apr 18  2022 sys
drwx------  18 root root  12K Jan 17 01:17 tmp
drwx------  14 root root 4.0K Jan  6 00:44 usr
drwx------  15 root root 4.0K Dec 10 08:58 var
root@ubuntu:/backups# grep . /backups/error.log 
tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets
tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets
tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets

```

---

### Post by kotgc on 2024-01-23
Ubuntu can't be fixed, looks like wiping the disk for a new install.
What a waste of time
Thanks to anyone who helped.

---

### Post by kotgc on 2024-01-23
Ok, just wiped the old Ubuntu OS with the black screen issue.
Just installed a fresh Ubuntu 22.04.3 and monitor 3 is showing black screen, any suggestions please?

See code 1/2 on post #112 and code 2/2 on post #113.
```

ubuntu@ubuntu:~$ sudo dmesg
[sudo] password for ubuntu: 
[    0.000000] microcode: updated early: 0xcc -> 0xf8, date = 2023-02-23
[    0.000000] Linux version 6.5.0-14-generic (buildd@lcy02-amd64-110) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov 20 18:15:30 UTC 2 (Ubuntu 6.5.0-14.14~22.04.1-generic 6.5.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic root=UUID=8db91722-3256-4c30-b0cf-4e75ea66d3b8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Hygon HygonGenuine
[    0.000000]   Centaur CentaurHauls
[    0.000000]   zhaoxin   Shanghai  
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000403fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040400000-0x000000008d84cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008d84e000-0x000000008e9abfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008e9ad000-0x000000009b845fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009b847000-0x000000009b869fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b86a000-0x000000009b86afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b86b000-0x000000009b9aefff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009dcff000-0x000000009effefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009efff000-0x000000009effffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f000000-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000045dffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x96836018-0x96856657] usable ==> usable
[    0.000000] e820: update [mem 0x96836018-0x96856657] usable ==> usable
[    0.000000] e820: update [mem 0x96827018-0x96835057] usable ==> usable
[    0.000000] e820: update [mem 0x96827018-0x96835057] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009efff] reserved
[    0.000000] reserve setup_data: [mem 0x000000000009f000-0x000000000009ffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000000a0000-0x00000000000fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000040000000-0x00000000403fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000040400000-0x000000008d84cfff] usable
[    0.000000] reserve setup_data: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
[    0.000000] reserve setup_data: [mem 0x000000008d84e000-0x000000008e9abfff] usable
[    0.000000] reserve setup_data: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
[    0.000000] reserve setup_data: [mem 0x000000008e9ad000-0x0000000096827017] usable
[    0.000000] reserve setup_data: [mem 0x0000000096827018-0x0000000096835057] usable
[    0.000000] reserve setup_data: [mem 0x0000000096835058-0x0000000096836017] usable
[    0.000000] reserve setup_data: [mem 0x0000000096836018-0x0000000096856657] usable
[    0.000000] reserve setup_data: [mem 0x0000000096856658-0x000000009b845fff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009b847000-0x000000009b869fff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b86a000-0x000000009b86afff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009b86b000-0x000000009b9aefff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
[    0.000000] reserve setup_data: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009dcff000-0x000000009effefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009efff000-0x000000009effffff] usable
[    0.000000] reserve setup_data: [mem 0x000000009f000000-0x000000009fffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000045dffffff] usable
[    0.000000] efi: EFI v2.7 by American Megatrends
[    0.000000] efi: ACPI=0x9dcbb000 ACPI 2.0=0x9dcbb014 SMBIOS=0x9eb75000 SMBIOS 3.0=0x9eb74000 MEMATTR=0x98d4c818 ESRT=0x994f6218 MOKvar=0x9eba6000 RNG=0x9db4d018 
[    0.000000] random: crng init done
[    0.000000] efi: Remove mem320: MMIO range=[0xe0000000-0xefffffff] (256MB) from e820 map
[    0.000000] e820: remove [mem 0xe0000000-0xefffffff] reserved
[    0.000000] efi: Not removing mem321: MMIO range=[0xfe000000-0xfe010fff] (68KB) from e820 map
[    0.000000] efi: Not removing mem322: MMIO range=[0xfec00000-0xfec00fff] (4KB) from e820 map
[    0.000000] efi: Not removing mem323: MMIO range=[0xfee00000-0xfee00fff] (4KB) from e820 map
[    0.000000] efi: Remove mem324: MMIO range=[0xff000000-0xffffffff] (16MB) from e820 map
[    0.000000] e820: remove [mem 0xff000000-0xffffffff] reserved
[    0.000000] secureboot: Secure boot disabled
[    0.000000] SMBIOS 3.2.0 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./H470M-HVS, BIOS P1.10 01/11/2021
[    0.000000] tsc: Detected 3700.000 MHz processor
[    0.000000] tsc: Detected 3699.850 MHz TSC
[    0.000519] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000522] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000533] last_pfn = 0x45e000 max_arch_pfn = 0x400000000
[    0.000536] MTRR map: 5 entries (3 fixed + 2 variable; max 23), built from 10 variable MTRRs
[    0.000538] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000935] last_pfn = 0x9f000 max_arch_pfn = 0x400000000
[    0.006996] esrt: Reserving ESRT space from 0x00000000994f6218 to 0x00000000994f6278.
[    0.007003] e820: update [mem 0x994f6000-0x994f6fff] usable ==> reserved
[    0.007055] Using GB pages for direct mapping
[    0.007600] secureboot: Secure boot disabled
[    0.007601] RAMDISK: [mem 0x91db5000-0x960a5fff]
[    0.007606] ACPI: Early table checksum verification disabled
[    0.007608] ACPI: RSDP 0x000000009DCBB014 000024 (v02 ALASKA)
[    0.007612] ACPI: XSDT 0x000000009DCBA728 0000BC (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007616] ACPI: FACP 0x000000009DBA8000 000114 (v06 ALASKA A M I    01072009 AMI  00010013)
[    0.007621] ACPI: DSDT 0x000000009DB65000 042272 (v02 ALASKA A M I    01072009 INTL 20160527)
[    0.007624] ACPI: FACS 0x000000009DCFE000 000040
[    0.007626] ACPI: MCFG 0x000000009DBAC000 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.007628] ACPI: SSDT 0x000000009DBA9000 0020AD (v02 CpuRef CpuSsdt  00003000 INTL 20160527)
[    0.007631] ACPI: FIDT 0x000000009DB64000 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007634] ACPI: AAFT 0x000000009DBAE000 0002DE (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.007636] ACPI: SSDT 0x000000009DB60000 0031DA (v02 SaSsdt SaSsdt   00003000 INTL 20160527)
[    0.007639] ACPI: SSDT 0x000000009DB5D000 002703 (v02 Intel  PegSsdt  00001000 INTL 20160527)
[    0.007641] ACPI: HPET 0x000000009DBAD000 000038 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007644] ACPI: NHLT 0x000000009DB5B000 001821 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.007646] ACPI: LPIT 0x000000009DB5A000 000094 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007649] ACPI: SSDT 0x000000009DB56000 0025B2 (v02 ALASKA TbtTypeC 00000000 INTL 20160527)
[    0.007652] ACPI: DBGP 0x000000009DB55000 000034 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007654] ACPI: DBG2 0x000000009DB54000 000054 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.007657] ACPI: SSDT 0x000000009DB52000 001B67 (v02 ALASKA UsbCTabl 00001000 INTL 20160527)
[    0.007659] ACPI: DMAR 0x000000009DB51000 000070 (v01 INTEL  EDK2     00000002      01000013)
[    0.007662] ACPI: BGRT 0x000000009DB50000 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007664] ACPI: WSMT 0x000000009DB59000 000028 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007667] ACPI: APIC 0x000000009DB4F000 0000BC (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.007669] ACPI: FPDT 0x000000009DB4E000 000044 (v01 ALASKA CML      01072009 AMI  01000013)
[    0.007671] ACPI: Reserving FACP table memory at [mem 0x9dba8000-0x9dba8113]
[    0.007673] ACPI: Reserving DSDT table memory at [mem 0x9db65000-0x9dba7271]
[    0.007673] ACPI: Reserving FACS table memory at [mem 0x9dcfe000-0x9dcfe03f]
[    0.007674] ACPI: Reserving MCFG table memory at [mem 0x9dbac000-0x9dbac03b]
[    0.007675] ACPI: Reserving SSDT table memory at [mem 0x9dba9000-0x9dbab0ac]
[    0.007676] ACPI: Reserving FIDT table memory at [mem 0x9db64000-0x9db6409b]
[    0.007676] ACPI: Reserving AAFT table memory at [mem 0x9dbae000-0x9dbae2dd]
[    0.007677] ACPI: Reserving SSDT table memory at [mem 0x9db60000-0x9db631d9]
[    0.007678] ACPI: Reserving SSDT table memory at [mem 0x9db5d000-0x9db5f702]
[    0.007678] ACPI: Reserving HPET table memory at [mem 0x9dbad000-0x9dbad037]
[    0.007679] ACPI: Reserving NHLT table memory at [mem 0x9db5b000-0x9db5c820]
[    0.007680] ACPI: Reserving LPIT table memory at [mem 0x9db5a000-0x9db5a093]
[    0.007681] ACPI: Reserving SSDT table memory at [mem 0x9db56000-0x9db585b1]
[    0.007681] ACPI: Reserving DBGP table memory at [mem 0x9db55000-0x9db55033]
[    0.007682] ACPI: Reserving DBG2 table memory at [mem 0x9db54000-0x9db54053]
[    0.007683] ACPI: Reserving SSDT table memory at [mem 0x9db52000-0x9db53b66]
[    0.007684] ACPI: Reserving DMAR table memory at [mem 0x9db51000-0x9db5106f]
[    0.007684] ACPI: Reserving BGRT table memory at [mem 0x9db50000-0x9db50037]
[    0.007685] ACPI: Reserving WSMT table memory at [mem 0x9db59000-0x9db59027]
[    0.007686] ACPI: Reserving APIC table memory at [mem 0x9db4f000-0x9db4f0bb]
[    0.007687] ACPI: Reserving FPDT table memory at [mem 0x9db4e000-0x9db4e043]
[    0.007942] No NUMA configuration found
[    0.007942] Faking a node at [mem 0x0000000000000000-0x000000045dffffff]
[    0.007951] NODE_DATA(0) allocated [mem 0x45dfd5000-0x45dffffff]
[    0.008121] Zone ranges:
[    0.008122]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.008124]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.008125]   Normal   [mem 0x0000000100000000-0x000000045dffffff]
[    0.008126]   Device   empty
[    0.008127] Movable zone start for each node
[    0.008129] Early memory node ranges
[    0.008129]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.008130]   node   0: [mem 0x000000000009f000-0x000000000009ffff]
[    0.008131]   node   0: [mem 0x0000000000100000-0x000000003fffffff]
[    0.008132]   node   0: [mem 0x0000000040400000-0x000000008d84cfff]
[    0.008133]   node   0: [mem 0x000000008d84e000-0x000000008e9abfff]
[    0.008134]   node   0: [mem 0x000000008e9ad000-0x000000009b845fff]
[    0.008135]   node   0: [mem 0x000000009b847000-0x000000009b869fff]
[    0.008135]   node   0: [mem 0x000000009b86b000-0x000000009b9aefff]
[    0.008136]   node   0: [mem 0x000000009efff000-0x000000009effffff]
[    0.008137]   node   0: [mem 0x0000000100000000-0x000000045dffffff]
[    0.008139] Initmem setup node 0 [mem 0x0000000000001000-0x000000045dffffff]
[    0.008142] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.008143] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.008159] On node 0, zone DMA: 96 pages in unavailable ranges
[    0.010553] On node 0, zone DMA32: 1024 pages in unavailable ranges
[    0.010571] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.010792] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.010793] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.010795] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.010903] On node 0, zone DMA32: 13904 pages in unavailable ranges
[    0.025888] On node 0, zone Normal: 4096 pages in unavailable ranges
[    0.025952] On node 0, zone Normal: 8192 pages in unavailable ranges
[    0.026180] ACPI: PM-Timer IO Port: 0x1808
[    0.026185] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.026187] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.026188] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.026188] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.026189] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.026190] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.026190] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.026191] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.026228] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.026230] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.026232] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.026235] ACPI: Using ACPI (MADT) for SMP configuration information
[    0.026236] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.026244] e820: update [mem 0x96f8f000-0x96fcffff] usable ==> reserved
[    0.026259] TSC deadline timer available
[    0.026260] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.026280] PM: hibernation: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.026282] PM: hibernation: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.026284] PM: hibernation: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.026285] PM: hibernation: Registered nosave memory: [mem 0x40000000-0x403fffff]
[    0.026287] PM: hibernation: Registered nosave memory: [mem 0x8d84d000-0x8d84dfff]
[    0.026288] PM: hibernation: Registered nosave memory: [mem 0x8e9ac000-0x8e9acfff]
[    0.026290] PM: hibernation: Registered nosave memory: [mem 0x96827000-0x96827fff]
[    0.026292] PM: hibernation: Registered nosave memory: [mem 0x96835000-0x96835fff]
[    0.026292] PM: hibernation: Registered nosave memory: [mem 0x96836000-0x96836fff]
[    0.026294] PM: hibernation: Registered nosave memory: [mem 0x96856000-0x96856fff]
[    0.026296] PM: hibernation: Registered nosave memory: [mem 0x96f8f000-0x96fcffff]
[    0.026297] PM: hibernation: Registered nosave memory: [mem 0x994f6000-0x994f6fff]
[    0.026299] PM: hibernation: Registered nosave memory: [mem 0x9b846000-0x9b846fff]
[    0.026301] PM: hibernation: Registered nosave memory: [mem 0x9b86a000-0x9b86afff]
[    0.026302] PM: hibernation: Registered nosave memory: [mem 0x9b9af000-0x9d9aefff]
[    0.026303] PM: hibernation: Registered nosave memory: [mem 0x9d9af000-0x9dbaefff]
[    0.026304] PM: hibernation: Registered nosave memory: [mem 0x9dbaf000-0x9dcfefff]
[    0.026304] PM: hibernation: Registered nosave memory: [mem 0x9dcff000-0x9effefff]
[    0.026306] PM: hibernation: Registered nosave memory: [mem 0x9f000000-0x9fffffff]
[    0.026307] PM: hibernation: Registered nosave memory: [mem 0xa0000000-0xfdffffff]
[    0.026307] PM: hibernation: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.026308] PM: hibernation: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.026309] PM: hibernation: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.026309] PM: hibernation: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.026310] PM: hibernation: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.026310] PM: hibernation: Registered nosave memory: [mem 0xfee01000-0xffffffff]
[    0.026312] [mem 0xa0000000-0xfdffffff] available for PCI devices
[    0.026313] Booting paravirtualized kernel on bare hardware
[    0.026314] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.026321] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.026604] percpu: Embedded 63 pages/cpu s221184 r8192 d28672 u262144
[    0.026611] pcpu-alloc: s221184 r8192 d28672 u262144 alloc=1*2097152
[    0.026613] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.026635] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic root=UUID=8db91722-3256-4c30-b0cf-4e75ea66d3b8 ro quiet splash vt.handoff=7
[    0.026700] Unknown kernel command line parameters "splash BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic", will be passed to user space.
[    0.027818] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes, linear)
[    0.028381] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes, linear)
[    0.028472] Fallback order for Node 0: 0 
[    0.028475] Built 1 zonelists, mobility grouping on.  Total pages: 4101717
[    0.028476] Policy zone: Normal
[    0.028480] mem auto-init: stack:all(zero), heap alloc:on, heap free:off
[    0.028485] software IO TLB: area num 8.
[    0.064513] Memory: 16097900K/16667944K available (20480K kernel code, 4265K rwdata, 13180K rodata, 4792K init, 17396K bss, 569784K reserved, 0K cma-reserved)
[    0.064713] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.064734] ftrace: allocating 55226 entries in 216 pages
[    0.072452] ftrace: allocated 216 pages with 4 groups
[    0.073033] Dynamic Preempt: voluntary
[    0.073060] rcu: Preemptible hierarchical RCU implementation.
[    0.073061] rcu:     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=8.
[    0.073062]     Trampoline variant of Tasks RCU enabled.
[    0.073062]     Rude variant of Tasks RCU enabled.
[    0.073063]     Tracing variant of Tasks RCU enabled.
[    0.073063] rcu: RCU calculated value of scheduler-enlistment delay is 25 jiffies.
[    0.073064] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.075510] NR_IRQS: 524544, nr_irqs: 2048, preallocated irqs: 16
[    0.075769] rcu: srcu_init: Setting srcu_struct sizes based on contention.
[    0.076001] Console: colour dummy device 80x25
[    0.076003] printk: console [tty0] enabled
[    0.076045] ACPI: Core revision 20230331
[    0.076379] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.076471] APIC: Switch to symmetric I/O mode setup
[    0.076473] DMAR: Host address width 39
[    0.076474] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.076479] DMAR: dmar0: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.076481] DMAR: RMRR base: 0x0000009e908000 end: 0x0000009eb51fff
[    0.076483] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 0
[    0.076485] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.076485] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.078025] DMAR-IR: Enabled IRQ remapping in x2apic mode
[    0.078026] x2apic enabled
[    0.078042] Switched APIC routing to cluster x2apic.
[    0.082932] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.100409] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x6aa99074b1c, max_idle_ns: 881590506587 ns
[    0.100414] Calibrating delay loop (skipped), value calculated using timer frequency.. 7399.70 BogoMIPS (lpj=14799400)
[    0.100432] x86/cpu: SGX disabled by BIOS.
[    0.100438] CPU0: Thermal monitoring enabled (TM1)
[    0.100468] process: using mwait in idle threads
[    0.100471] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.100472] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.100475] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.100477] Spectre V2 : Mitigation: Enhanced / Automatic IBRS
[    0.100477] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.100478] Spectre V2 : Spectre v2 / PBRSB-eIBRS: Retire a single CALL on VMEXIT
[    0.100479] RETBleed: Mitigation: Enhanced IBRS
[    0.100480] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.100481] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl
[    0.100485] MMIO Stale Data: Mitigation: Clear CPU buffers
[    0.100487] SRBDS: Mitigation: Microcode
[    0.100488] GDS: Mitigation: Microcode
[    0.100492] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.100493] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.100494] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.100495] x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
[    0.100496] x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
[    0.100497] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.100498] x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
[    0.100499] x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
[    0.100499] x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
[    0.121645] Freeing SMP alternatives memory: 44K
[    0.121648] pid_max: default: 32768 minimum: 301
[    0.124452] LSM: initializing lsm=lockdown,capability,landlock,yama,apparmor,integrity
[    0.124462] landlock: Up and running.
[    0.124463] Yama: becoming mindful.
[    0.124482] AppArmor: AppArmor initialized
[    0.124516] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.124528] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.124939] smpboot: CPU0: Intel(R) Core(TM) i3-10105F CPU @ 3.70GHz (family: 0x6, model: 0xa5, stepping: 0x3)
[    0.125023] RCU Tasks: Setting shift to 3 and lim to 1 rcu_task_cb_adjust=1.
[    0.125034] RCU Tasks Rude: Setting shift to 3 and lim to 1 rcu_task_cb_adjust=1.
[    0.125046] RCU Tasks Trace: Setting shift to 3 and lim to 1 rcu_task_cb_adjust=1.
[    0.125054] Performance Events: PEBS fmt3+, Skylake events, 32-deep LBR, full-width counters, Intel PMU driver.
[    0.125072] ... version:                4
[    0.125073] ... bit width:              48
[    0.125073] ... generic registers:      4
[    0.125074] ... value mask:             0000ffffffffffff
[    0.125075] ... max period:             00007fffffffffff
[    0.125075] ... fixed-purpose events:   3
[    0.125076] ... event mask:             000000070000000f
[    0.125150] signal: max sigframe size: 2032
[    0.125159] Estimated ratio of average max frequency by base frequency (times 1024): 1162
[    0.125176] rcu: Hierarchical SRCU implementation.
[    0.125177] rcu:     Max phase no-delay instances is 1000.
[    0.125606] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.125661] smp: Bringing up secondary CPUs ...
[    0.125726] smpboot: x86: Booting SMP configuration:
[    0.125727] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.128427] MMIO Stale Data CPU bug present and SMT on, data leak possible. See https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/processor_mmio_stale_data.html for more details.
[    0.128442] smp: Brought up 1 node, 8 CPUs
[    0.128442] smpboot: Max logical packages: 1
[    0.128442] smpboot: Total of 8 processors activated (59197.60 BogoMIPS)
[    0.132671] devtmpfs: initialized
[    0.132671] x86/mm: Memory block size: 128MB
[    0.133401] ACPI: PM: Registering ACPI NVS region [mem 0x9b846000-0x9b846fff] (4096 bytes)
[    0.133401] ACPI: PM: Registering ACPI NVS region [mem 0x9dbaf000-0x9dcfefff] (1376256 bytes)
[    0.133401] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.133401] futex hash table entries: 2048 (order: 5, 131072 bytes, linear)
[    0.133401] pinctrl core: initialized pinctrl subsystem
[    0.133401] PM: RTC time: 08:18:19, date: 2024-01-23
[    0.133401] NET: Registered PF_NETLINK/PF_ROUTE protocol family
[    0.133401] DMA: preallocated 2048 KiB GFP_KERNEL pool for atomic allocations
[    0.133401] DMA: preallocated 2048 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
[    0.133470] DMA: preallocated 2048 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
[    0.133482] audit: initializing netlink subsys (disabled)
[    0.133494] audit: type=2000 audit(1705997899.056:1): state=initialized audit_enabled=0 res=1
[    0.133494] thermal_sys: Registered thermal governor 'fair_share'
[    0.133494] thermal_sys: Registered thermal governor 'bang_bang'
[    0.133494] thermal_sys: Registered thermal governor 'step_wise'
[    0.133494] thermal_sys: Registered thermal governor 'user_space'
[    0.133494] thermal_sys: Registered thermal governor 'power_allocator'
[    0.133494] EISA bus registered
[    0.133494] cpuidle: using governor ladder
[    0.133494] cpuidle: using governor menu
[    0.133494] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.133494] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.133494] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.133494] PCI: not using MMCONFIG
[    0.133494] PCI: Using configuration type 1 for base access
[    0.133494] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.133494] kprobes: kprobe jump-optimization is enabled. All kprobes are optimized if possible.
[    0.133494] HugeTLB: registered 1.00 GiB page size, pre-allocated 0 pages
[    0.133494] HugeTLB: 16380 KiB vmemmap can be freed for a 1.00 GiB page
[    0.133494] HugeTLB: registered 2.00 MiB page size, pre-allocated 0 pages
[    0.133494] HugeTLB: 28 KiB vmemmap can be freed for a 2.00 MiB page
[    0.133494] fbcon: Taking over console
[    0.133494] ACPI: Added _OSI(Module Device)
[    0.133494] ACPI: Added _OSI(Processor Device)
[    0.133494] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.133494] ACPI: Added _OSI(Processor Aggregator Device)
[    0.174912] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.179710] ACPI: Dynamic OEM Table Load:
[    0.179710] ACPI: SSDT 0xFFFF91FBC1144800 000400 (v02 PmRef  Cpu0Cst  00003001 INTL 20160527)
[    0.181046] ACPI: Dynamic OEM Table Load:
[    0.181051] ACPI: SSDT 0xFFFF91FBC1125800 0006EC (v02 PmRef  Cpu0Ist  00003000 INTL 20160527)
[    0.182007] ACPI: Dynamic OEM Table Load:
[    0.182011] ACPI: SSDT 0xFFFF91FBC090F600 0000FC (v02 PmRef  Cpu0Psd  00003000 INTL 20160527)
[    0.183299] ACPI: Dynamic OEM Table Load:
[    0.183304] ACPI: SSDT 0xFFFF91FBC196D800 000778 (v02 PmRef  ApIst    00003000 INTL 20160527)
[    0.184414] ACPI: Dynamic OEM Table Load:
[    0.184420] ACPI: SSDT 0xFFFF91FBC015B000 000D22 (v02 PmRef  ApPsd    00003000 INTL 20160527)
[    0.185975] ACPI: Dynamic OEM Table Load:
[    0.185979] ACPI: SSDT 0xFFFF91FBC1147400 0003CA (v02 PmRef  ApCst    00003000 INTL 20160527)
[    0.190398] ACPI: Interpreter enabled
[    0.190429] ACPI: PM: (supports S0 S3 S4 S5)
[    0.190430] ACPI: Using IOAPIC for interrupt routing
[    0.191676] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.193535] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved as ACPI motherboard resource
[    0.193544] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.193545] PCI: Using E820 reservations for host bridge windows
[    0.194514] ACPI: Enabled 9 GPEs in block 00 to 7F
[    0.204845] ACPI: \_SB_.PCI0.XDCI.USBC: New power resource
[    0.207354] ACPI: \_SB_.PCI0.SAT0.VOL0.V0PR: New power resource
[    0.207541] ACPI: \_SB_.PCI0.SAT0.VOL1.V1PR: New power resource
[    0.207718] ACPI: \_SB_.PCI0.SAT0.VOL2.V2PR: New power resource
[    0.210561] ACPI: \_SB_.PCI0.CNVW.WRST: New power resource
[    0.214053] ACPI: \PIN_: New power resource
[    0.214395] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.214402] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI EDR HPX-Type3]
[    0.214488] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug SHPCHotplug PME]
[    0.214644] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability LTR DPC]
[    0.214645] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.215712] PCI host bridge to bus 0000:00
[    0.215714] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.215716] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.215717] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.215719] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff window]
[    0.215720] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xdfffffff window]
[    0.215721] pci_bus 0000:00: root bus resource [mem 0xfc800000-0xfe7fffff window]
[    0.215722] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.215797] pci 0000:00:00.0: [8086:9b63] type 00 class 0x060000
[    0.215857] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.215890] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.216447] pci 0000:00:12.0: [8086:06f9] type 00 class 0x118000
[    0.216462] pci 0000:00:12.0: reg 0x10: [mem 0xab41d000-0xab41dfff 64bit]
[    0.216603] pci 0000:00:14.0: [8086:06ed] type 00 class 0x0c0330
[    0.216616] pci 0000:00:14.0: reg 0x10: [mem 0xab400000-0xab40ffff 64bit]
[    0.216668] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.217152] pci 0000:00:14.2: [8086:06ef] type 00 class 0x050000
[    0.217167] pci 0000:00:14.2: reg 0x10: [mem 0xab416000-0xab417fff 64bit]
[    0.217177] pci 0000:00:14.2: reg 0x18: [mem 0xab41c000-0xab41cfff 64bit]
[    0.217284] pci 0000:00:16.0: [8086:06e0] type 00 class 0x078000
[    0.217301] pci 0000:00:16.0: reg 0x10: [mem 0xab41b000-0xab41bfff 64bit]
[    0.217368] pci 0000:00:16.0: PME# supported from D3hot
[    0.217794] pci 0000:00:17.0: [8086:06d2] type 00 class 0x010601
[    0.217805] pci 0000:00:17.0: reg 0x10: [mem 0xab414000-0xab415fff]
[    0.217812] pci 0000:00:17.0: reg 0x14: [mem 0xab41a000-0xab41a0ff]
[    0.217818] pci 0000:00:17.0: reg 0x18: [io  0x6050-0x6057]
[    0.217824] pci 0000:00:17.0: reg 0x1c: [io  0x6040-0x6043]
[    0.217830] pci 0000:00:17.0: reg 0x20: [io  0x6020-0x603f]
[    0.217836] pci 0000:00:17.0: reg 0x24: [mem 0xab419000-0xab4197ff]
[    0.217869] pci 0000:00:17.0: PME# supported from D3hot
[    0.218203] pci 0000:00:1d.0: [8086:06b2] type 01 class 0x060400
[    0.218277] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.218302] pci 0000:00:1d.0: PTM enabled (root), 4ns granularity
[    0.218943] pci 0000:00:1d.3: [8086:06b3] type 01 class 0x060400
[    0.219015] pci 0000:00:1d.3: PME# supported from D0 D3hot D3cold
[    0.219038] pci 0000:00:1d.3: PTM enabled (root), 4ns granularity
[    0.219680] pci 0000:00:1f.0: [8086:0684] type 00 class 0x060100
[    0.220053] pci 0000:00:1f.3: [8086:06c8] type 00 class 0x040300
[    0.220082] pci 0000:00:1f.3: reg 0x10: [mem 0xab410000-0xab413fff 64bit]
[    0.220119] pci 0000:00:1f.3: reg 0x20: [mem 0xab100000-0xab1fffff 64bit]
[    0.220193] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.221123] pci 0000:00:1f.4: [8086:06a3] type 00 class 0x0c0500
[    0.221146] pci 0000:00:1f.4: reg 0x10: [mem 0xab418000-0xab4180ff 64bit]
[    0.221172] pci 0000:00:1f.4: reg 0x20: [io  0xefa0-0xefbf]
[    0.221404] pci 0000:00:1f.5: [8086:06a4] type 00 class 0x0c8000
[    0.221417] pci 0000:00:1f.5: reg 0x10: [mem 0xfe010000-0xfe010fff]
[    0.221529] pci 0000:01:00.0: [10de:128b] type 00 class 0x030000
[    0.221539] pci 0000:01:00.0: reg 0x10: [mem 0xaa000000-0xaaffffff]
[    0.221548] pci 0000:01:00.0: reg 0x14: [mem 0xa0000000-0xa7ffffff 64bit pref]
[    0.221556] pci 0000:01:00.0: reg 0x1c: [mem 0xa8000000-0xa9ffffff 64bit pref]
[    0.221562] pci 0000:01:00.0: reg 0x24: [io  0x5000-0x507f]
[    0.221568] pci 0000:01:00.0: reg 0x30: [mem 0xab000000-0xab07ffff pref]
[    0.221583] pci 0000:01:00.0: BAR 1: assigned to efifb
[    0.221587] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.221645] pci 0000:01:00.0: 16.000 Gb/s available PCIe bandwidth, limited by 2.5 GT/s PCIe x8 link at 0000:00:01.0 (capable of 63.008 Gb/s with 8.0 GT/s PCIe x8 link)
[    0.221710] pci 0000:01:00.1: [10de:0e0f] type 00 class 0x040300
[    0.221719] pci 0000:01:00.1: reg 0x10: [mem 0xab080000-0xab083fff]
[    0.221813] pci 0000:00:01.0: ASPM: current common clock configuration is inconsistent, reconfiguring
[    0.232424] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.232426] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.232428] pci 0000:00:01.0:   bridge window [mem 0xaa000000-0xab0fffff]
[    0.232430] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.232514] pci 0000:02:00.0: [10ec:8161] type 00 class 0x020000
[    0.232530] pci 0000:02:00.0: reg 0x10: [io  0x4000-0x40ff]
[    0.232549] pci 0000:02:00.0: reg 0x18: [mem 0xab304000-0xab304fff 64bit]
[    0.232562] pci 0000:02:00.0: reg 0x20: [mem 0xab300000-0xab303fff 64bit]
[    0.232659] pci 0000:02:00.0: supports D1 D2
[    0.232660] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.232833] pci 0000:00:1d.0: PCI bridge to [bus 02]
[    0.232836] pci 0000:00:1d.0:   bridge window [io  0x4000-0x4fff]
[    0.232838] pci 0000:00:1d.0:   bridge window [mem 0xab300000-0xab3fffff]
[    0.232916] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.232932] pci 0000:03:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.232951] pci 0000:03:00.0: reg 0x18: [mem 0xab204000-0xab204fff 64bit]
[    0.232963] pci 0000:03:00.0: reg 0x20: [mem 0xab200000-0xab203fff 64bit]
[    0.233058] pci 0000:03:00.0: supports D1 D2
[    0.233059] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233226] pci 0000:00:1d.3: PCI bridge to [bus 03]
[    0.233228] pci 0000:00:1d.3:   bridge window [io  0x3000-0x3fff]
[    0.233230] pci 0000:00:1d.3:   bridge window [mem 0xab200000-0xab2fffff]
[    0.234727] ACPI: PCI: Interrupt link LNKA configured for IRQ 0
[    0.234805] ACPI: PCI: Interrupt link LNKB configured for IRQ 1
[    0.234881] ACPI: PCI: Interrupt link LNKC configured for IRQ 0
[    0.234956] ACPI: PCI: Interrupt link LNKD configured for IRQ 0
[    0.235032] ACPI: PCI: Interrupt link LNKE configured for IRQ 0
[    0.235107] ACPI: PCI: Interrupt link LNKF configured for IRQ 0
[    0.235182] ACPI: PCI: Interrupt link LNKG configured for IRQ 0
[    0.235257] ACPI: PCI: Interrupt link LNKH configured for IRQ 0
[    0.238198] iommu: Default domain type: Translated
[    0.238198] iommu: DMA domain TLB invalidation policy: lazy mode
[    0.238198] SCSI subsystem initialized
[    0.238198] libata version 3.00 loaded.
[    0.238198] ACPI: bus type USB registered
[    0.238198] usbcore: registered new interface driver usbfs
[    0.238198] usbcore: registered new interface driver hub
[    0.238198] usbcore: registered new device driver usb
[    0.238198] pps_core: LinuxPPS API ver. 1 registered
[    0.238198] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.238198] PTP clock support registered
[    0.238198] EDAC MC: Ver: 3.0.0
[    0.238198] efivars: Registered efivars operations
[    0.238198] NetLabel: Initializing
[    0.238198] NetLabel:  domain hash size = 128
[    0.238198] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.238198] NetLabel:  unlabeled traffic allowed by default
[    0.238198] mctp: management component transport protocol core
[    0.238198] NET: Registered PF_MCTP protocol family
[    0.238198] PCI: Using ACPI for IRQ routing
[    0.281808] PCI: pci_cache_line_size set to 64 bytes
[    0.281872] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.281873] e820: reserve RAM buffer [mem 0x8d84d000-0x8fffffff]
[    0.281874] e820: reserve RAM buffer [mem 0x8e9ac000-0x8fffffff]
[    0.281875] e820: reserve RAM buffer [mem 0x96827018-0x97ffffff]
[    0.281876] e820: reserve RAM buffer [mem 0x96836018-0x97ffffff]
[    0.281877] e820: reserve RAM buffer [mem 0x96f8f000-0x97ffffff]
[    0.281878] e820: reserve RAM buffer [mem 0x994f6000-0x9bffffff]
[    0.281879] e820: reserve RAM buffer [mem 0x9b846000-0x9bffffff]
[    0.281880] e820: reserve RAM buffer [mem 0x9b86a000-0x9bffffff]
[    0.281880] e820: reserve RAM buffer [mem 0x9b9af000-0x9bffffff]
[    0.281881] e820: reserve RAM buffer [mem 0x9f000000-0x9fffffff]
[    0.281882] e820: reserve RAM buffer [mem 0x45e000000-0x45fffffff]
[    0.281911] pci 0000:01:00.0: vgaarb: setting as boot VGA device
[    0.281911] pci 0000:01:00.0: vgaarb: bridge control possible
[    0.281911] pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.281911] vgaarb: loaded
[    0.281911] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.281911] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.284435] clocksource: Switched to clocksource tsc-early
[    0.291679] VFS: Disk quotas dquot_6.6.0
[    0.291694] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.291785] AppArmor: AppArmor Filesystem Enabled
[    0.291823] pnp: PnP ACPI init
[    0.291923] system 00:00: [mem 0x40000000-0x403fffff] has been reserved
[    0.292193] system 00:01: [io  0x0280-0x028f] has been reserved
[    0.292195] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.292196] system 00:01: [io  0x02a0-0x02bf] has been reserved
[    0.292197] system 00:01: [io  0x02c0-0x02cf] has been reserved
[    0.292316] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.292318] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.292413] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.292605] system 00:04: [io  0x1800-0x18fe] could not be reserved
[    0.292607] system 00:04: [mem 0xfd000000-0xfd69ffff] has been reserved
[    0.292608] system 00:04: [mem 0xfd6c0000-0xfd6cffff] has been reserved
[    0.292609] system 00:04: [mem 0xfd6f0000-0xfdffffff] has been reserved
[    0.292610] system 00:04: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.292611] system 00:04: [mem 0xfe200000-0xfe7fffff] has been reserved
[    0.292613] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.292860] system 00:05: [io  0x2000-0x20fe] has been reserved
[    0.293088] system 00:06: [mem 0xfd6e0000-0xfd6effff] has been reserved
[    0.293090] system 00:06: [mem 0xfd6d0000-0xfd6dffff] has been reserved
[    0.293091] system 00:06: [mem 0xfd6b0000-0xfd6bffff] has been reserved
[    0.293092] system 00:06: [mem 0xfd6a0000-0xfd6affff] has been reserved
[    0.293601] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.293603] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.293604] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.293605] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.293606] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.293607] system 00:07: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.293609] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.293610] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.293915] system 00:08: [mem 0xfe038000-0xfe038fff] has been reserved
[    0.294299] pnp: PnP ACPI: found 9 devices
[    0.299628] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.299668] NET: Registered PF_INET protocol family
[    0.299768] IP idents hash table entries: 262144 (order: 9, 2097152 bytes, linear)
[    0.301922] tcp_listen_portaddr_hash hash table entries: 8192 (order: 5, 131072 bytes, linear)
[    0.301946] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, linear)
[    0.301998] TCP established hash table entries: 131072 (order: 8, 1048576 bytes, linear)
[    0.302159] TCP bind hash table entries: 65536 (order: 9, 2097152 bytes, linear)
[    0.302337] TCP: Hash tables configured (established 131072 bind 65536)
[    0.302397] MPTCP token hash table entries: 16384 (order: 6, 393216 bytes, linear)
[    0.302432] UDP hash table entries: 8192 (order: 6, 262144 bytes, linear)
[    0.302463] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes, linear)
[    0.302505] NET: Registered PF_UNIX/PF_LOCAL protocol family
[    0.302511] NET: Registered PF_XDP protocol family
[    0.302520] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.302523] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.302525] pci 0000:00:01.0:   bridge window [mem 0xaa000000-0xab0fffff]
[    0.302527] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.302530] pci 0000:00:1d.0: PCI bridge to [bus 02]
[    0.302535] pci 0000:00:1d.0:   bridge window [io  0x4000-0x4fff]
[    0.302538] pci 0000:00:1d.0:   bridge window [mem 0xab300000-0xab3fffff]
[    0.302543] pci 0000:00:1d.3: PCI bridge to [bus 03]
[    0.302544] pci 0000:00:1d.3:   bridge window [io  0x3000-0x3fff]
[    0.302547] pci 0000:00:1d.3:   bridge window [mem 0xab200000-0xab2fffff]
[    0.302552] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.302554] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.302555] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.302556] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff window]
[    0.302557] pci_bus 0000:00: resource 8 [mem 0xa0000000-0xdfffffff window]
[    0.302558] pci_bus 0000:00: resource 9 [mem 0xfc800000-0xfe7fffff window]
[    0.302559] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.302560] pci_bus 0000:01: resource 1 [mem 0xaa000000-0xab0fffff]
[    0.302561] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.302562] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.302563] pci_bus 0000:02: resource 1 [mem 0xab300000-0xab3fffff]
[    0.302564] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.302565] pci_bus 0000:03: resource 1 [mem 0xab200000-0xab2fffff]
[    0.302956] pci 0000:01:00.1: extending delay after power-on from D3hot to 20 msec
[    0.302978] pci 0000:01:00.1: D0 power state depends on 0000:01:00.0
[    0.302990] PCI: CLS 64 bytes, default 64
[    0.303026] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.303027] software IO TLB: mapped [mem 0x00000000879b0000-0x000000008b9b0000] (64MB)
[    0.303055] Trying to unpack rootfs image as initramfs...
[    0.303196] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.303514] Initialise system trusted keyrings
[    0.303520] Key type blacklist registered
[    0.303556] workingset: timestamp_bits=36 max_order=22 bucket_order=0
[    0.303568] zbud: loaded
[    0.303712] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.303769] fuse: init (API version 7.38)
[    0.303853] integrity: Platform Keyring initialized
[    0.303857] integrity: Machine keyring initialized
[    0.309532] Key type asymmetric registered
[    0.309535] Asymmetric key parser 'x509' registered
[    0.309551] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 243)
[    0.309578] io scheduler mq-deadline registered
[    0.310194] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.310234] efifb: probing for efifb
[    0.310248] efifb: showing boot graphics
[    0.316042] efifb: framebuffer at 0xa0000000, using 8640k, total 8640k
[    0.316044] efifb: mode is 1920x1080x32, linelength=8192, pages=1
[    0.316045] efifb: scrolling: redraw
[    0.316045] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.316111] Console: switching to colour frame buffer device 240x67
[    0.321593] fb0: EFI VGA frame buffer device
[    0.321829] Monitor-Mwait will be used to enter C-1 state
[    0.321833] Monitor-Mwait will be used to enter C-2 state
[    0.321835] ACPI: \_SB_.PR00: Found 2 idle states
[    0.322144] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.322164] ACPI: button: Sleep Button [SLPB]
[    0.322187] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.322200] ACPI: button: Power Button [PWRB]
[    0.322222] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.322252] ACPI: button: Power Button [PWRF]
[    0.322636] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.343797] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.345320] Linux agpgart interface v0.103
[    0.346588] loop: module loaded
[    0.346767] tun: Universal TUN/TAP device driver, 1.6
[    0.346788] PPP generic driver version 2.4.2
[    0.346870] i8042: PNP: No PS/2 controller found.
[    0.346897] mousedev: PS/2 mouse device common for all mice
[    0.346968] rtc_cmos rtc_cmos: RTC can wake from S4
[    0.347881] rtc_cmos rtc_cmos: registered as rtc0
[    0.348070] rtc_cmos rtc_cmos: setting system clock to 2024-01-23T08:18:20 UTC (1705997900)
[    0.348094] rtc_cmos rtc_cmos: alarms up to one month, y3k, 114 bytes nvram
[    0.348100] i2c_dev: i2c /dev entries driver
[    0.348333] device-mapper: core: CONFIG_IMA_DISABLE_HTABLE is disabled. Duplicate IMA measurements will not be recorded in the IMA log.
[    0.348342] device-mapper: uevent: version 1.0.3
[    0.348372] device-mapper: ioctl: 4.48.0-ioctl (2023-03-01) initialised: dm-devel@redhat.com
[    0.348388] platform eisa.0: Probing EISA bus 0
[    0.348391] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.348393] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.348394] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.348395] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.348396] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.348396] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.348397] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.348398] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.348399] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.348400] platform eisa.0: EISA: Detected 0 cards
[    0.348403] intel_pstate: Intel P-state driver initializing
[    0.348762] ledtrig-cpu: registered to indicate activity on CPUs
[    0.348812] intel_pmc_core INT33A1:00:  initialized
[    0.348866] drop_monitor: Initializing network drop monitor service
[    0.357297] NET: Registered PF_INET6 protocol family
[    0.551469] Freeing initrd memory: 68548K
[    0.555161] Segment Routing with IPv6
[    0.555183] In-situ OAM (IOAM) with IPv6
[    0.555206] NET: Registered PF_PACKET protocol family
[    0.555244] Key type dns_resolver registered
[    0.555882] microcode: Microcode Update Driver: v2.2.
[    0.555887] IPI shorthand broadcast: enabled
[    0.556841] sched_clock: Marking stable (556001286, 443862)->(558030959, -1585811)
[    0.557004] registered taskstats version 1
[    0.557442] Loading compiled-in X.509 certificates
[    0.557833] Loaded X.509 cert 'Build time autogenerated kernel key: 605c7c135229ebe23ab6a6fa2965fd12055e3c58'
[    0.558155] Loaded X.509 cert 'Canonical Ltd. Live Patch Signing: 14df34d1a87cf37625abec039ef2bf521249b969'
[    0.558470] Loaded X.509 cert 'Canonical Ltd. Kernel Module Signing: 88f752e560a1e0737e31163a466ad7b70a850c19'
[    0.558471] blacklist: Loading compiled-in revocation X.509 certificates
[    0.558481] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing: 61482aa2830d0ab2ad5af10b7250da9033ddcef0'
[    0.558490] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2017): 242ade75ac4a15e50d50c84b0d45ff3eae707a03'
[    0.558500] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (ESM 2018): 365188c1d374d6b07c3c8f240f8ef722433d6a8b'
[    0.558508] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2019): c0746fd6c5da3ae827864651ad66ae47fe24b3e8'
[    0.558518] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v1): a8d54bbb3825cfb94fa13c9f8a594a195c107b8d'
[    0.558528] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v2): 4cf046892d6fd3c9a5b03f98d845f90851dc6a8c'
[    0.558536] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v3): 100437bb6de6e469b581e61cd66bce3ef4ed53af'
[    0.558546] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (Ubuntu Core 2019): c1d57b8f6b743f23ee41f4f7ee292f06eecadfb9'
[    0.559590] Key type .fscrypt registered
[    0.559591] Key type fscrypt-provisioning registered
[    0.561364] Key type encrypted registered
[    0.561367] AppArmor: AppArmor sha1 policy hashing enabled
[    0.561648] ima: No TPM chip found, activating TPM-bypass!
[    0.561650] Loading compiled-in module X.509 certificates
[    0.562009] Loaded X.509 cert 'Build time autogenerated kernel key: 605c7c135229ebe23ab6a6fa2965fd12055e3c58'
[    0.562011] ima: Allocated hash algorithm: sha1
[    0.562015] ima: No architecture policies found
[    0.562021] evm: Initialising EVM extended attributes:
[    0.562021] evm: security.selinux
[    0.562022] evm: security.SMACK64
[    0.562023] evm: security.SMACK64EXEC
[    0.562023] evm: security.SMACK64TRANSMUTE
[    0.562024] evm: security.SMACK64MMAP
[    0.562024] evm: security.apparmor
[    0.562024] evm: security.ima
[    0.562025] evm: security.capability
[    0.562025] evm: HMAC attrs: 0x1
[    0.562213] PM:   Magic number: 8:814:321
[    0.562245] tty tty46: hash matches
[    0.668562] RAS: Correctable Errors collector initialized.
[    0.668592] clk: Disabling unused clocks
[    0.669413] Freeing unused decrypted memory: 2036K
[    0.669843] Freeing unused kernel image (initmem) memory: 4792K
[    0.669846] Write protecting the kernel read-only data: 34816k
[    0.670142] Freeing unused kernel image (rodata/data gap) memory: 1156K
[    0.681709] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    0.681719] Run /init as init process
[    0.681720]   with arguments:
[    0.681721]     /init
[    0.681722]     splash
[    0.681722]   with environment:
[    0.681723]     HOME=/
[    0.681723]     TERM=linux
[    0.681724]     BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic
[    0.751191] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.751198] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.752266] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x110 quirks 0x0000000000009810
[    0.752474] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.752478] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.752480] xhci_hcd 0000:00:14.0: Host supports USB 3.1 Enhanced SuperSpeed
[    0.752499] ahci 0000:00:17.0: version 3.0
[    0.752506] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 6.05
[    0.752507] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.752508] usb usb1: Product: xHCI Host Controller
[    0.752509] usb usb1: Manufacturer: Linux 6.5.0-14-generic xhci-hcd
[    0.752510] usb usb1: SerialNumber: 0000:00:14.0
[    0.752936] hub 1-0:1.0: USB hub found
[    0.752955] hub 1-0:1.0: 16 ports detected
[    0.753254] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 6.05
[    0.753256] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.753257] usb usb2: Product: xHCI Host Controller
[    0.753258] usb usb2: Manufacturer: Linux 6.5.0-14-generic xhci-hcd
[    0.753259] usb usb2: SerialNumber: 0000:00:14.0
[    0.753325] hub 2-0:1.0: USB hub found
[    0.753336] hub 2-0:1.0: 8 ports detected
[    0.754059] r8169 0000:02:00.0: enabling device (0000 -> 0003)
[    0.754174] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.755622] i801_smbus 0000:00:1f.4: SMBus using PCI interrupt
[    0.757091] i2c i2c-0: 2/2 memory slots populated (from DMI)
[    0.757549] i2c i2c-0: Successfully instantiated SPD at 0x50
[    0.762853] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.762860] ahci 0000:00:17.0: flags: 64bit ncq sntf clo only pio slum part ems deso sadm sds apst 
[    0.770410] r8169 0000:02:00.0 eth0: RTL8168h/8111h, 1c:61:b4:6d:38:4f, XID 541, IRQ 126
[    0.770416] r8169 0000:02:00.0 eth0: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    0.770449] r8169 0000:03:00.0: enabling device (0000 -> 0003)
[    0.770592] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.790083] r8169 0000:03:00.0 eth1: RTL8168h/8111h, a8:a1:59:6e:1f:8b, XID 541, IRQ 127
[    0.790087] r8169 0000:03:00.0 eth1: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    0.820891] scsi host0: ahci
[    0.821023] scsi host1: ahci
[    0.821115] scsi host2: ahci
[    0.821194] scsi host3: ahci
[    0.821300] scsi host4: ahci
[    0.821387] scsi host5: ahci
[    0.821421] ata1: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419100 irq 125
[    0.821423] ata2: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419180 irq 125
[    0.821424] ata3: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419200 irq 125
[    0.821426] ata4: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419280 irq 125
[    0.821428] ata5: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419300 irq 125
[    0.821430] ata6: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419380 irq 125
[    0.829336] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    0.856586] r8169 0000:03:00.0 enp3s0: renamed from eth1
[    1.012475] usb 1-6: new low-speed USB device number 2 using xhci_hcd
[    1.135541] ata3: SATA link down (SStatus 4 SControl 300)
[    1.135840] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.135854] ata2: SATA link down (SStatus 4 SControl 300)
[    1.135870] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.135885] ata5: SATA link down (SStatus 4 SControl 300)
[    1.135899] ata6: SATA link down (SStatus 4 SControl 300)
[    1.136645] ata1.00: ATA-10: INTEL SSDSC2KW240H6,  LSBG200, max UDMA/133
[    1.136733] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    1.137399] ata1.00: Features: Dev-Sleep
[    1.138505] ata1.00: configured for UDMA/133
[    1.138631] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSC2KW24 G200 PQ: 0 ANSI: 5
[    1.138957] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.138983] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/224 GiB)
[    1.138991] sd 0:0:0:0: [sda] Write Protect is off
[    1.138992] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.138999] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.139007] sd 0:0:0:0: [sda] Preferred minimum I/O size 512 bytes
[    1.140472]  sda: sda1 sda2
[    1.140543] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.148546] ata4.00: ATA-9: INTEL SSDSC2BW120A4, DC32, max UDMA/133
[    1.150450] ata4.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    1.176782] ata4.00: Features: Dev-Sleep
[    1.188015] usb 1-6: New USB device found, idVendor=04d9, idProduct=1503, bcdDevice= 3.10
[    1.188017] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.188019] usb 1-6: Product: USB Keyboard
[    1.188020] usb 1-6: Manufacturer:  
[    1.216699] ata4.00: configured for UDMA/133
[    1.216801] scsi 3:0:0:0: Direct-Access     ATA      INTEL SSDSC2BW12 DC32 PQ: 0 ANSI: 5
[    1.217209] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.217228] sd 3:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    1.217234] sd 3:0:0:0: [sdb] Write Protect is off
[    1.217236] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.217242] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.217249] sd 3:0:0:0: [sdb] Preferred minimum I/O size 512 bytes
[    1.218334]  sdb: sdb1
[    1.218379] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.316528] usb 1-9: new full-speed USB device number 3 using xhci_hcd
[    1.320498] tsc: Refined TSC clocksource calibration: 3695.998 MHz
[    1.320503] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x6a8d2284b57, max_idle_ns: 881590451434 ns
[    1.320538] clocksource: Switched to clocksource tsc
[    1.467767] usb 1-9: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.10
[    1.467770] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.467771] usb 1-9: Product: USB Receiver
[    1.467772] usb 1-9: Manufacturer: Logitech
[    1.481248] hid: raw HID events driver (C) Jiri Kosina
[    1.514957] usbcore: registered new interface driver usbhid
[    1.514965] usbhid: USB HID core driver
[    1.521348] input:   USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04D9:1503.0001/input/input3
[    1.580789] hid-generic 0003:04D9:1503.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:14.0-6/input0
[    1.581177] input:   USB Keyboard System Control as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input4
[    1.640649] input:   USB Keyboard Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input5
[    1.640886] hid-generic 0003:04D9:1503.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:14.0-6/input1
[    1.641337] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:046D:C52B.0003/input/input6
[    1.700688] hid-generic 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:14.0-9/input0
[    1.701453] input: Logitech USB Receiver Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input7
[    1.701719] input: Logitech USB Receiver Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input8
[    1.760670] input: Logitech USB Receiver System Control as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input9
[    1.761057] hid-generic 0003:046D:C52B.0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-9/input1
[    1.761725] hid-generic 0003:046D:C52B.0005: hiddev1,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-9/input2
[    1.977348] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-9/input2

```

---

### Post by kotgc on 2024-01-23
Code 2/2, code 1/2 on post #112.

```

[    2.099766] input: Logitech Wireless Device PID:402d Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input11
[    2.100083] input: Logitech Wireless Device PID:402d Mouse as 
/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input12[     2.100630] hid-generic 0003:046D:402D.0006: input,hidraw3: USB HID v1.11  Keyboard [Logitech Wireless Device PID:402d] on  usb-0000:00:14.0-9/input2:1
[    2.207871] logitech-hidpp-device  0003:046D:402D.0006: hidraw3: USB HID v1.11 Keyboard [Logitech M560] on  usb-0000:00:14.0-9/input2:1
[    2.246007] EXT4-fs (sda2): mounted  filesystem 8db91722-3256-4c30-b0cf-4e75ea66d3b8 ro with ordered data  mode. Quota mode: none.
[    2.353573] systemd[1]: Inserted module 'autofs4'
[     2.377512] systemd[1]: systemd 249.11-0ubuntu3.12 running in system mode  (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS  +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD  +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4  +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)
[    2.377578] systemd[1]: Detected architecture x86-64.
[    2.377916] systemd[1]: Hostname set to <ubuntu>.
[    2.411628] systemd[1]: memfd_create() called without MFD_EXEC or MFD_NOEXEC_SEAL set
[    2.435584] block sda: the capability attribute has been deprecated.
[    2.512808] systemd[1]: Queued start job for default target Graphical Interface.
[    2.536828] systemd[1]: Created slice Slice /system/modprobe.
[    2.537041] systemd[1]: Created slice Slice /system/systemd-fsck.
[    2.537176] systemd[1]: Created slice User and Session Slice.
[    2.537226] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    2.537338] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    2.537383] systemd[1]: Reached target User and Group Name Lookups.
[    2.537393] systemd[1]: Reached target Remote File Systems.
[    2.537402] systemd[1]: Reached target Slice Units.
[    2.537412] systemd[1]: Reached target Mounting snaps.
[    2.537430] systemd[1]: Reached target Local Verity Protected Volumes.
[    2.537509] systemd[1]: Listening on Syslog Socket.
[    2.537574] systemd[1]: Listening on fsck to fsckd communication Socket.
[    2.537611] systemd[1]: Listening on initctl Compatibility Named Pipe.
[    2.537729] systemd[1]: Listening on Journal Audit Socket.
[    2.537785] systemd[1]: Listening on Journal Socket (/dev/log).
[    2.537852] systemd[1]: Listening on Journal Socket.
[    2.538076] systemd[1]: Listening on udev Control Socket.
[    2.538137] systemd[1]: Listening on udev Kernel Socket.
[    2.538667] systemd[1]: Mounting Huge Pages File System...
[    2.539196] systemd[1]: Mounting POSIX Message Queue File System...
[    2.539773] systemd[1]: Mounting Kernel Debug File System...
[    2.540327] systemd[1]: Mounting Kernel Trace File System...
[    2.541537] systemd[1]: Starting Journal Service...
[    2.542200] systemd[1]: Starting Set the console keyboard layout...
[    2.542810] systemd[1]: Starting Create List of Static Device Nodes...
[    2.543391] systemd[1]: Starting Load Kernel Module configfs...
[    2.544056] systemd[1]: Starting Load Kernel Module drm...
[    2.544955] systemd[1]: Starting Load Kernel Module efi_pstore...
[    2.545885] systemd[1]: Starting Load Kernel Module fuse...
[    2.546022] systemd[1]: Condition check resulted in File System Check on Root Device being skipped.
[    2.547563] systemd[1]: Starting Load Kernel Modules...
[    2.548161] pstore: Using crash dump compression: deflate
[    2.548284] systemd[1]: Starting Remount Root and Kernel File Systems...
[    2.549014] systemd[1]: Starting Coldplug All udev Devices...
[    2.549903] systemd[1]: Mounted Huge Pages File System.
[    2.550012] systemd[1]: Mounted POSIX Message Queue File System.
[    2.550074] systemd[1]: Mounted Kernel Debug File System.
[    2.550123] systemd[1]: Mounted Kernel Trace File System.
[    2.550304] systemd[1]: Finished Create List of Static Device Nodes.
[    2.550466] systemd[1]: modprobe@configfs.service: Deactivated successfully.
[    2.550595] systemd[1]: Finished Load Kernel Module configfs.
[    2.550733] systemd[1]: modprobe@fuse.service: Deactivated successfully.
[    2.550858] systemd[1]: Finished Load Kernel Module fuse.
[    2.551553] systemd[1]: Mounting FUSE Control File System...
[    2.552312] systemd[1]: Mounting Kernel Configuration File System...
[    2.552730] pstore: Registered efi_pstore as persistent store backend
[    2.553191] systemd[1]: modprobe@efi_pstore.service: Deactivated successfully.
[    2.553404] systemd[1]: Finished Load Kernel Module efi_pstore.
[    2.554722] systemd[1]: Mounted FUSE Control File System.
[    2.554787] systemd[1]: Mounted Kernel Configuration File System.
[    2.557310] EXT4-fs (sda2): re-mounted 8db91722-3256-4c30-b0cf-4e75ea66d3b8 r/w. Quota mode: none.
[    2.558175] systemd[1]: Finished Remount Root and Kernel File Systems.
[    2.558733] systemd[1]: Activating swap /swapfile...
[    2.558787] systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
[    2.559407] systemd[1]: Starting Load/Save Random Seed...
[    2.560002] systemd[1]: Starting Create System Users...
[    2.562530] Adding 2097148k swap on /swapfile.  Priority:-2 extents:17 across:233758720k SSFS
[    2.562582] systemd[1]: Activated swap /swapfile.
[    2.562618] systemd[1]: Reached target Swaps.
[    2.571613] ACPI: bus type drm_connector registered
[    2.573112] systemd[1]: modprobe@drm.service: Deactivated successfully.
[    2.573365] systemd[1]: Finished Load Kernel Module drm.
[    2.574397] systemd[1]: Finished Load/Save Random Seed.
[    2.574542] systemd[1]: Condition check resulted in First Boot Complete being skipped.
[    2.577272] lp: driver loaded but no devices found
[    2.578240] systemd[1]: Finished Set the console keyboard layout.
[    2.579590] ppdev: user-space parallel port driver
[    2.580692] systemd[1]: Finished Create System Users.
[    2.581343] systemd[1]: Starting Create Static Device Nodes in /dev...
[    2.581454] systemd[1]: Started Journal Service.
[    2.585306] systemd-journald[256]: Received client request to flush runtime journal.
[    2.596794] loop0: detected capacity change from 0 to 8
[    2.596828] loop1: detected capacity change from 0 to 129944
[    2.598422] loop2: detected capacity change from 0 to 151296
[    2.599221] loop3: detected capacity change from 0 to 485800
[    2.601334] loop4: detected capacity change from 0 to 716176
[    2.602007] loop5: detected capacity change from 0 to 994336
[    2.603448] loop6: detected capacity change from 0 to 187776
[    2.604991] loop7: detected capacity change from 0 to 25240
[    2.606032] loop8: detected capacity change from 0 to 109072
[    2.607070] loop9: detected capacity change from 0 to 904
[    2.748031] intel_pch_thermal 0000:00:12.0: enabling device (0000 -> 0002)
[    2.751989] ee1004 0-0050: 512 byte EE1004-compliant SPD EEPROM, read-only
[    2.805849] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    2.818112] RAPL PMU: API unit is 2^-32 Joules, 3 fixed counters, 655360 ms ovfl timer
[    2.818116] RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
[    2.818117] RAPL PMU: hw unit of domain package 2^-14 Joules
[    2.818118] RAPL PMU: hw unit of domain dram 2^-14 Joules
[    2.818732] spi-nor spi0.0: mx25l12805d (16384 Kbytes)
[    2.823692] cryptd: max_cpu_qlen set to 1000
[    2.829457] Creating 1 MTD partitions on "0000:00:1f.5":
[    2.829462] 0x000000000000-0x000001000000 : "BIOS"
[    2.837042] AVX2 version of gcm_enc/dec engaged.
[    2.837086] AES CTR mode by8 optimization enabled
[    3.096340] Console: switching to colour dummy device 80x25
[    3.096388] nouveau 0000:01:00.0: vgaarb: deactivate vga console
[    3.096461] nouveau 0000:01:00.0: NVIDIA GK208B (b060b0b1)
[    3.101990] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.102474] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    3.102562] snd_hda_intel 0000:01:00.1: Disabling MSI
[    3.102567] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[     3.126366] audit: type=1400 audit(1705997903.272:2): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="libreoffice-senddoc"  pid=549 comm="apparmor_parser"
[    3.126776] audit: type=1400  audit(1705997903.272:3): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="lsb_release" pid=542 comm="apparmor_parser"
[     3.126888] audit: type=1400 audit(1705997903.272:4): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="nvidia_modprobe"  pid=543 comm="apparmor_parser"
[    3.126892] audit: type=1400  audit(1705997903.272:5): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="nvidia_modprobe//kmod" pid=543  comm="apparmor_parser"
[    3.127318] audit: type=1400  audit(1705997903.272:6): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/bin/man" pid=546 comm="apparmor_parser"
[     3.127323] audit: type=1400 audit(1705997903.272:7): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="man_filter" pid=546  comm="apparmor_parser"
[    3.127325] audit: type=1400  audit(1705997903.272:8): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="man_groff" pid=546 comm="apparmor_parser"
[     3.127721] audit: type=1400 audit(1705997903.272:9): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="libreoffice-oosplash" pid=548 comm="apparmor_parser"
[     3.129060] audit: type=1400 audit(1705997903.276:10): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="libreoffice-xpdfimport" pid=551 comm="apparmor_parser"
[    3.131963] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    3.132157] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[    3.132345] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[    3.132396] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    3.141779] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC897: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    3.141786] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.141788] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    3.141790] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.141791] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.141793] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    3.141795] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    3.141796] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    3.172344] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[    3.172406] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input21
[    3.172490] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input22
[    3.172598] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input23
[    3.172654] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input24
[    3.209325] nouveau 0000:01:00.0: bios: version 80.28.b8.00.05
[    3.216406] nouveau 0000:01:00.0: fb: 2048 MiB GDDR5
[    3.220272] intel_tcc_cooling: Programmable TCC Offset detected
[    3.224351] intel_rapl_common: Found RAPL domain package
[    3.224354] intel_rapl_common: Found RAPL domain core
[    3.224355] intel_rapl_common: Found RAPL domain dram
[    3.224358] intel_rapl_common: package-0:package:long_term locked by BIOS
[    3.224359] intel_rapl_common: package-0:package:short_term locked by BIOS
[    4.524772] nouveau 0000:01:00.0: DRM: VRAM: 2048 MiB
[    4.524777] nouveau 0000:01:00.0: DRM: GART: 1048576 MiB
[    4.524780] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
[    4.524782] nouveau 0000:01:00.0: DRM: DCB version 4.0
[    4.524784] nouveau 0000:01:00.0: DRM: DCB outp 00: 01000f02 00020030
[    4.524786] nouveau 0000:01:00.0: DRM: DCB outp 01: 02011f62 00020010
[    4.524788] nouveau 0000:01:00.0: DRM: DCB outp 02: 02022f10 00000000
[    4.524790] nouveau 0000:01:00.0: DRM: DCB conn 00: 00001031
[    4.524791] nouveau 0000:01:00.0: DRM: DCB conn 01: 00002161
[    4.524792] nouveau 0000:01:00.0: DRM: DCB conn 02: 00000200
[    4.525822] nouveau 0000:01:00.0: DRM: MM: using COPY for buffer copies
[    4.526721] snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops nv50_audio_component_bind_ops [nouveau])
[    4.527355] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 0
[    4.669091] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[    4.688551] fbcon: nouveaudrmfb (fb0) is primary device
[    4.810966] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[    4.862640] Console: switching to colour frame buffer device 240x67
[    4.864055] nouveau 0000:01:00.0: [drm] fb0: nouveaudrmfb frame buffer device
[    4.884469] nouveau 0000:01:00.0: DRM: Disabling PCI power management to avoid bug
[    5.025343] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[    5.147313] kauditd_printk_skb: 33 callbacks suppressed
[     5.147316] audit: type=1400 audit(1705997905.292:44): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="snap.firefox.geckodriver" pid=583 comm="apparmor_parser"
[    5.167285] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[     5.187073] audit: type=1400 audit(1705997905.332:45): apparmor="STATUS"  operation="profile_load" profile="unconfined"  name="snap.snapd-desktop-integration.snapd-desktop-integration" pid=607  comm="apparmor_parser"
[    5.263891] audit: type=1400  audit(1705997905.408:46): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="snap.firefox.firefox" pid=582  comm="apparmor_parser"
[    5.313687] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[     5.548666] audit: type=1400 audit(1705997905.696:47): apparmor="DENIED"  operation="capable" class="cap" profile="/usr/sbin/cupsd" pid=800  comm="cupsd" capability=12  capname="net_admin"
[    5.604472] Generic FE-GE Realtek PHY r8169-0-200:00: attached PHY driver (mii_bus:phy_addr=r8169-0-200:00, irq=MAC)
[    5.792615] r8169 0000:02:00.0 enp2s0: Link is Down
[    5.820524] Generic FE-GE Realtek PHY r8169-0-300:00: attached PHY driver (mii_bus:phy_addr=r8169-0-300:00, irq=MAC)
[    6.016659] r8169 0000:03:00.0 enp3s0: Link is Down
[    6.169936] loop10: detected capacity change from 0 to 8
[     6.334063] audit: type=1400 audit(1705997906.480:48): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=898  comm="apparmor_parser"
[    6.372560] audit: type=1400  audit(1705997906.520:49): apparmor="STATUS" operation="profile_replace"  profile="unconfined"  name="/snap/snapd/19457/usr/lib/snapd/snap-confine//mount-namespace-capture-helper"  pid=898 comm="apparmor_parser"
[    7.102731] audit: type=1400  audit(1705997907.248:50): apparmor="STATUS" operation="profile_replace"  info="same as current profile, skipping" profile="unconfined"  name="snap-update-ns.firefox" pid=902 comm="apparmor_parser"
[     7.163557] audit: type=1400 audit(1705997907.308:51): apparmor="STATUS"  operation="profile_replace" info="same as current profile, skipping"  profile="unconfined" name="snap-update-ns.snap-store" pid=900  comm="apparmor_parser"
[    7.237752] audit: type=1400  audit(1705997907.384:52): apparmor="STATUS" operation="profile_replace"  info="same as current profile, skipping" profile="unconfined"  name="snap-update-ns.snapd-desktop-integration" pid=901  comm="apparmor_parser"
[    7.246966] audit: type=1400  audit(1705997907.392:53): apparmor="STATUS" operation="profile_replace"  info="same as current profile, skipping" profile="unconfined"  name="snap.snap-store.hook.configure" pid=904 comm="apparmor_parser"
[    9.118993] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[    9.220324] r8169 0000:02:00.0 enp2s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   15.749848] kauditd_printk_skb: 11 callbacks suppressed
[    15.749850] audit: type=1400 audit(1705997915.896:65): apparmor="DENIED"  operation="capable" class="cap"  profile="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=1013  comm="snap-confine" capability=12  capname="net_admin"
[   15.749856]  audit: type=1400 audit(1705997915.896:66): apparmor="DENIED"  operation="capable" class="cap"  profile="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=1013  comm="snap-confine" capability=38  capname="perfmon"
[   16.103248] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[   17.333745] rfkill: input handler disabled
[    23.186651] audit: type=1400 audit(1705997923.332:67): apparmor="DENIED"  operation="capable" class="cap"  profile="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=1425  comm="snap-confine" capability=12  capname="net_admin"
[   23.186668]  audit: type=1400 audit(1705997923.332:68): apparmor="DENIED"  operation="capable" class="cap"  profile="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=1425  comm="snap-confine" capability=38  capname="perfmon"
[   23.413308] rfkill: input handler enabled
[   23.797142] nouveau 0000:01:00.0: DRM: [DRM/00000002:dac-0000-0f02] [LOAD_DETECT data:00000154] load:07 (ret:-5)
[   24.721361] rfkill: input handler disabled
[   26.005740] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.009738] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.015738] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.039760] logitech-hidpp-device 0003:046D:402D.0006: HID++ 2.0 device connected.
[    26.286577] audit: type=1400 audit(1705997926.432:69): apparmor="DENIED"  operation="capable" class="cap"  profile="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=2103  comm="snap-confine" capability=12  capname="net_admin"
[   26.286584]  audit: type=1400 audit(1705997926.432:70): apparmor="DENIED"  operation="capable" class="cap"  profile="/snap/snapd/19457/usr/lib/snapd/snap-confine" pid=2103  comm="snap-confine" capability=38  capname="perfmon"
[   26.543763] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.557758] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.573761] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.589736] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.605757] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.619766] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.635734] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.651759] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[    26.659802] input: Logitech Wireless Mouse M560 as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input25
[    46.529588] audit: type=1400 audit(1705997945.872:71): apparmor="DENIED"  operation="open" class="file" profile="snap-update-ns.firefox"  name="/var/lib/" pid=2326 comm="5" requested_mask="r" denied_mask="r"  fsuid=0 ouid=0
[   46.530068] audit: type=1400  audit(1705997945.872:72): apparmor="DENIED" operation="open"  class="file" profile="snap-update-ns.firefox" name="/var/lib/" pid=2326  comm="5" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[    47.696344] audit: type=1326 audit(1705997947.036:73): auid=1000 uid=1000  gid=1000 ses=3 subj=snap.firefox.firefox pid=2298 comm="firefox"  exe="/snap/firefox/2987/usr/lib/firefox/firefox" sig=0 arch=c000003e  syscall=314 compat=0 ip=0x7f762a27973d code=0x50000

```

---

### Post by kotgc on 2024-01-23
Just rebooted into grub to add nomodeset after quiet splash, and now Ubuntu has more black screens, Ubuntu's getting worse!
Here's the dmesg:
```

ubuntu@ubuntu:~$ sudo dmesg
[sudo] password for ubuntu: 
[    0.000000] microcode: updated early: 0xcc -> 0xf8, date = 2023-02-23
[    0.000000] Linux version 6.5.0-14-generic (buildd@lcy02-amd64-110) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov 20 18:15:30 UTC 2 (Ubuntu 6.5.0-14.14~22.04.1-generic 6.5.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic root=UUID=8db91722-3256-4c30-b0cf-4e75ea66d3b8 ro quiet splash nomodeset vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Hygon HygonGenuine
[    0.000000]   Centaur CentaurHauls
[    0.000000]   zhaoxin   Shanghai  
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000403fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040400000-0x000000008d84cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008d84e000-0x000000008e9abfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008e9ad000-0x000000009b845fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009b847000-0x000000009b869fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b86a000-0x000000009b86afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b86b000-0x000000009b9aefff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009dcff000-0x000000009effefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009efff000-0x000000009effffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f000000-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000045dffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x96852018-0x96872657] usable ==> usable
[    0.000000] e820: update [mem 0x96852018-0x96872657] usable ==> usable
[    0.000000] e820: update [mem 0x969cf018-0x969dd057] usable ==> usable
[    0.000000] e820: update [mem 0x969cf018-0x969dd057] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009efff] reserved
[    0.000000] reserve setup_data: [mem 0x000000000009f000-0x000000000009ffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000000a0000-0x00000000000fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000040000000-0x00000000403fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000040400000-0x000000008d84cfff] usable
[    0.000000] reserve setup_data: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
[    0.000000] reserve setup_data: [mem 0x000000008d84e000-0x000000008e9abfff] usable
[    0.000000] reserve setup_data: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
[    0.000000] reserve setup_data: [mem 0x000000008e9ad000-0x0000000096852017] usable
[    0.000000] reserve setup_data: [mem 0x0000000096852018-0x0000000096872657] usable
[    0.000000] reserve setup_data: [mem 0x0000000096872658-0x00000000969cf017] usable
[    0.000000] reserve setup_data: [mem 0x00000000969cf018-0x00000000969dd057] usable
[    0.000000] reserve setup_data: [mem 0x00000000969dd058-0x000000009b845fff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009b847000-0x000000009b869fff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b86a000-0x000000009b86afff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009b86b000-0x000000009b9aefff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
[    0.000000] reserve setup_data: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009dcff000-0x000000009effefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009efff000-0x000000009effffff] usable
[    0.000000] reserve setup_data: [mem 0x000000009f000000-0x000000009fffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000045dffffff] usable
[    0.000000] efi: EFI v2.7 by American Megatrends
[    0.000000] efi: ACPI=0x9dcbb000 ACPI 2.0=0x9dcbb014 SMBIOS=0x9eb75000 SMBIOS 3.0=0x9eb74000 MEMATTR=0x98d4c818 ESRT=0x994f6218 MOKvar=0x9eba6000 RNG=0x9db4d018 
[    0.000000] random: crng init done
[    0.000000] efi: Remove mem320: MMIO range=[0xe0000000-0xefffffff] (256MB) from e820 map
[    0.000000] e820: remove [mem 0xe0000000-0xefffffff] reserved
[    0.000000] efi: Not removing mem321: MMIO range=[0xfe000000-0xfe010fff] (68KB) from e820 map
[    0.000000] efi: Not removing mem322: MMIO range=[0xfec00000-0xfec00fff] (4KB) from e820 map
[    0.000000] efi: Not removing mem323: MMIO range=[0xfee00000-0xfee00fff] (4KB) from e820 map
[    0.000000] efi: Remove mem324: MMIO range=[0xff000000-0xffffffff] (16MB) from e820 map
[    0.000000] e820: remove [mem 0xff000000-0xffffffff] reserved
[    0.000000] secureboot: Secure boot disabled
[    0.000000] SMBIOS 3.2.0 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./H470M-HVS, BIOS P1.10 01/11/2021
[    0.000000] tsc: Detected 3700.000 MHz processor
[    0.000000] tsc: Detected 3699.850 MHz TSC
[    0.000519] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000521] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000532] last_pfn = 0x45e000 max_arch_pfn = 0x400000000
[    0.000536] MTRR map: 5 entries (3 fixed + 2 variable; max 23), built from 10 variable MTRRs
[    0.000538] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000934] last_pfn = 0x9f000 max_arch_pfn = 0x400000000
[    0.006998] esrt: Reserving ESRT space from 0x00000000994f6218 to 0x00000000994f6278.
[    0.007005] e820: update [mem 0x994f6000-0x994f6fff] usable ==> reserved
[    0.007058] Using GB pages for direct mapping
[    0.007887] secureboot: Secure boot disabled
[    0.007888] RAMDISK: [mem 0x91db5000-0x960a5fff]
[    0.007893] ACPI: Early table checksum verification disabled
[    0.007895] ACPI: RSDP 0x000000009DCBB014 000024 (v02 ALASKA)
[    0.007899] ACPI: XSDT 0x000000009DCBA728 0000BC (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007904] ACPI: FACP 0x000000009DBA8000 000114 (v06 ALASKA A M I    01072009 AMI  00010013)
[    0.007908] ACPI: DSDT 0x000000009DB65000 042272 (v02 ALASKA A M I    01072009 INTL 20160527)
[    0.007911] ACPI: FACS 0x000000009DCFE000 000040
[    0.007913] ACPI: MCFG 0x000000009DBAC000 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.007916] ACPI: SSDT 0x000000009DBA9000 0020AD (v02 CpuRef CpuSsdt  00003000 INTL 20160527)
[    0.007919] ACPI: FIDT 0x000000009DB64000 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007921] ACPI: AAFT 0x000000009DBAE000 0002DE (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.007924] ACPI: SSDT 0x000000009DB60000 0031DA (v02 SaSsdt SaSsdt   00003000 INTL 20160527)
[    0.007927] ACPI: SSDT 0x000000009DB5D000 002703 (v02 Intel  PegSsdt  00001000 INTL 20160527)
[    0.007929] ACPI: HPET 0x000000009DBAD000 000038 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007932] ACPI: NHLT 0x000000009DB5B000 001821 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.007934] ACPI: LPIT 0x000000009DB5A000 000094 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007937] ACPI: SSDT 0x000000009DB56000 0025B2 (v02 ALASKA TbtTypeC 00000000 INTL 20160527)
[    0.007939] ACPI: DBGP 0x000000009DB55000 000034 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007942] ACPI: DBG2 0x000000009DB54000 000054 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.007944] ACPI: SSDT 0x000000009DB52000 001B67 (v02 ALASKA UsbCTabl 00001000 INTL 20160527)
[    0.007947] ACPI: DMAR 0x000000009DB51000 000070 (v01 INTEL  EDK2     00000002      01000013)
[    0.007949] ACPI: BGRT 0x000000009DB50000 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007952] ACPI: WSMT 0x000000009DB59000 000028 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007954] ACPI: APIC 0x000000009DB4F000 0000BC (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.007957] ACPI: FPDT 0x000000009DB4E000 000044 (v01 ALASKA CML      01072009 AMI  01000013)
[    0.007959] ACPI: Reserving FACP table memory at [mem 0x9dba8000-0x9dba8113]
[    0.007960] ACPI: Reserving DSDT table memory at [mem 0x9db65000-0x9dba7271]
[    0.007961] ACPI: Reserving FACS table memory at [mem 0x9dcfe000-0x9dcfe03f]
[    0.007962] ACPI: Reserving MCFG table memory at [mem 0x9dbac000-0x9dbac03b]
[    0.007963] ACPI: Reserving SSDT table memory at [mem 0x9dba9000-0x9dbab0ac]
[    0.007963] ACPI: Reserving FIDT table memory at [mem 0x9db64000-0x9db6409b]
[    0.007964] ACPI: Reserving AAFT table memory at [mem 0x9dbae000-0x9dbae2dd]
[    0.007965] ACPI: Reserving SSDT table memory at [mem 0x9db60000-0x9db631d9]
[    0.007965] ACPI: Reserving SSDT table memory at [mem 0x9db5d000-0x9db5f702]
[    0.007966] ACPI: Reserving HPET table memory at [mem 0x9dbad000-0x9dbad037]
[    0.007967] ACPI: Reserving NHLT table memory at [mem 0x9db5b000-0x9db5c820]
[    0.007968] ACPI: Reserving LPIT table memory at [mem 0x9db5a000-0x9db5a093]
[    0.007968] ACPI: Reserving SSDT table memory at [mem 0x9db56000-0x9db585b1]
[    0.007969] ACPI: Reserving DBGP table memory at [mem 0x9db55000-0x9db55033]
[    0.007970] ACPI: Reserving DBG2 table memory at [mem 0x9db54000-0x9db54053]
[    0.007971] ACPI: Reserving SSDT table memory at [mem 0x9db52000-0x9db53b66]
[    0.007971] ACPI: Reserving DMAR table memory at [mem 0x9db51000-0x9db5106f]
[    0.007972] ACPI: Reserving BGRT table memory at [mem 0x9db50000-0x9db50037]
[    0.007973] ACPI: Reserving WSMT table memory at [mem 0x9db59000-0x9db59027]
[    0.007973] ACPI: Reserving APIC table memory at [mem 0x9db4f000-0x9db4f0bb]
[    0.007974] ACPI: Reserving FPDT table memory at [mem 0x9db4e000-0x9db4e043]
[    0.008231] No NUMA configuration found
[    0.008232] Faking a node at [mem 0x0000000000000000-0x000000045dffffff]
[    0.008241] NODE_DATA(0) allocated [mem 0x45dfd5000-0x45dffffff]
[    0.008411] Zone ranges:
[    0.008411]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.008413]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.008414]   Normal   [mem 0x0000000100000000-0x000000045dffffff]
[    0.008416]   Device   empty
[    0.008417] Movable zone start for each node
[    0.008418] Early memory node ranges
[    0.008419]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.008420]   node   0: [mem 0x000000000009f000-0x000000000009ffff]
[    0.008421]   node   0: [mem 0x0000000000100000-0x000000003fffffff]
[    0.008422]   node   0: [mem 0x0000000040400000-0x000000008d84cfff]
[    0.008422]   node   0: [mem 0x000000008d84e000-0x000000008e9abfff]
[    0.008423]   node   0: [mem 0x000000008e9ad000-0x000000009b845fff]
[    0.008424]   node   0: [mem 0x000000009b847000-0x000000009b869fff]
[    0.008425]   node   0: [mem 0x000000009b86b000-0x000000009b9aefff]
[    0.008425]   node   0: [mem 0x000000009efff000-0x000000009effffff]
[    0.008426]   node   0: [mem 0x0000000100000000-0x000000045dffffff]
[    0.008428] Initmem setup node 0 [mem 0x0000000000001000-0x000000045dffffff]
[    0.008431] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.008433] On node 0, zone DMA: 1 pages in unavailable ranges
[    0.008448] On node 0, zone DMA: 96 pages in unavailable ranges
[    0.010850] On node 0, zone DMA32: 1024 pages in unavailable ranges
[    0.010868] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.011088] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.011089] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.011091] On node 0, zone DMA32: 1 pages in unavailable ranges
[    0.011200] On node 0, zone DMA32: 13904 pages in unavailable ranges
[    0.026127] On node 0, zone Normal: 4096 pages in unavailable ranges
[    0.026191] On node 0, zone Normal: 8192 pages in unavailable ranges
[    0.026420] ACPI: PM-Timer IO Port: 0x1808
[    0.026425] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.026427] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.026428] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.026428] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.026429] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.026430] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.026430] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.026431] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.026465] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.026468] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.026469] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.026473] ACPI: Using ACPI (MADT) for SMP configuration information
[    0.026474] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.026482] e820: update [mem 0x96f8f000-0x96fcffff] usable ==> reserved
[    0.026496] TSC deadline timer available
[    0.026497] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.026517] PM: hibernation: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.026519] PM: hibernation: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.026521] PM: hibernation: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.026523] PM: hibernation: Registered nosave memory: [mem 0x40000000-0x403fffff]
[    0.026524] PM: hibernation: Registered nosave memory: [mem 0x8d84d000-0x8d84dfff]
[    0.026526] PM: hibernation: Registered nosave memory: [mem 0x8e9ac000-0x8e9acfff]
[    0.026528] PM: hibernation: Registered nosave memory: [mem 0x96852000-0x96852fff]
[    0.026529] PM: hibernation: Registered nosave memory: [mem 0x96872000-0x96872fff]
[    0.026531] PM: hibernation: Registered nosave memory: [mem 0x969cf000-0x969cffff]
[    0.026532] PM: hibernation: Registered nosave memory: [mem 0x969dd000-0x969ddfff]
[    0.026534] PM: hibernation: Registered nosave memory: [mem 0x96f8f000-0x96fcffff]
[    0.026536] PM: hibernation: Registered nosave memory: [mem 0x994f6000-0x994f6fff]
[    0.026537] PM: hibernation: Registered nosave memory: [mem 0x9b846000-0x9b846fff]
[    0.026539] PM: hibernation: Registered nosave memory: [mem 0x9b86a000-0x9b86afff]
[    0.026541] PM: hibernation: Registered nosave memory: [mem 0x9b9af000-0x9d9aefff]
[    0.026542] PM: hibernation: Registered nosave memory: [mem 0x9d9af000-0x9dbaefff]
[    0.026542] PM: hibernation: Registered nosave memory: [mem 0x9dbaf000-0x9dcfefff]
[    0.026543] PM: hibernation: Registered nosave memory: [mem 0x9dcff000-0x9effefff]
[    0.026545] PM: hibernation: Registered nosave memory: [mem 0x9f000000-0x9fffffff]
[    0.026545] PM: hibernation: Registered nosave memory: [mem 0xa0000000-0xfdffffff]
[    0.026546] PM: hibernation: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.026546] PM: hibernation: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.026547] PM: hibernation: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.026548] PM: hibernation: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.026548] PM: hibernation: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.026549] PM: hibernation: Registered nosave memory: [mem 0xfee01000-0xffffffff]
[    0.026550] [mem 0xa0000000-0xfdffffff] available for PCI devices
[    0.026552] Booting paravirtualized kernel on bare hardware
[    0.026553] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.026560] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.026850] percpu: Embedded 63 pages/cpu s221184 r8192 d28672 u262144
[    0.026857] pcpu-alloc: s221184 r8192 d28672 u262144 alloc=1*2097152
[    0.026859] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.026880] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic root=UUID=8db91722-3256-4c30-b0cf-4e75ea66d3b8 ro quiet splash nomodeset vt.handoff=7
[    0.026944] Booted with the nomodeset parameter. Only the system framebuffer will be available
[    0.026959] Unknown kernel command line parameters "splash BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic", will be passed to user space.
[    0.028075] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes, linear)
[    0.028637] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes, linear)
[    0.028730] Fallback order for Node 0: 0 
[    0.028732] Built 1 zonelists, mobility grouping on.  Total pages: 4101717
[    0.028733] Policy zone: Normal
[    0.028737] mem auto-init: stack:all(zero), heap alloc:on, heap free:off
[    0.028742] software IO TLB: area num 8.
[    0.064792] Memory: 16097896K/16667944K available (20480K kernel code, 4265K rwdata, 13180K rodata, 4792K init, 17396K bss, 569788K reserved, 0K cma-reserved)
[    0.064992] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.065012] ftrace: allocating 55226 entries in 216 pages
[    0.072746] ftrace: allocated 216 pages with 4 groups
[    0.073331] Dynamic Preempt: voluntary
[    0.073358] rcu: Preemptible hierarchical RCU implementation.
[    0.073358] rcu:     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=8.
[    0.073360]     Trampoline variant of Tasks RCU enabled.
[    0.073360]     Rude variant of Tasks RCU enabled.
[    0.073360]     Tracing variant of Tasks RCU enabled.
[    0.073361] rcu: RCU calculated value of scheduler-enlistment delay is 25 jiffies.
[    0.073362] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.075811] NR_IRQS: 524544, nr_irqs: 2048, preallocated irqs: 16
[    0.076069] rcu: srcu_init: Setting srcu_struct sizes based on contention.
[    0.076288] Console: colour dummy device 80x25
[    0.076290] printk: console [tty0] enabled
[    0.076333] ACPI: Core revision 20230331
[    0.076671] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.076762] APIC: Switch to symmetric I/O mode setup
[    0.076764] DMAR: Host address width 39
[    0.076765] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.076770] DMAR: dmar0: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.076772] DMAR: RMRR base: 0x0000009e908000 end: 0x0000009eb51fff
[    0.076774] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 0
[    0.076776] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.076777] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.078307] DMAR-IR: Enabled IRQ remapping in x2apic mode
[    0.078309] x2apic enabled
[    0.078325] Switched APIC routing to cluster x2apic.
[    0.083173] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.100701] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x6aa99074b1c, max_idle_ns: 881590506587 ns
[    0.100706] Calibrating delay loop (skipped), value calculated using timer frequency.. 7399.70 BogoMIPS (lpj=14799400)
[    0.100723] x86/cpu: SGX disabled by BIOS.
[    0.100730] CPU0: Thermal monitoring enabled (TM1)
[    0.100760] process: using mwait in idle threads
[    0.100762] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.100763] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.100766] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.100768] Spectre V2 : Mitigation: Enhanced / Automatic IBRS
[    0.100769] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.100769] Spectre V2 : Spectre v2 / PBRSB-eIBRS: Retire a single CALL on VMEXIT
[    0.100770] RETBleed: Mitigation: Enhanced IBRS
[    0.100771] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.100773] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl
[    0.100777] MMIO Stale Data: Mitigation: Clear CPU buffers
[    0.100778] SRBDS: Mitigation: Microcode
[    0.100780] GDS: Mitigation: Microcode
[    0.100784] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.100785] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.100786] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.100787] x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
[    0.100788] x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
[    0.100789] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.100790] x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
[    0.100791] x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
[    0.100791] x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
[    0.121949] Freeing SMP alternatives memory: 44K
[    0.121953] pid_max: default: 32768 minimum: 301
[    0.124743] LSM: initializing lsm=lockdown,capability,landlock,yama,apparmor,integrity
[    0.124753] landlock: Up and running.
[    0.124754] Yama: becoming mindful.
[    0.124774] AppArmor: AppArmor initialized
[    0.124808] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.124820] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.125246] smpboot: CPU0: Intel(R) Core(TM) i3-10105F CPU @ 3.70GHz (family: 0x6, model: 0xa5, stepping: 0x3)
[    0.125330] RCU Tasks: Setting shift to 3 and lim to 1 rcu_task_cb_adjust=1.
[    0.125341] RCU Tasks Rude: Setting shift to 3 and lim to 1 rcu_task_cb_adjust=1.
[    0.125353] RCU Tasks Trace: Setting shift to 3 and lim to 1 rcu_task_cb_adjust=1.
[    0.125361] Performance Events: PEBS fmt3+, Skylake events, 32-deep LBR, full-width counters, Intel PMU driver.
[    0.125379] ... version:                4
[    0.125379] ... bit width:              48
[    0.125380] ... generic registers:      4
[    0.125380] ... value mask:             0000ffffffffffff
[    0.125381] ... max period:             00007fffffffffff
[    0.125382] ... fixed-purpose events:   3
[    0.125383] ... event mask:             000000070000000f
[    0.125457] signal: max sigframe size: 2032
[    0.125467] Estimated ratio of average max frequency by base frequency (times 1024): 1162
[    0.125483] rcu: Hierarchical SRCU implementation.
[    0.125483] rcu:     Max phase no-delay instances is 1000.
[    0.125911] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.125967] smp: Bringing up secondary CPUs ...
[    0.126031] smpboot: x86: Booting SMP configuration:
[    0.126032] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.128740] MMIO Stale Data CPU bug present and SMT on, data leak possible. See https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/processor_mmio_stale_data.html for more details.
[    0.128740] smp: Brought up 1 node, 8 CPUs
[    0.128740] smpboot: Max logical packages: 1
[    0.128740] smpboot: Total of 8 processors activated (59197.60 BogoMIPS)
[    0.132945] devtmpfs: initialized
[    0.132945] x86/mm: Memory block size: 128MB
[    0.133692] ACPI: PM: Registering ACPI NVS region [mem 0x9b846000-0x9b846fff] (4096 bytes)
[    0.133692] ACPI: PM: Registering ACPI NVS region [mem 0x9dbaf000-0x9dcfefff] (1376256 bytes)
[    0.133692] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.133692] futex hash table entries: 2048 (order: 5, 131072 bytes, linear)
[    0.133692] pinctrl core: initialized pinctrl subsystem
[    0.133692] PM: RTC time: 08:46:07, date: 2024-01-23
[    0.133692] NET: Registered PF_NETLINK/PF_ROUTE protocol family
[    0.133692] DMA: preallocated 2048 KiB GFP_KERNEL pool for atomic allocations
[    0.133692] DMA: preallocated 2048 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
[    0.133764] DMA: preallocated 2048 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
[    0.133776] audit: initializing netlink subsys (disabled)
[    0.133788] audit: type=2000 audit(1705999567.056:1): state=initialized audit_enabled=0 res=1
[    0.133788] thermal_sys: Registered thermal governor 'fair_share'
[    0.133788] thermal_sys: Registered thermal governor 'bang_bang'
[    0.133788] thermal_sys: Registered thermal governor 'step_wise'
[    0.133788] thermal_sys: Registered thermal governor 'user_space'
[    0.133788] thermal_sys: Registered thermal governor 'power_allocator'
[    0.133788] EISA bus registered
[    0.133788] cpuidle: using governor ladder
[    0.133788] cpuidle: using governor menu
[    0.133788] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.133788] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.133788] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.133788] PCI: not using MMCONFIG
[    0.133788] PCI: Using configuration type 1 for base access
[    0.133788] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.133788] kprobes: kprobe jump-optimization is enabled. All kprobes are optimized if possible.
[    0.133788] HugeTLB: registered 1.00 GiB page size, pre-allocated 0 pages
[    0.133788] HugeTLB: 16380 KiB vmemmap can be freed for a 1.00 GiB page
[    0.133788] HugeTLB: registered 2.00 MiB page size, pre-allocated 0 pages
[    0.133788] HugeTLB: 28 KiB vmemmap can be freed for a 2.00 MiB page
[    0.133788] fbcon: Taking over console
[    0.133788] ACPI: Added _OSI(Module Device)
[    0.133788] ACPI: Added _OSI(Processor Device)
[    0.133788] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.133788] ACPI: Added _OSI(Processor Aggregator Device)
[    0.174357] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.179085] ACPI: Dynamic OEM Table Load:
[    0.179085] ACPI: SSDT 0xFFFF9BD241146000 000400 (v02 PmRef  Cpu0Cst  00003001 INTL 20160527)
[    0.179085] ACPI: Dynamic OEM Table Load:
[    0.179085] ACPI: SSDT 0xFFFF9BD241126000 0006EC (v02 PmRef  Cpu0Ist  00003000 INTL 20160527)
[    0.181375] ACPI: Dynamic OEM Table Load:
[    0.181379] ACPI: SSDT 0xFFFF9BD24090E100 0000FC (v02 PmRef  Cpu0Psd  00003000 INTL 20160527)
[    0.182663] ACPI: Dynamic OEM Table Load:
[    0.182669] ACPI: SSDT 0xFFFF9BD24196B000 000778 (v02 PmRef  ApIst    00003000 INTL 20160527)
[    0.183774] ACPI: Dynamic OEM Table Load:
[    0.183779] ACPI: SSDT 0xFFFF9BD24015D000 000D22 (v02 PmRef  ApPsd    00003000 INTL 20160527)
[    0.185327] ACPI: Dynamic OEM Table Load:
[    0.185331] ACPI: SSDT 0xFFFF9BD241143800 0003CA (v02 PmRef  ApCst    00003000 INTL 20160527)
[    0.189710] ACPI: Interpreter enabled
[    0.189740] ACPI: PM: (supports S0 S3 S4 S5)
[    0.189741] ACPI: Using IOAPIC for interrupt routing
[    0.190983] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.192817] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved as ACPI motherboard resource
[    0.192826] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.192827] PCI: Using E820 reservations for host bridge windows
[    0.193790] ACPI: Enabled 9 GPEs in block 00 to 7F
[    0.203946] ACPI: \_SB_.PCI0.XDCI.USBC: New power resource
[    0.206457] ACPI: \_SB_.PCI0.SAT0.VOL0.V0PR: New power resource
[    0.206643] ACPI: \_SB_.PCI0.SAT0.VOL1.V1PR: New power resource
[    0.206820] ACPI: \_SB_.PCI0.SAT0.VOL2.V2PR: New power resource
[    0.209639] ACPI: \_SB_.PCI0.CNVW.WRST: New power resource
[    0.213089] ACPI: \PIN_: New power resource
[    0.213428] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.213434] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI EDR HPX-Type3]
[    0.213520] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug SHPCHotplug PME]
[    0.213673] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability LTR DPC]
[    0.213674] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.214747] PCI host bridge to bus 0000:00
[    0.214748] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.214750] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.214751] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.214753] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff window]
[    0.214754] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xdfffffff window]
[    0.214755] pci_bus 0000:00: root bus resource [mem 0xfc800000-0xfe7fffff window]
[    0.214756] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.214830] pci 0000:00:00.0: [8086:9b63] type 00 class 0x060000
[    0.214890] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.214923] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.215491] pci 0000:00:12.0: [8086:06f9] type 00 class 0x118000
[    0.215506] pci 0000:00:12.0: reg 0x10: [mem 0xab41d000-0xab41dfff 64bit]
[    0.215645] pci 0000:00:14.0: [8086:06ed] type 00 class 0x0c0330
[    0.215658] pci 0000:00:14.0: reg 0x10: [mem 0xab400000-0xab40ffff 64bit]
[    0.215709] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.216184] pci 0000:00:14.2: [8086:06ef] type 00 class 0x050000
[    0.216198] pci 0000:00:14.2: reg 0x10: [mem 0xab416000-0xab417fff 64bit]
[    0.216208] pci 0000:00:14.2: reg 0x18: [mem 0xab41c000-0xab41cfff 64bit]
[    0.216314] pci 0000:00:16.0: [8086:06e0] type 00 class 0x078000
[    0.216331] pci 0000:00:16.0: reg 0x10: [mem 0xab41b000-0xab41bfff 64bit]
[    0.216397] pci 0000:00:16.0: PME# supported from D3hot
[    0.216826] pci 0000:00:17.0: [8086:06d2] type 00 class 0x010601
[    0.216837] pci 0000:00:17.0: reg 0x10: [mem 0xab414000-0xab415fff]
[    0.216843] pci 0000:00:17.0: reg 0x14: [mem 0xab41a000-0xab41a0ff]
[    0.216849] pci 0000:00:17.0: reg 0x18: [io  0x6050-0x6057]
[    0.216855] pci 0000:00:17.0: reg 0x1c: [io  0x6040-0x6043]
[    0.216861] pci 0000:00:17.0: reg 0x20: [io  0x6020-0x603f]
[    0.216867] pci 0000:00:17.0: reg 0x24: [mem 0xab419000-0xab4197ff]
[    0.216900] pci 0000:00:17.0: PME# supported from D3hot
[    0.217230] pci 0000:00:1d.0: [8086:06b2] type 01 class 0x060400
[    0.217304] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.217329] pci 0000:00:1d.0: PTM enabled (root), 4ns granularity
[    0.217961] pci 0000:00:1d.3: [8086:06b3] type 01 class 0x060400
[    0.218033] pci 0000:00:1d.3: PME# supported from D0 D3hot D3cold
[    0.218055] pci 0000:00:1d.3: PTM enabled (root), 4ns granularity
[    0.218688] pci 0000:00:1f.0: [8086:0684] type 00 class 0x060100
[    0.219059] pci 0000:00:1f.3: [8086:06c8] type 00 class 0x040300
[    0.219088] pci 0000:00:1f.3: reg 0x10: [mem 0xab410000-0xab413fff 64bit]
[    0.219125] pci 0000:00:1f.3: reg 0x20: [mem 0xab100000-0xab1fffff 64bit]
[    0.219198] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.220102] pci 0000:00:1f.4: [8086:06a3] type 00 class 0x0c0500
[    0.220125] pci 0000:00:1f.4: reg 0x10: [mem 0xab418000-0xab4180ff 64bit]
[    0.220151] pci 0000:00:1f.4: reg 0x20: [io  0xefa0-0xefbf]
[    0.220380] pci 0000:00:1f.5: [8086:06a4] type 00 class 0x0c8000
[    0.220394] pci 0000:00:1f.5: reg 0x10: [mem 0xfe010000-0xfe010fff]
[    0.220501] pci 0000:01:00.0: [10de:128b] type 00 class 0x030000
[    0.220512] pci 0000:01:00.0: reg 0x10: [mem 0xaa000000-0xaaffffff]
[    0.220521] pci 0000:01:00.0: reg 0x14: [mem 0xa0000000-0xa7ffffff 64bit pref]
[    0.220529] pci 0000:01:00.0: reg 0x1c: [mem 0xa8000000-0xa9ffffff 64bit pref]
[    0.220535] pci 0000:01:00.0: reg 0x24: [io  0x5000-0x507f]
[    0.220541] pci 0000:01:00.0: reg 0x30: [mem 0xab000000-0xab07ffff pref]
[    0.220556] pci 0000:01:00.0: BAR 1: assigned to efifb
[    0.220560] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.220618] pci 0000:01:00.0: 16.000 Gb/s available PCIe bandwidth, limited by 2.5 GT/s PCIe x8 link at 0000:00:01.0 (capable of 63.008 Gb/s with 8.0 GT/s PCIe x8 link)
[    0.220685] pci 0000:01:00.1: [10de:0e0f] type 00 class 0x040300
[    0.220694] pci 0000:01:00.1: reg 0x10: [mem 0xab080000-0xab083fff]
[    0.220796] pci 0000:00:01.0: ASPM: current common clock configuration is inconsistent, reconfiguring
[    0.232715] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.232717] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.232719] pci 0000:00:01.0:   bridge window [mem 0xaa000000-0xab0fffff]
[    0.232722] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.232804] pci 0000:02:00.0: [10ec:8161] type 00 class 0x020000
[    0.232819] pci 0000:02:00.0: reg 0x10: [io  0x4000-0x40ff]
[    0.232838] pci 0000:02:00.0: reg 0x18: [mem 0xab304000-0xab304fff 64bit]
[    0.232851] pci 0000:02:00.0: reg 0x20: [mem 0xab300000-0xab303fff 64bit]
[    0.232948] pci 0000:02:00.0: supports D1 D2
[    0.232949] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233122] pci 0000:00:1d.0: PCI bridge to [bus 02]
[    0.233124] pci 0000:00:1d.0:   bridge window [io  0x4000-0x4fff]
[    0.233127] pci 0000:00:1d.0:   bridge window [mem 0xab300000-0xab3fffff]
[    0.233203] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.233219] pci 0000:03:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.233238] pci 0000:03:00.0: reg 0x18: [mem 0xab204000-0xab204fff 64bit]
[    0.233250] pci 0000:03:00.0: reg 0x20: [mem 0xab200000-0xab203fff 64bit]
[    0.233345] pci 0000:03:00.0: supports D1 D2
[    0.233346] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233511] pci 0000:00:1d.3: PCI bridge to [bus 03]
[    0.233513] pci 0000:00:1d.3:   bridge window [io  0x3000-0x3fff]
[    0.233515] pci 0000:00:1d.3:   bridge window [mem 0xab200000-0xab2fffff]
[    0.234992] ACPI: PCI: Interrupt link LNKA configured for IRQ 0
[    0.235068] ACPI: PCI: Interrupt link LNKB configured for IRQ 1
[    0.235142] ACPI: PCI: Interrupt link LNKC configured for IRQ 0
[    0.235215] ACPI: PCI: Interrupt link LNKD configured for IRQ 0
[    0.235288] ACPI: PCI: Interrupt link LNKE configured for IRQ 0
[    0.235361] ACPI: PCI: Interrupt link LNKF configured for IRQ 0
[    0.235434] ACPI: PCI: Interrupt link LNKG configured for IRQ 0
[    0.235507] ACPI: PCI: Interrupt link LNKH configured for IRQ 0
[    0.238403] iommu: Default domain type: Translated
[    0.238403] iommu: DMA domain TLB invalidation policy: lazy mode
[    0.238403] SCSI subsystem initialized
[    0.238403] libata version 3.00 loaded.
[    0.238403] ACPI: bus type USB registered
[    0.238403] usbcore: registered new interface driver usbfs
[    0.238403] usbcore: registered new interface driver hub
[    0.238403] usbcore: registered new device driver usb
[    0.238403] pps_core: LinuxPPS API ver. 1 registered
[    0.238403] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.238403] PTP clock support registered
[    0.238403] EDAC MC: Ver: 3.0.0
[    0.238403] efivars: Registered efivars operations
[    0.238403] NetLabel: Initializing
[    0.238403] NetLabel:  domain hash size = 128
[    0.238403] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.238403] NetLabel:  unlabeled traffic allowed by default
[    0.238403] mctp: management component transport protocol core
[    0.238403] NET: Registered PF_MCTP protocol family
[    0.238403] PCI: Using ACPI for IRQ routing
[    0.282057] PCI: pci_cache_line_size set to 64 bytes
[    0.282120] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.282121] e820: reserve RAM buffer [mem 0x8d84d000-0x8fffffff]
[    0.282122] e820: reserve RAM buffer [mem 0x8e9ac000-0x8fffffff]
[    0.282123] e820: reserve RAM buffer [mem 0x96852018-0x97ffffff]
[    0.282124] e820: reserve RAM buffer [mem 0x969cf018-0x97ffffff]
[    0.282125] e820: reserve RAM buffer [mem 0x96f8f000-0x97ffffff]
[    0.282126] e820: reserve RAM buffer [mem 0x994f6000-0x9bffffff]
[    0.282127] e820: reserve RAM buffer [mem 0x9b846000-0x9bffffff]
[    0.282128] e820: reserve RAM buffer [mem 0x9b86a000-0x9bffffff]
[    0.282129] e820: reserve RAM buffer [mem 0x9b9af000-0x9bffffff]
[    0.282129] e820: reserve RAM buffer [mem 0x9f000000-0x9fffffff]
[    0.282130] e820: reserve RAM buffer [mem 0x45e000000-0x45fffffff]
[    0.282160] pci 0000:01:00.0: vgaarb: setting as boot VGA device
[    0.282160] pci 0000:01:00.0: vgaarb: bridge control possible
[    0.282160] pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.282160] vgaarb: loaded
[    0.282160] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.282160] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.284725] clocksource: Switched to clocksource tsc-early
[    0.291971] VFS: Disk quotas dquot_6.6.0
[    0.291982] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.292074] AppArmor: AppArmor Filesystem Enabled
[    0.292109] pnp: PnP ACPI init
[    0.292208] system 00:00: [mem 0x40000000-0x403fffff] has been reserved
[    0.292481] system 00:01: [io  0x0280-0x028f] has been reserved
[    0.292483] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.292485] system 00:01: [io  0x02a0-0x02bf] has been reserved
[    0.292486] system 00:01: [io  0x02c0-0x02cf] has been reserved
[    0.292604] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.292606] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.292700] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.292883] system 00:04: [io  0x1800-0x18fe] could not be reserved
[    0.292885] system 00:04: [mem 0xfd000000-0xfd69ffff] has been reserved
[    0.292886] system 00:04: [mem 0xfd6c0000-0xfd6cffff] has been reserved
[    0.292887] system 00:04: [mem 0xfd6f0000-0xfdffffff] has been reserved
[    0.292888] system 00:04: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.292889] system 00:04: [mem 0xfe200000-0xfe7fffff] has been reserved
[    0.292891] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.293132] system 00:05: [io  0x2000-0x20fe] has been reserved
[    0.293355] system 00:06: [mem 0xfd6e0000-0xfd6effff] has been reserved
[    0.293357] system 00:06: [mem 0xfd6d0000-0xfd6dffff] has been reserved
[    0.293358] system 00:06: [mem 0xfd6b0000-0xfd6bffff] has been reserved
[    0.293360] system 00:06: [mem 0xfd6a0000-0xfd6affff] has been reserved
[    0.293858] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.293860] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.293861] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.293862] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.293863] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.293865] system 00:07: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.293866] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.293867] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.294165] system 00:08: [mem 0xfe038000-0xfe038fff] has been reserved
[    0.294543] pnp: PnP ACPI: found 9 devices
[    0.299872] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.299911] NET: Registered PF_INET protocol family
[    0.300011] IP idents hash table entries: 262144 (order: 9, 2097152 bytes, linear)
[    0.302162] tcp_listen_portaddr_hash hash table entries: 8192 (order: 5, 131072 bytes, linear)
[    0.302186] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, linear)
[    0.302238] TCP established hash table entries: 131072 (order: 8, 1048576 bytes, linear)
[    0.302398] TCP bind hash table entries: 65536 (order: 9, 2097152 bytes, linear)
[    0.302576] TCP: Hash tables configured (established 131072 bind 65536)
[    0.302637] MPTCP token hash table entries: 16384 (order: 6, 393216 bytes, linear)
[    0.302672] UDP hash table entries: 8192 (order: 6, 262144 bytes, linear)
[    0.302702] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes, linear)
[    0.302745] NET: Registered PF_UNIX/PF_LOCAL protocol family
[    0.302750] NET: Registered PF_XDP protocol family
[    0.302760] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.302763] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.302765] pci 0000:00:01.0:   bridge window [mem 0xaa000000-0xab0fffff]
[    0.302767] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.302770] pci 0000:00:1d.0: PCI bridge to [bus 02]
[    0.302774] pci 0000:00:1d.0:   bridge window [io  0x4000-0x4fff]
[    0.302777] pci 0000:00:1d.0:   bridge window [mem 0xab300000-0xab3fffff]
[    0.302782] pci 0000:00:1d.3: PCI bridge to [bus 03]
[    0.302784] pci 0000:00:1d.3:   bridge window [io  0x3000-0x3fff]
[    0.302786] pci 0000:00:1d.3:   bridge window [mem 0xab200000-0xab2fffff]
[    0.302791] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.302793] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.302794] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.302795] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff window]
[    0.302796] pci_bus 0000:00: resource 8 [mem 0xa0000000-0xdfffffff window]
[    0.302797] pci_bus 0000:00: resource 9 [mem 0xfc800000-0xfe7fffff window]
[    0.302798] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.302799] pci_bus 0000:01: resource 1 [mem 0xaa000000-0xab0fffff]
[    0.302800] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.302801] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.302802] pci_bus 0000:02: resource 1 [mem 0xab300000-0xab3fffff]
[    0.302803] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.302804] pci_bus 0000:03: resource 1 [mem 0xab200000-0xab2fffff]
[    0.303192] pci 0000:01:00.1: extending delay after power-on from D3hot to 20 msec
[    0.303214] pci 0000:01:00.1: D0 power state depends on 0000:01:00.0
[    0.303228] PCI: CLS 64 bytes, default 64
[    0.303264] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.303265] software IO TLB: mapped [mem 0x00000000879b0000-0x000000008b9b0000] (64MB)
[    0.303294] Trying to unpack rootfs image as initramfs...
[    0.303439] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.303755] Initialise system trusted keyrings
[    0.303762] Key type blacklist registered
[    0.303797] workingset: timestamp_bits=36 max_order=22 bucket_order=0
[    0.303811] zbud: loaded
[    0.303952] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.304009] fuse: init (API version 7.38)
[    0.304094] integrity: Platform Keyring initialized
[    0.304097] integrity: Machine keyring initialized
[    0.309777] Key type asymmetric registered
[    0.309779] Asymmetric key parser 'x509' registered
[    0.309796] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 243)
[    0.309822] io scheduler mq-deadline registered
[    0.310432] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.310459] Driver imsttfb not loading because of nomodeset parameter
[    0.310461] Driver asiliantfb not loading because of nomodeset parameter
[    0.310469] efifb: probing for efifb
[    0.310482] efifb: showing boot graphics
[    0.315969] efifb: framebuffer at 0xa0000000, using 8640k, total 8640k
[    0.315970] efifb: mode is 1920x1080x32, linelength=8192, pages=1
[    0.315971] efifb: scrolling: redraw
[    0.315972] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.316035] Console: switching to colour frame buffer device 240x67
[    0.321518] fb0: EFI VGA frame buffer device
[    0.321755] Monitor-Mwait will be used to enter C-1 state
[    0.321758] Monitor-Mwait will be used to enter C-2 state
[    0.321760] ACPI: \_SB_.PR00: Found 2 idle states
[    0.322065] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.322085] ACPI: button: Sleep Button [SLPB]
[    0.322111] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.322124] ACPI: button: Power Button [PWRB]
[    0.322145] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.322175] ACPI: button: Power Button [PWRF]
[    0.322559] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.343707] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.345337] Linux agpgart interface v0.103
[    0.346608] loop: module loaded
[    0.346787] tun: Universal TUN/TAP device driver, 1.6
[    0.346831] PPP generic driver version 2.4.2
[    0.346940] i8042: PNP: No PS/2 controller found.
[    0.347024] mousedev: PS/2 mouse device common for all mice
[    0.347154] rtc_cmos rtc_cmos: RTC can wake from S4
[    0.348089] rtc_cmos rtc_cmos: registered as rtc0
[    0.348258] rtc_cmos rtc_cmos: setting system clock to 2024-01-23T08:46:07 UTC (1705999567)
[    0.348280] rtc_cmos rtc_cmos: alarms up to one month, y3k, 114 bytes nvram
[    0.348286] i2c_dev: i2c /dev entries driver
[    0.348428] device-mapper: core: CONFIG_IMA_DISABLE_HTABLE is disabled. Duplicate IMA measurements will not be recorded in the IMA log.
[    0.348437] device-mapper: uevent: version 1.0.3
[    0.348503] device-mapper: ioctl: 4.48.0-ioctl (2023-03-01) initialised: dm-devel@redhat.com
[    0.348519] platform eisa.0: Probing EISA bus 0
[    0.348522] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.348523] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.348524] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.348525] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.348526] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.348527] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.348528] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.348529] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.348529] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.348530] platform eisa.0: EISA: Detected 0 cards
[    0.348534] intel_pstate: Intel P-state driver initializing
[    0.348945] ledtrig-cpu: registered to indicate activity on CPUs
[    0.348997] intel_pmc_core INT33A1:00:  initialized
[    0.349053] drop_monitor: Initializing network drop monitor service
[    0.357618] NET: Registered PF_INET6 protocol family
[    0.551565] Freeing initrd memory: 68548K
[    0.555283] Segment Routing with IPv6
[    0.555305] In-situ OAM (IOAM) with IPv6
[    0.555328] NET: Registered PF_PACKET protocol family
[    0.555369] Key type dns_resolver registered
[    0.556023] microcode: Microcode Update Driver: v2.2.
[    0.556040] IPI shorthand broadcast: enabled
[    0.556983] sched_clock: Marking stable (556001540, 447873)->(557983866, -1534453)
[    0.557161] registered taskstats version 1
[    0.557552] Loading compiled-in X.509 certificates
[    0.557941] Loaded X.509 cert 'Build time autogenerated kernel key: 605c7c135229ebe23ab6a6fa2965fd12055e3c58'
[    0.558264] Loaded X.509 cert 'Canonical Ltd. Live Patch Signing: 14df34d1a87cf37625abec039ef2bf521249b969'
[    0.558579] Loaded X.509 cert 'Canonical Ltd. Kernel Module Signing: 88f752e560a1e0737e31163a466ad7b70a850c19'
[    0.558580] blacklist: Loading compiled-in revocation X.509 certificates
[    0.558590] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing: 61482aa2830d0ab2ad5af10b7250da9033ddcef0'
[    0.558599] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2017): 242ade75ac4a15e50d50c84b0d45ff3eae707a03'
[    0.558608] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (ESM 2018): 365188c1d374d6b07c3c8f240f8ef722433d6a8b'
[    0.558617] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2019): c0746fd6c5da3ae827864651ad66ae47fe24b3e8'
[    0.558627] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v1): a8d54bbb3825cfb94fa13c9f8a594a195c107b8d'
[    0.558637] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v2): 4cf046892d6fd3c9a5b03f98d845f90851dc6a8c'
[    0.558646] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v3): 100437bb6de6e469b581e61cd66bce3ef4ed53af'
[    0.558656] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (Ubuntu Core 2019): c1d57b8f6b743f23ee41f4f7ee292f06eecadfb9'
[    0.559727] Key type .fscrypt registered
[    0.559728] Key type fscrypt-provisioning registered
[    0.561522] Key type encrypted registered
[    0.561525] AppArmor: AppArmor sha1 policy hashing enabled
[    0.561785] ima: No TPM chip found, activating TPM-bypass!
[    0.561788] Loading compiled-in module X.509 certificates
[    0.562143] Loaded X.509 cert 'Build time autogenerated kernel key: 605c7c135229ebe23ab6a6fa2965fd12055e3c58'
[    0.562144] ima: Allocated hash algorithm: sha1
[    0.562149] ima: No architecture policies found
[    0.562155] evm: Initialising EVM extended attributes:
[    0.562155] evm: security.selinux
[    0.562156] evm: security.SMACK64
[    0.562156] evm: security.SMACK64EXEC
[    0.562157] evm: security.SMACK64TRANSMUTE
[    0.562157] evm: security.SMACK64MMAP
[    0.562158] evm: security.apparmor
[    0.562158] evm: security.ima
[    0.562159] evm: security.capability
[    0.562159] evm: HMAC attrs: 0x1
[    0.562356] PM:   Magic number: 8:779:776
[    0.668553] RAS: Correctable Errors collector initialized.
[    0.668583] clk: Disabling unused clocks
[    0.669403] Freeing unused decrypted memory: 2036K
[    0.669830] Freeing unused kernel image (initmem) memory: 4792K
[    0.669833] Write protecting the kernel read-only data: 34816k
[    0.670130] Freeing unused kernel image (rodata/data gap) memory: 1156K
[    0.681703] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    0.681712] Run /init as init process
[    0.681713]   with arguments:
[    0.681715]     /init
[    0.681715]     splash
[    0.681716]   with environment:
[    0.681717]     HOME=/
[    0.681717]     TERM=linux
[    0.681718]     BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic
[    0.745638] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.745648] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.746722] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x110 quirks 0x0000000000009810
[    0.747030] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.747035] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.747037] xhci_hcd 0000:00:14.0: Host supports USB 3.1 Enhanced SuperSpeed
[    0.747079] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 6.05
[    0.747081] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.747082] usb usb1: Product: xHCI Host Controller
[    0.747083] usb usb1: Manufacturer: Linux 6.5.0-14-generic xhci-hcd
[    0.747084] usb usb1: SerialNumber: 0000:00:14.0
[    0.747206] i801_smbus 0000:00:1f.4: SMBus using PCI interrupt
[    0.747287] hub 1-0:1.0: USB hub found
[    0.747304] hub 1-0:1.0: 16 ports detected
[    0.747738] ahci 0000:00:17.0: version 3.0
[    0.747753] r8169 0000:02:00.0: enabling device (0000 -> 0003)
[    0.748288] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 6.05
[    0.748292] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.748294] usb usb2: Product: xHCI Host Controller
[    0.748295] usb usb2: Manufacturer: Linux 6.5.0-14-generic xhci-hcd
[    0.748296] usb usb2: SerialNumber: 0000:00:14.0
[    0.749160] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.749560] hub 2-0:1.0: USB hub found
[    0.749578] hub 2-0:1.0: 8 ports detected
[    0.750283] i2c i2c-0: 2/2 memory slots populated (from DMI)
[    0.750730] i2c i2c-0: Successfully instantiated SPD at 0x50
[    0.759604] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.759610] ahci 0000:00:17.0: flags: 64bit ncq sntf clo only pio slum part ems deso sadm sds apst 
[    0.766746] r8169 0000:02:00.0 eth0: RTL8168h/8111h, 1c:61:b4:6d:38:4f, XID 541, IRQ 126
[    0.766750] r8169 0000:02:00.0 eth0: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    0.766776] r8169 0000:03:00.0: enabling device (0000 -> 0003)
[    0.766875] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.782114] r8169 0000:03:00.0 eth1: RTL8168h/8111h, a8:a1:59:6e:1f:8b, XID 541, IRQ 127
[    0.782118] r8169 0000:03:00.0 eth1: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    0.805350] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    0.816985] scsi host0: ahci
[    0.817243] scsi host1: ahci
[    0.817429] scsi host2: ahci
[    0.817616] scsi host3: ahci
[    0.817743] scsi host4: ahci
[    0.817867] scsi host5: ahci
[    0.817920] ata1: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419100 irq 125
[    0.817924] ata2: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419180 irq 125
[    0.817926] ata3: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419200 irq 125
[    0.817927] ata4: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419280 irq 125
[    0.817929] ata5: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419300 irq 125
[    0.817930] ata6: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419380 irq 125
[    0.828695] r8169 0000:03:00.0 enp3s0: renamed from eth1
[    1.000521] usb 1-6: new low-speed USB device number 2 using xhci_hcd
[    1.131698] ata6: SATA link down (SStatus 4 SControl 300)
[    1.131806] ata2: SATA link down (SStatus 4 SControl 300)
[    1.131834] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.131857] ata5: SATA link down (SStatus 4 SControl 300)
[    1.131897] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.131913] ata3: SATA link down (SStatus 4 SControl 300)
[    1.132624] ata1.00: ATA-10: INTEL SSDSC2KW240H6,  LSBG200, max UDMA/133
[    1.132717] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    1.133309] ata1.00: Features: Dev-Sleep
[    1.134165] ata1.00: configured for UDMA/133
[    1.134354] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSC2KW24 G200 PQ: 0 ANSI: 5
[    1.135221] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.135391] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/224 GiB)
[    1.135424] sd 0:0:0:0: [sda] Write Protect is off
[    1.135427] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.135480] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.135540] sd 0:0:0:0: [sda] Preferred minimum I/O size 512 bytes
[    1.137105]  sda: sda1 sda2
[    1.137173] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.144669] ata4.00: ATA-9: INTEL SSDSC2BW120A4, DC32, max UDMA/133
[    1.146509] ata4.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    1.172245] usb 1-6: New USB device found, idVendor=04d9, idProduct=1503, bcdDevice= 3.10
[    1.172248] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.172250] usb 1-6: Product: USB Keyboard
[    1.172251] usb 1-6: Manufacturer:  
[    1.172810] ata4.00: Features: Dev-Sleep
[    1.212791] ata4.00: configured for UDMA/133
[    1.212928] scsi 3:0:0:0: Direct-Access     ATA      INTEL SSDSC2BW12 DC32 PQ: 0 ANSI: 5
[    1.213434] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.213479] sd 3:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    1.213519] sd 3:0:0:0: [sdb] Write Protect is off
[    1.213521] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.213542] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.213568] sd 3:0:0:0: [sdb] Preferred minimum I/O size 512 bytes
[    1.215230]  sdb: sdb1
[    1.215317] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.300527] usb 1-9: new full-speed USB device number 3 using xhci_hcd
[    1.324519] tsc: Refined TSC clocksource calibration: 3696.001 MHz
[    1.324524] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x6a8d2ad56ed, max_idle_ns: 881591064802 ns
[    1.324561] clocksource: Switched to clocksource tsc
[    1.451541] usb 1-9: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.10
[    1.451544] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.451545] usb 1-9: Product: USB Receiver
[    1.451546] usb 1-9: Manufacturer: Logitech
[    1.459910] hid: raw HID events driver (C) Jiri Kosina
[    1.488912] usbcore: registered new interface driver usbhid
[    1.488915] usbhid: USB HID core driver
[    1.491325] input:   USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04D9:1503.0001/input/input3
[    1.548637] hid-generic 0003:04D9:1503.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:14.0-6/input0
[    1.548772] input:   USB Keyboard System Control as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input4
[    1.608675] input:   USB Keyboard Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input5
[    1.608829] hid-generic 0003:04D9:1503.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:14.0-6/input1
[    1.609130] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:046D:C52B.0003/input/input6
[    1.668706] hid-generic 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:14.0-9/input0
[    1.669208] input: Logitech USB Receiver Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input7
[    1.669414] input: Logitech USB Receiver Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input8
[    1.728632] input: Logitech USB Receiver System Control as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input9
[    1.728910] hid-generic 0003:046D:C52B.0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-9/input1
[    1.729338] hid-generic 0003:046D:C52B.0005: hiddev1,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-9/input2
[    1.901669] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-9/input2
[    2.023894] input: Logitech Wireless Device PID:402d Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input11
[    2.024721] input: Logitech Wireless Device PID:402d Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input12
[    2.025681] hid-generic 0003:046D:402D.0006: input,hidraw3: USB HID v1.11 Keyboard [Logitech Wireless Device PID:402d] on usb-0000:00:14.0-9/input2:1
[    2.151896] logitech-hidpp-device 0003:046D:402D.0006: hidraw3: USB HID v1.11 Keyboard [Logitech M560] on usb-0000:00:14.0-9/input2:1
[    2.198019] EXT4-fs (sda2): mounted filesystem 8db91722-3256-4c30-b0cf-4e75ea66d3b8 ro with ordered data mode. Quota mode: none.
[    2.305277] systemd[1]: Inserted module 'autofs4'
[    2.329389] systemd[1]: systemd 249.11-0ubuntu3.12 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)
[    2.329452] systemd[1]: Detected architecture x86-64.
[    2.329791] systemd[1]: Hostname set to <ubuntu>.
[    2.359404] systemd[1]: memfd_create() called without MFD_EXEC or MFD_NOEXEC_SEAL set
[    2.382068] block sda: the capability attribute has been deprecated.
[    2.464657] systemd[1]: Queued start job for default target Graphical Interface.
[    2.496836] systemd[1]: Created slice Slice /system/modprobe.
[    2.497048] systemd[1]: Created slice Slice /system/systemd-fsck.
[    2.497175] systemd[1]: Created slice User and Session Slice.
[    2.497222] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    2.497336] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    2.497381] systemd[1]: Reached target User and Group Name Lookups.
[    2.497392] systemd[1]: Reached target Remote File Systems.
[    2.497399] systemd[1]: Reached target Slice Units.
[    2.497409] systemd[1]: Reached target Mounting snaps.
[    2.497427] systemd[1]: Reached target Local Verity Protected Volumes.
[    2.497504] systemd[1]: Listening on Syslog Socket.
[    2.497571] systemd[1]: Listening on fsck to fsckd communication Socket.
[    2.497608] systemd[1]: Listening on initctl Compatibility Named Pipe.
[    2.497724] systemd[1]: Listening on Journal Audit Socket.
[    2.497779] systemd[1]: Listening on Journal Socket (/dev/log).
[    2.497845] systemd[1]: Listening on Journal Socket.
[    2.498084] systemd[1]: Listening on udev Control Socket.
[    2.498142] systemd[1]: Listening on udev Kernel Socket.
[    2.498654] systemd[1]: Mounting Huge Pages File System...
[    2.499172] systemd[1]: Mounting POSIX Message Queue File System...
[    2.499743] systemd[1]: Mounting Kernel Debug File System...
[    2.500282] systemd[1]: Mounting Kernel Trace File System...
[    2.501461] systemd[1]: Starting Journal Service...
[    2.502107] systemd[1]: Starting Set the console keyboard layout...
[    2.502707] systemd[1]: Starting Create List of Static Device Nodes...
[    2.503274] systemd[1]: Starting Load Kernel Module configfs...
[    2.503927] systemd[1]: Starting Load Kernel Module drm...
[    2.504825] systemd[1]: Starting Load Kernel Module efi_pstore...
[    2.505739] systemd[1]: Starting Load Kernel Module fuse...
[    2.505875] systemd[1]: Condition check resulted in File System Check on Root Device being skipped.
[    2.507476] systemd[1]: Starting Load Kernel Modules...
[    2.507911] pstore: Using crash dump compression: deflate
[    2.508186] systemd[1]: Starting Remount Root and Kernel File Systems...
[    2.508950] systemd[1]: Starting Coldplug All udev Devices...
[    2.509881] systemd[1]: Mounted Huge Pages File System.
[    2.509964] systemd[1]: Mounted POSIX Message Queue File System.
[    2.510020] systemd[1]: Mounted Kernel Debug File System.
[    2.510069] systemd[1]: Mounted Kernel Trace File System.
[    2.510249] systemd[1]: Finished Create List of Static Device Nodes.
[    2.510411] systemd[1]: modprobe@configfs.service: Deactivated successfully.
[    2.510538] systemd[1]: Finished Load Kernel Module configfs.
[    2.510673] systemd[1]: modprobe@fuse.service: Deactivated successfully.
[    2.510799] systemd[1]: Finished Load Kernel Module fuse.
[    2.511507] systemd[1]: Mounting FUSE Control File System...
[    2.512176] systemd[1]: Mounting Kernel Configuration File System...
[    2.513172] pstore: Registered efi_pstore as persistent store backend
[    2.513610] systemd[1]: modprobe@efi_pstore.service: Deactivated successfully.
[    2.513788] systemd[1]: Finished Load Kernel Module efi_pstore.
[    2.514212] systemd[1]: Mounted FUSE Control File System.
[    2.514273] systemd[1]: Mounted Kernel Configuration File System.
[    2.516319] EXT4-fs (sda2): re-mounted 8db91722-3256-4c30-b0cf-4e75ea66d3b8 r/w. Quota mode: none.
[    2.517225] systemd[1]: Finished Remount Root and Kernel File Systems.
[    2.517874] systemd[1]: Activating swap /swapfile...
[    2.517942] systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
[    2.518561] systemd[1]: Starting Load/Save Random Seed...
[    2.519176] systemd[1]: Starting Create System Users...
[    2.529904] Adding 2097148k swap on /swapfile.  Priority:-2 extents:17 across:233758720k SSFS
[    2.529987] systemd[1]: Activated swap /swapfile.
[    2.530040] systemd[1]: Reached target Swaps.
[    2.530580] ACPI: bus type drm_connector registered
[    2.532028] systemd[1]: modprobe@drm.service: Deactivated successfully.
[    2.532175] systemd[1]: Finished Load Kernel Module drm.
[    2.534168] systemd[1]: Finished Load/Save Random Seed.
[    2.534287] systemd[1]: Condition check resulted in First Boot Complete being skipped.
[    2.536040] systemd[1]: Started Journal Service.
[    2.536078] lp: driver loaded but no devices found
[    2.538660] ppdev: user-space parallel port driver
[    2.540637] systemd-journald[257]: Received client request to flush runtime journal.
[    2.555722] loop0: detected capacity change from 0 to 129944
[    2.555758] loop1: detected capacity change from 0 to 8
[    2.557543] loop2: detected capacity change from 0 to 130888
[    2.558462] loop3: detected capacity change from 0 to 151784
[    2.559177] loop4: detected capacity change from 0 to 151296
[    2.560878] loop5: detected capacity change from 0 to 485800
[    2.561690] loop6: detected capacity change from 0 to 503800
[    2.562871] loop7: detected capacity change from 0 to 716176
[    2.564386] loop8: detected capacity change from 0 to 994336
[    2.565559] loop9: detected capacity change from 0 to 1017816
[    2.566992] loop10: detected capacity change from 0 to 187776
[    2.567990] loop11: detected capacity change from 0 to 25240
[    2.569344] loop12: detected capacity change from 0 to 109072
[    2.569841] loop13: detected capacity change from 0 to 82800
[    2.571114] loop14: detected capacity change from 0 to 904
[    2.776951] intel_pch_thermal 0000:00:12.0: enabling device (0000 -> 0002)
[    2.778240] ee1004 0-0050: 512 byte EE1004-compliant SPD EEPROM, read-only
[    2.787033] RAPL PMU: API unit is 2^-32 Joules, 3 fixed counters, 655360 ms ovfl timer
[    2.787037] RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
[    2.787038] RAPL PMU: hw unit of domain package 2^-14 Joules
[    2.787039] RAPL PMU: hw unit of domain dram 2^-14 Joules
[    2.787137] spi-nor spi0.0: mx25l12805d (16384 Kbytes)
[    2.790247] cryptd: max_cpu_qlen set to 1000
[    2.791992] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    2.793019] Creating 1 MTD partitions on "0000:00:1f.5":
[    2.793025] 0x000000000000-0x000001000000 : "BIOS"
[    2.814215] AVX2 version of gcm_enc/dec engaged.
[    2.814248] AES CTR mode by8 optimization enabled
[    3.090204] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.090569] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    3.090656] snd_hda_intel 0000:01:00.1: Disabling MSI
[    3.090660] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    3.094414] intel_tcc_cooling: Programmable TCC Offset detected
[    3.099650] intel_rapl_common: Found RAPL domain package
[    3.099655] intel_rapl_common: Found RAPL domain core
[    3.099656] intel_rapl_common: Found RAPL domain dram
[    3.099660] intel_rapl_common: package-0:package:long_term locked by BIOS
[    3.099662] intel_rapl_common: package-0:package:short_term locked by BIOS
[    3.100546] audit: type=1400 audit(1705999570.248:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lsb_release" pid=547 comm="apparmor_parser"
[    3.100572] audit: type=1400 audit(1705999570.248:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=554 comm="apparmor_parser"
[    3.100821] audit: type=1400 audit(1705999570.248:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=548 comm="apparmor_parser"
[    3.100827] audit: type=1400 audit(1705999570.248:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=548 comm="apparmor_parser"
[    3.101081] audit: type=1400 audit(1705999570.248:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=551 comm="apparmor_parser"
[    3.101085] audit: type=1400 audit(1705999570.248:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=551 comm="apparmor_parser"
[    3.101087] audit: type=1400 audit(1705999570.248:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=551 comm="apparmor_parser"
[    3.101545] audit: type=1400 audit(1705999570.248:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oosplash" pid=553 comm="apparmor_parser"
[    3.105067] audit: type=1400 audit(1705999570.252:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=558 comm="apparmor_parser"
[    3.108683] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    3.108730] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[    3.108773] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[    3.108822] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    3.120089] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC897: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    3.120094] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.120095] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    3.120097] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.120097] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.120098] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    3.120099] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    3.120100] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    3.137636] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[    3.137677] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input21
[    3.137719] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input22
[    3.137753] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input23
[    3.137782] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input24
[    3.560490] Generic FE-GE Realtek PHY r8169-0-200:00: attached PHY driver (mii_bus:phy_addr=r8169-0-200:00, irq=MAC)
[    3.760591] r8169 0000:02:00.0 enp2s0: Link is Down
[    3.788529] Generic FE-GE Realtek PHY r8169-0-300:00: attached PHY driver (mii_bus:phy_addr=r8169-0-300:00, irq=MAC)
[    3.988643] r8169 0000:03:00.0 enp3s0: Link is Down
[    4.121158] loop15: detected capacity change from 0 to 8
[    7.177355] r8169 0000:02:00.0 enp2s0: Link is Up - 1Gbps/Full - flow control rx/tx
[    7.562061] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   24.233005] kauditd_printk_skb: 39 callbacks suppressed
[   24.233009] audit: type=1400 audit(1705999591.380:50): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20671/usr/lib/snapd/snap-confine" pid=916 comm="snap-confine" capability=12  capname="net_admin"
[   24.233013] audit: type=1400 audit(1705999591.380:51): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20671/usr/lib/snapd/snap-confine" pid=916 comm="snap-confine" capability=38  capname="perfmon"
[   26.102875] rfkill: input handler disabled
[   32.596425] rfkill: input handler enabled
[   33.675729] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.683706] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.699725] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.707748] logitech-hidpp-device 0003:046D:402D.0006: HID++ 2.0 device connected.
[   33.745727] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.799706] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.815707] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.853705] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.869704] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.885722] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.901729] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.915729] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.931732] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.947706] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   33.955767] input: Logitech Wireless Mouse M560 as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input25
[   34.096873] rfkill: input handler disabled
[   34.162785] audit: type=1400 audit(1705999601.800:52): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20671/usr/lib/snapd/snap-confine" pid=1951 comm="snap-confine" capability=12  capname="net_admin"
[   34.162792] audit: type=1400 audit(1705999601.800:53): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20671/usr/lib/snapd/snap-confine" pid=1951 comm="snap-confine" capability=38  capname="perfmon"
[   35.429344] audit: type=1400 audit(1705999603.068:54): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20671/usr/lib/snapd/snap-confine" pid=2325 comm="snap-confine" capability=12  capname="net_admin"
[   35.429351] audit: type=1400 audit(1705999603.068:55): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20671/usr/lib/snapd/snap-confine" pid=2325 comm="snap-confine" capability=38  capname="perfmon"
[   35.953887] audit: type=1107 audit(1705999603.592:56): pid=622 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.9" pid=1951 label="snap.snap-store.ubuntu-software" peer_pid=633 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   35.954128] audit: type=1107 audit(1705999603.592:57): pid=622 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=1951 label="snap.snap-store.ubuntu-software" peer_pid=633 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   35.955836] audit: type=1107 audit(1705999603.592:58): pid=622 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.9" pid=1951 label="snap.snap-store.ubuntu-software" peer_pid=633 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   35.956003] audit: type=1107 audit(1705999603.592:59): pid=622 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=1951 label="snap.snap-store.ubuntu-software" peer_pid=633 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   36.237108] audit: type=1400 audit(1705999603.876:60): apparmor="DENIED" operation="open" class="file" profile="snap.snap-store.ubuntu-software" name="/etc/appstream.conf" pid=1951 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

---

### Post by kotgc on 2024-01-23
Hilarious! I just connected a 2nd SSD to the machine and booted Linux Mint 20.1 Ulyssa 64-bit, Kernel Linux 5.4.0-74-generic x86_64, MATE 1.24.0 and all 3 monitors work fine.
Lol, so much for people saying Ubuntu's better!
Code 1/2:
```

linuxmint@linuxmint:~$ dmesg
[    0.000000] microcode: microcode updated early to revision 0xea, date = 2021-03-08
[    0.000000] Linux version 5.4.0-74-generic (buildd@lgw01-amd64-038) (gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04)) #83-Ubuntu SMP Sat May 8 02:35:39 UTC 2021 (Ubuntu 5.4.0-74.83-generic 5.4.114)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-74-generic root=UUID=bdb7ece6-c98c-4635-bfea-2d0d9bbdc22c ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Hygon HygonGenuine
[    0.000000]   Centaur CentaurHauls
[    0.000000]   zhaoxin   Shanghai  
[    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
[    0.000000] x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000000a0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000403fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040400000-0x000000008d84cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008d84e000-0x000000008e9abfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008e9ad000-0x000000009b845fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009b847000-0x000000009b869fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b86a000-0x000000009b86afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b86b000-0x000000009b9aefff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009dcff000-0x000000009effefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009efff000-0x000000009effffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f000000-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000045dffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x96529018-0x96549657] usable ==> usable
[    0.000000] e820: update [mem 0x96529018-0x96549657] usable ==> usable
[    0.000000] e820: update [mem 0x963c1018-0x963cf057] usable ==> usable
[    0.000000] e820: update [mem 0x963c1018-0x963cf057] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009efff] reserved
[    0.000000] reserve setup_data: [mem 0x000000000009f000-0x000000000009ffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000000a0000-0x00000000000fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000003fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000040000000-0x00000000403fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000040400000-0x000000008d84cfff] usable
[    0.000000] reserve setup_data: [mem 0x000000008d84d000-0x000000008d84dfff] reserved
[    0.000000] reserve setup_data: [mem 0x000000008d84e000-0x000000008e9abfff] usable
[    0.000000] reserve setup_data: [mem 0x000000008e9ac000-0x000000008e9acfff] reserved
[    0.000000] reserve setup_data: [mem 0x000000008e9ad000-0x00000000963c1017] usable
[    0.000000] reserve setup_data: [mem 0x00000000963c1018-0x00000000963cf057] usable
[    0.000000] reserve setup_data: [mem 0x00000000963cf058-0x0000000096529017] usable
[    0.000000] reserve setup_data: [mem 0x0000000096529018-0x0000000096549657] usable
[    0.000000] reserve setup_data: [mem 0x0000000096549658-0x000000009b845fff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b846000-0x000000009b846fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009b847000-0x000000009b869fff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b86a000-0x000000009b86afff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009b86b000-0x000000009b9aefff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b9af000-0x000000009d9aefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009d9af000-0x000000009dbaefff] ACPI data
[    0.000000] reserve setup_data: [mem 0x000000009dbaf000-0x000000009dcfefff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009dcff000-0x000000009effefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009efff000-0x000000009effffff] usable
[    0.000000] reserve setup_data: [mem 0x000000009f000000-0x000000009fffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000045dffffff] usable
[    0.000000] efi: EFI v2.70 by American Megatrends
[    0.000000] efi:  ACPI=0x9dcbb000  ACPI 2.0=0x9dcbb014  SMBIOS=0x9eb75000  SMBIOS 3.0=0x9eb74000  MEMATTR=0x9738b298  ESRT=0x994f6218 
[    0.000000] secureboot: Secure boot disabled
[    0.000000] SMBIOS 3.2.0 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./H470M-HVS, BIOS P1.10 01/11/2021
[    0.000000] tsc: Detected 3700.000 MHz processor
[    0.000522] tsc: Detected 3699.850 MHz TSC
[    0.000522] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000523] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000528] last_pfn = 0x45e000 max_arch_pfn = 0x400000000
[    0.000531] MTRR default type: write-back
[    0.000531] MTRR fixed ranges enabled:
[    0.000532]   00000-9FFFF write-back
[    0.000532]   A0000-BFFFF uncachable
[    0.000533]   C0000-FFFFF write-protect
[    0.000533] MTRR variable ranges enabled:
[    0.000534]   0 base 00C0000000 mask 7FC0000000 uncachable
[    0.000535]   1 base 00A0000000 mask 7FE0000000 uncachable
[    0.000536]   2 base 2000000000 mask 6000000000 uncachable
[    0.000536]   3 base 1000000000 mask 7000000000 uncachable
[    0.000537]   4 base 0800000000 mask 7800000000 uncachable
[    0.000537]   5 base 4000000000 mask 4000000000 uncachable
[    0.000538]   6 disabled
[    0.000538]   7 disabled
[    0.000538]   8 disabled
[    0.000539]   9 disabled
[    0.000878] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.001010] last_pfn = 0x9f000 max_arch_pfn = 0x400000000
[    0.006702] esrt: Reserving ESRT space from 0x00000000994f6218 to 0x00000000994f6278.
[    0.006709] e820: update [mem 0x994f6000-0x994f6fff] usable ==> reserved
[    0.006773] check: Scanning 1 areas for low memory corruption
[    0.006784] Using GB pages for direct mapping
[    0.007589] secureboot: Secure boot disabled
[    0.007590] RAMDISK: [mem 0x3ac0b000-0x3fffdfff]
[    0.007599] ACPI: Early table checksum verification disabled
[    0.007601] ACPI: RSDP 0x000000009DCBB014 000024 (v02 ALASKA)
[    0.007603] ACPI: XSDT 0x000000009DCBA728 0000BC (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007607] ACPI: FACP 0x000000009DBA8000 000114 (v06 ALASKA A M I    01072009 AMI  00010013)
[    0.007610] ACPI: DSDT 0x000000009DB65000 042272 (v02 ALASKA A M I    01072009 INTL 20160527)
[    0.007612] ACPI: FACS 0x000000009DCFE000 000040
[    0.007614] ACPI: MCFG 0x000000009DBAC000 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.007616] ACPI: SSDT 0x000000009DBA9000 0020AD (v02 CpuRef CpuSsdt  00003000 INTL 20160527)
[    0.007618] ACPI: FIDT 0x000000009DB64000 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007619] ACPI: AAFT 0x000000009DBAE000 0002DE (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.007621] ACPI: SSDT 0x000000009DB60000 0031DA (v02 SaSsdt SaSsdt   00003000 INTL 20160527)
[    0.007623] ACPI: SSDT 0x000000009DB5D000 002703 (v02 Intel  PegSsdt  00001000 INTL 20160527)
[    0.007625] ACPI: HPET 0x000000009DBAD000 000038 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007627] ACPI: NHLT 0x000000009DB5B000 001821 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.007628] ACPI: LPIT 0x000000009DB5A000 000094 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007630] ACPI: SSDT 0x000000009DB56000 0025B2 (v02 ALASKA TbtTypeC 00000000 INTL 20160527)
[    0.007632] ACPI: DBGP 0x000000009DB55000 000034 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.007634] ACPI: DBG2 0x000000009DB54000 000054 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.007635] ACPI: SSDT 0x000000009DB52000 001B67 (v02 ALASKA UsbCTabl 00001000 INTL 20160527)
[    0.007637] ACPI: DMAR 0x000000009DB51000 000070 (v01 INTEL  EDK2     00000002      01000013)
[    0.007639] ACPI: BGRT 0x000000009DB50000 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007641] ACPI: WSMT 0x000000009DB59000 000028 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.007642] ACPI: APIC 0x000000009DB4F000 0000BC (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.007644] ACPI: FPDT 0x000000009DB4E000 000044 (v01 ALASKA CML      01072009 AMI  01000013)
[    0.007650] ACPI: Local APIC address 0xfee00000
[    0.007917] No NUMA configuration found
[    0.007917] Faking a node at [mem 0x0000000000000000-0x000000045dffffff]
[    0.007925] NODE_DATA(0) allocated [mem 0x45dfd5000-0x45dffffff]
[    0.008089] Zone ranges:
[    0.008089]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.008090]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.008091]   Normal   [mem 0x0000000100000000-0x000000045dffffff]
[    0.008091]   Device   empty
[    0.008092] Movable zone start for each node
[    0.008094] Early memory node ranges
[    0.008095]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.008095]   node   0: [mem 0x000000000009f000-0x000000000009ffff]
[    0.008096]   node   0: [mem 0x0000000000100000-0x000000003fffffff]
[    0.008096]   node   0: [mem 0x0000000040400000-0x000000008d84cfff]
[    0.008097]   node   0: [mem 0x000000008d84e000-0x000000008e9abfff]
[    0.008097]   node   0: [mem 0x000000008e9ad000-0x000000009b845fff]
[    0.008097]   node   0: [mem 0x000000009b847000-0x000000009b869fff]
[    0.008098]   node   0: [mem 0x000000009b86b000-0x000000009b9aefff]
[    0.008098]   node   0: [mem 0x000000009efff000-0x000000009effffff]
[    0.008099]   node   0: [mem 0x0000000100000000-0x000000045dffffff]
[    0.008234] Zeroed struct page in unavailable ranges: 27318 pages
[    0.008235] Initmem setup node 0 [mem 0x0000000000001000-0x000000045dffffff]
[    0.008236] On node 0 totalpages: 4166986
[    0.008236]   DMA zone: 64 pages used for memmap
[    0.008237]   DMA zone: 26 pages reserved
[    0.008237]   DMA zone: 3998 pages, LIFO batch:0
[    0.008280]   DMA32 zone: 9879 pages used for memmap
[    0.008280]   DMA32 zone: 632236 pages, LIFO batch:63
[    0.016234]   Normal zone: 55168 pages used for memmap
[    0.016234]   Normal zone: 3530752 pages, LIFO batch:63
[    0.051444] ACPI: PM-Timer IO Port: 0x1808
[    0.051445] ACPI: Local APIC address 0xfee00000
[    0.051450] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.051450] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.051451] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.051451] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.051451] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.051452] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.051452] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.051453] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.051494] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.051495] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.051496] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.051497] ACPI: IRQ0 used by override.
[    0.051498] ACPI: IRQ9 used by override.
[    0.051499] Using ACPI (MADT) for SMP configuration information
[    0.051500] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.051508] e820: update [mem 0x96f8f000-0x96fcffff] usable ==> reserved
[    0.051515] TSC deadline timer available
[    0.051516] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.051536] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.051538] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.051539] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.051540] PM: Registered nosave memory: [mem 0x40000000-0x403fffff]
[    0.051541] PM: Registered nosave memory: [mem 0x8d84d000-0x8d84dfff]
[    0.051543] PM: Registered nosave memory: [mem 0x8e9ac000-0x8e9acfff]
[    0.051544] PM: Registered nosave memory: [mem 0x963c1000-0x963c1fff]
[    0.051545] PM: Registered nosave memory: [mem 0x963cf000-0x963cffff]
[    0.051546] PM: Registered nosave memory: [mem 0x96529000-0x96529fff]
[    0.051548] PM: Registered nosave memory: [mem 0x96549000-0x96549fff]
[    0.051549] PM: Registered nosave memory: [mem 0x96f8f000-0x96fcffff]
[    0.051550] PM: Registered nosave memory: [mem 0x994f6000-0x994f6fff]
[    0.051552] PM: Registered nosave memory: [mem 0x9b846000-0x9b846fff]
[    0.051553] PM: Registered nosave memory: [mem 0x9b86a000-0x9b86afff]
[    0.051555] PM: Registered nosave memory: [mem 0x9b9af000-0x9d9aefff]
[    0.051555] PM: Registered nosave memory: [mem 0x9d9af000-0x9dbaefff]
[    0.051555] PM: Registered nosave memory: [mem 0x9dbaf000-0x9dcfefff]
[    0.051556] PM: Registered nosave memory: [mem 0x9dcff000-0x9effefff]
[    0.051557] PM: Registered nosave memory: [mem 0x9f000000-0x9fffffff]
[    0.051558] PM: Registered nosave memory: [mem 0xa0000000-0xdfffffff]
[    0.051558] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.051558] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.051559] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.051559] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.051559] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.051560] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.051560] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.051560] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.051561] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.051562] [mem 0xa0000000-0xdfffffff] available for PCI devices
[    0.051563] Booting paravirtualized kernel on bare hardware
[    0.051565] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.051570] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.051689] percpu: Embedded 55 pages/cpu s188416 r8192 d28672 u262144
[    0.051695] pcpu-alloc: s188416 r8192 d28672 u262144 alloc=1*2097152
[    0.051696] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.051720] Built 1 zonelists, mobility grouping on.  Total pages: 4101849
[    0.051721] Policy zone: Normal
[    0.051722] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-74-generic root=UUID=bdb7ece6-c98c-4635-bfea-2d0d9bbdc22c ro quiet splash
[    0.052307] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes, linear)
[    0.052572] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes, linear)
[    0.052625] mem auto-init: stack:off, heap alloc:on, heap free:off
[    0.054777] Calgary: detecting Calgary via BIOS EBDA area
[    0.054779] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.079487] Memory: 16105828K/16667944K available (14339K kernel code, 2400K rwdata, 5008K rodata, 2736K init, 4964K bss, 562116K reserved, 0K cma-reserved)
[    0.079491] random: get_random_u64 called from kmem_cache_open+0x2d/0x410 with crng_init=0
[    0.079579] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.079587] ftrace: allocating 44589 entries in 175 pages
[    0.091848] rcu: Hierarchical RCU implementation.
[    0.091849] rcu:     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=8.
[    0.091849]     Tasks RCU enabled.
[    0.091850] rcu: RCU calculated value of scheduler-enlistment delay is 25 jiffies.
[    0.091850] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.093855] NR_IRQS: 524544, nr_irqs: 2048, preallocated irqs: 16
[    0.094255] random: crng done (trusting CPU's manufacturer)
[    0.094271] Console: colour dummy device 80x25
[    0.094275] printk: console [tty0] enabled
[    0.094285] ACPI: Core revision 20190816
[    0.094613] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.094698] APIC: Switch to symmetric I/O mode setup
[    0.094700] DMAR: Host address width 39
[    0.094700] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.094704] DMAR: dmar0: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.094704] DMAR: RMRR base: 0x0000009e908000 end: 0x0000009eb51fff
[    0.094706] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 0
[    0.094706] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.094707] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.096190] DMAR-IR: Enabled IRQ remapping in x2apic mode
[    0.096191] x2apic enabled
[    0.096216] Switched APIC routing to cluster x2apic.
[    0.101009] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.118644] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x6aa99074b1c, max_idle_ns: 881590506587 ns
[    0.118647] Calibrating delay loop (skipped), value calculated using timer frequency.. 7399.70 BogoMIPS (lpj=14799400)
[    0.118648] pid_max: default: 32768 minimum: 301
[    0.121703] LSM: Security Framework initializing
[    0.121710] Yama: becoming mindful.
[    0.121738] AppArmor: AppArmor initialized
[    0.121776] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.121795] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes, linear)
[    0.121804] *** VALIDATE tmpfs ***
[    0.121901] *** VALIDATE proc ***
[    0.121934] *** VALIDATE cgroup1 ***
[    0.121935] *** VALIDATE cgroup2 ***
[    0.121970] mce: CPU0: Thermal monitoring enabled (TM1)
[    0.121984] process: using mwait in idle threads
[    0.121986] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.121986] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.121988] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.121989] Spectre V2 : Mitigation: Enhanced IBRS
[    0.121990] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.121990] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.121991] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl and seccomp
[    0.122163] Freeing SMP alternatives memory: 40K
[    0.123718] smpboot: CPU0: Intel(R) Core(TM) i3-10105F CPU @ 3.70GHz (family: 0x6, model: 0xa5, stepping: 0x3)
[    0.123781] Performance Events: PEBS fmt3+, Skylake events, 32-deep LBR, full-width counters, Intel PMU driver.
[    0.123784] ... version:                4
[    0.123785] ... bit width:              48
[    0.123785] ... generic registers:      4
[    0.123786] ... value mask:             0000ffffffffffff
[    0.123786] ... max period:             00007fffffffffff
[    0.123786] ... fixed-purpose events:   3
[    0.123786] ... event mask:             000000070000000f
[    0.123810] rcu: Hierarchical SRCU implementation.
[    0.124421] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.124470] smp: Bringing up secondary CPUs ...
[    0.124519] x86: Booting SMP configuration:
[    0.124519] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.127689] smp: Brought up 1 node, 8 CPUs
[    0.127689] smpboot: Max logical packages: 1
[    0.127689] smpboot: Total of 8 processors activated (59197.60 BogoMIPS)
[    0.130954] devtmpfs: initialized
[    0.130954] x86/mm: Memory block size: 128MB
[    0.131649] PM: Registering ACPI NVS region [mem 0x9b846000-0x9b846fff] (4096 bytes)
[    0.131649] PM: Registering ACPI NVS region [mem 0x9dbaf000-0x9dcfefff] (1376256 bytes)
[    0.131649] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.131649] futex hash table entries: 2048 (order: 5, 131072 bytes, linear)
[    0.131649] pinctrl core: initialized pinctrl subsystem
[    0.131649] PM: RTC time: 08:58:58, date: 2024-01-23
[    0.131649] NET: Registered protocol family 16
[    0.131649] audit: initializing netlink subsys (disabled)
[    0.131649] audit: type=2000 audit(1706000338.036:1): state=initialized audit_enabled=0 res=1
[    0.131649] EISA bus registered
[    0.131649] cpuidle: using governor ladder
[    0.131649] cpuidle: using governor menu
[    0.131649] KVM setup pv remote TLB flush
[    0.131649] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.131649] ACPI: bus type PCI registered
[    0.131649] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.131649] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.131649] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.131649] PCI: Using configuration type 1 for base access
[    0.131649] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.131649] HugeTLB registered 1.00 GiB page size, pre-allocated 0 pages
[    0.131649] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.134687] ACPI: Added _OSI(Module Device)
[    0.134687] ACPI: Added _OSI(Processor Device)
[    0.134688] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.134688] ACPI: Added _OSI(Processor Aggregator Device)
[    0.134689] ACPI: Added _OSI(Linux-Dell-Video)
[    0.134689] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.134690] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.175103] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.180564] ACPI: Dynamic OEM Table Load:
[    0.180564] ACPI: SSDT 0xFFFF95C4CB242000 000400 (v02 PmRef  Cpu0Cst  00003001 INTL 20160527)
[    0.180564] ACPI: Dynamic OEM Table Load:
[    0.180564] ACPI: SSDT 0xFFFF95C4CACF9800 0006EC (v02 PmRef  Cpu0Ist  00003000 INTL 20160527)
[    0.183009] ACPI: Dynamic OEM Table Load:
[    0.183012] ACPI: SSDT 0xFFFF95C4CAD00100 0000FC (v02 PmRef  Cpu0Psd  00003000 INTL 20160527)
[    0.184514] ACPI: Dynamic OEM Table Load:
[    0.184518] ACPI: SSDT 0xFFFF95C4CACFB800 000778 (v02 PmRef  ApIst    00003000 INTL 20160527)
[    0.185810] ACPI: Dynamic OEM Table Load:
[    0.185815] ACPI: SSDT 0xFFFF95C4CBC6D000 000D22 (v02 PmRef  ApPsd    00003000 INTL 20160527)
[    0.187588] ACPI: Dynamic OEM Table Load:
[    0.187591] ACPI: SSDT 0xFFFF95C4CB247C00 0003CA (v02 PmRef  ApCst    00003000 INTL 20160527)
[    0.192153] ACPI: Interpreter enabled
[    0.192184] ACPI: (supports S0 S3 S4 S5)
[    0.192185] ACPI: Using IOAPIC for interrupt routing
[    0.192277] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.193288] ACPI: Enabled 9 GPEs in block 00 to 7F
[    0.204715] ACPI: Power Resource [USBC] (on)
[    0.207371] ACPI: Power Resource [V0PR] (on)
[    0.207557] ACPI: Power Resource [V1PR] (on)
[    0.207737] ACPI: Power Resource [V2PR] (on)
[    0.210724] ACPI: Power Resource [WRST] (on)
[    0.216660] ACPI: Power Resource [PIN] (off)
[    0.217007] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.217012] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
[    0.217183] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug SHPCHotplug PME]
[    0.217344] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability LTR]
[    0.217344] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.218236] PCI host bridge to bus 0000:00
[    0.218237] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.218238] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.218239] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.218239] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.218240] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.218240] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    0.218241] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    0.218242] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xdfffffff window]
[    0.218242] pci_bus 0000:00: root bus resource [mem 0xfc800000-0xfe7fffff window]
[    0.218243] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.218250] pci 0000:00:00.0: [8086:9b63] type 00 class 0x060000
[    0.218604] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.218639] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.218953] pci 0000:00:12.0: [8086:06f9] type 00 class 0x118000
[    0.218973] pci 0000:00:12.0: reg 0x10: [mem 0xab41d000-0xab41dfff 64bit]
[    0.219192] pci 0000:00:14.0: [8086:06ed] type 00 class 0x0c0330
[    0.219208] pci 0000:00:14.0: reg 0x10: [mem 0xab400000-0xab40ffff 64bit]
[    0.219259] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.219469] pci 0000:00:14.2: [8086:06ef] type 00 class 0x050000
[    0.219486] pci 0000:00:14.2: reg 0x10: [mem 0xab416000-0xab417fff 64bit]
[    0.219495] pci 0000:00:14.2: reg 0x18: [mem 0xab41c000-0xab41cfff 64bit]
[    0.219674] pci 0000:00:16.0: [8086:06e0] type 00 class 0x078000
[    0.219697] pci 0000:00:16.0: reg 0x10: [mem 0xab41b000-0xab41bfff 64bit]
[    0.219764] pci 0000:00:16.0: PME# supported from D3hot
[    0.219997] pci 0000:00:17.0: [8086:06d2] type 00 class 0x010601
[    0.220011] pci 0000:00:17.0: reg 0x10: [mem 0xab414000-0xab415fff]
[    0.220016] pci 0000:00:17.0: reg 0x14: [mem 0xab41a000-0xab41a0ff]
[    0.220022] pci 0000:00:17.0: reg 0x18: [io  0x6050-0x6057]
[    0.220028] pci 0000:00:17.0: reg 0x1c: [io  0x6040-0x6043]
[    0.220033] pci 0000:00:17.0: reg 0x20: [io  0x6020-0x603f]
[    0.220039] pci 0000:00:17.0: reg 0x24: [mem 0xab419000-0xab4197ff]
[    0.220071] pci 0000:00:17.0: PME# supported from D3hot
[    0.220274] pci 0000:00:1d.0: [8086:06b2] type 01 class 0x060400
[    0.220349] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.220364] pci 0000:00:1d.0: PTM enabled (root), 4ns granularity
[    0.220566] pci 0000:00:1d.3: [8086:06b3] type 01 class 0x060400
[    0.220637] pci 0000:00:1d.3: PME# supported from D0 D3hot D3cold
[    0.220651] pci 0000:00:1d.3: PTM enabled (root), 4ns granularity
[    0.220870] pci 0000:00:1f.0: [8086:0684] type 00 class 0x060100
[    0.221193] pci 0000:00:1f.3: [8086:06c8] type 00 class 0x040300
[    0.221233] pci 0000:00:1f.3: reg 0x10: [mem 0xab410000-0xab413fff 64bit]
[    0.221269] pci 0000:00:1f.3: reg 0x20: [mem 0xab100000-0xab1fffff 64bit]
[    0.221345] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.221644] pci 0000:00:1f.4: [8086:06a3] type 00 class 0x0c0500
[    0.221669] pci 0000:00:1f.4: reg 0x10: [mem 0xab418000-0xab4180ff 64bit]
[    0.221694] pci 0000:00:1f.4: reg 0x20: [io  0xefa0-0xefbf]
[    0.221873] pci 0000:00:1f.5: [8086:06a4] type 00 class 0x0c8000
[    0.221887] pci 0000:00:1f.5: reg 0x10: [mem 0xfe010000-0xfe010fff]
[    0.222078] pci 0000:01:00.0: [10de:128b] type 00 class 0x030000
[    0.222093] pci 0000:01:00.0: reg 0x10: [mem 0xaa000000-0xaaffffff]
[    0.222102] pci 0000:01:00.0: reg 0x14: [mem 0xa0000000-0xa7ffffff 64bit pref]
[    0.222110] pci 0000:01:00.0: reg 0x1c: [mem 0xa8000000-0xa9ffffff 64bit pref]
[    0.222115] pci 0000:01:00.0: reg 0x24: [io  0x5000-0x507f]
[    0.222121] pci 0000:01:00.0: reg 0x30: [mem 0xab000000-0xab07ffff pref]
[    0.222133] pci 0000:01:00.0: BAR 1: assigned to efifb
[    0.222181] pci 0000:01:00.0: 16.000 Gb/s available PCIe bandwidth, limited by 2.5 GT/s x8 link at 0000:00:01.0 (capable of 63.008 Gb/s with 8 GT/s x8 link)
[    0.222219] pci 0000:01:00.1: [10de:0e0f] type 00 class 0x040300
[    0.222230] pci 0000:01:00.1: reg 0x10: [mem 0xab080000-0xab083fff]
[    0.222319] pci 0000:00:01.0: ASPM: current common clock configuration is broken, reconfiguring
[    0.230691] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.230692] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.230694] pci 0000:00:01.0:   bridge window [mem 0xaa000000-0xab0fffff]
[    0.230696] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.230773] pci 0000:02:00.0: [10ec:8161] type 00 class 0x020000
[    0.230798] pci 0000:02:00.0: reg 0x10: [io  0x4000-0x40ff]
[    0.230817] pci 0000:02:00.0: reg 0x18: [mem 0xab304000-0xab304fff 64bit]
[    0.230829] pci 0000:02:00.0: reg 0x20: [mem 0xab300000-0xab303fff 64bit]
[    0.230923] pci 0000:02:00.0: supports D1 D2
[    0.230924] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.231027] pci 0000:00:1d.0: PCI bridge to [bus 02]
[    0.231029] pci 0000:00:1d.0:   bridge window [io  0x4000-0x4fff]
[    0.231031] pci 0000:00:1d.0:   bridge window [mem 0xab300000-0xab3fffff]
[    0.231102] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.231126] pci 0000:03:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.231145] pci 0000:03:00.0: reg 0x18: [mem 0xab204000-0xab204fff 64bit]
[    0.231157] pci 0000:03:00.0: reg 0x20: [mem 0xab200000-0xab203fff 64bit]
[    0.231248] pci 0000:03:00.0: supports D1 D2
[    0.231249] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.231349] pci 0000:00:1d.3: PCI bridge to [bus 03]
[    0.231351] pci 0000:00:1d.3:   bridge window [io  0x3000-0x3fff]
[    0.231353] pci 0000:00:1d.3:   bridge window [mem 0xab200000-0xab2fffff]
[    0.232802] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.232882] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *1
[    0.232961] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.233039] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.233119] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.233198] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.233276] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.233354] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    0.233590] iommu: Default domain type: Translated 
[    0.233590] SCSI subsystem initialized
[    0.233590] libata version 3.00 loaded.
[    0.233590] pci 0000:01:00.0: vgaarb: setting as boot VGA device
[    0.233590] pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.233590] pci 0000:01:00.0: vgaarb: bridge control possible
[    0.233590] vgaarb: loaded
[    0.233590] ACPI: bus type USB registered
[    0.233590] usbcore: registered new interface driver usbfs
[    0.233590] usbcore: registered new interface driver hub
[    0.233590] usbcore: registered new device driver usb
[    0.233590] pps_core: LinuxPPS API ver. 1 registered
[    0.233590] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.233590] PTP clock support registered
[    0.233590] EDAC MC: Ver: 3.0.0
[    0.233590] Registered efivars operations
[    0.233590] PCI: Using ACPI for IRQ routing
[    0.276940] PCI: pci_cache_line_size set to 64 bytes
[    0.277004] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.277005] e820: reserve RAM buffer [mem 0x8d84d000-0x8fffffff]
[    0.277006] e820: reserve RAM buffer [mem 0x8e9ac000-0x8fffffff]
[    0.277006] e820: reserve RAM buffer [mem 0x963c1018-0x97ffffff]
[    0.277007] e820: reserve RAM buffer [mem 0x96529018-0x97ffffff]
[    0.277007] e820: reserve RAM buffer [mem 0x96f8f000-0x97ffffff]
[    0.277008] e820: reserve RAM buffer [mem 0x994f6000-0x9bffffff]
[    0.277008] e820: reserve RAM buffer [mem 0x9b846000-0x9bffffff]
[    0.277009] e820: reserve RAM buffer [mem 0x9b86a000-0x9bffffff]
[    0.277009] e820: reserve RAM buffer [mem 0x9b9af000-0x9bffffff]
[    0.277010] e820: reserve RAM buffer [mem 0x9f000000-0x9fffffff]
[    0.277010] e820: reserve RAM buffer [mem 0x45e000000-0x45fffffff]
[    0.277065] NetLabel: Initializing
[    0.277065] NetLabel:  domain hash size = 128
[    0.277065] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.277074] NetLabel:  unlabeled traffic allowed by default
[    0.277082] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.277082] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.280689] clocksource: Switched to clocksource tsc-early
[    0.284605] *** VALIDATE bpf ***
[    0.284605] VFS: Disk quotas dquot_6.6.0
[    0.284605] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.284605] *** VALIDATE ramfs ***
[    0.284605] *** VALIDATE hugetlbfs ***
[    0.284605] AppArmor: AppArmor Filesystem Enabled
[    0.284605] pnp: PnP ACPI init
[    0.284605] system 00:00: [mem 0x40000000-0x403fffff] has been reserved
[    0.284605] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.284605] system 00:01: [io  0x0280-0x028f] has been reserved
[    0.284605] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.284605] system 00:01: [io  0x02a0-0x02bf] has been reserved
[    0.284605] system 00:01: [io  0x02c0-0x02cf] has been reserved
[    0.284605] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.284605] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.284605] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.284605] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.284605] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.284605] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.286684] system 00:04: [io  0x1800-0x18fe] could not be reserved
[    0.286686] system 00:04: [mem 0xfd000000-0xfd69ffff] has been reserved
[    0.286686] system 00:04: [mem 0xfd6c0000-0xfd6cffff] has been reserved
[    0.286687] system 00:04: [mem 0xfd6f0000-0xfdffffff] has been reserved
[    0.286688] system 00:04: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.286689] system 00:04: [mem 0xfe200000-0xfe7fffff] has been reserved
[    0.286689] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.286691] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286941] system 00:05: [io  0x2000-0x20fe] has been reserved
[    0.286943] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.287171] system 00:06: [mem 0xfd6e0000-0xfd6effff] has been reserved
[    0.287172] system 00:06: [mem 0xfd6d0000-0xfd6dffff] has been reserved
[    0.287173] system 00:06: [mem 0xfd6b0000-0xfd6bffff] has been reserved
[    0.287174] system 00:06: [mem 0xfd6a0000-0xfd6affff] has been reserved
[    0.287176] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.287692] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.287693] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.287693] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.287694] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.287695] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.287696] system 00:07: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.287697] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.287697] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.287699] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.288008] system 00:08: [mem 0xfe038000-0xfe038fff] has been reserved
[    0.288010] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.288409] pnp: PnP ACPI: found 9 devices
[    0.289124] thermal_sys: Registered thermal governor 'fair_share'
[    0.289124] thermal_sys: Registered thermal governor 'bang_bang'
[    0.289125] thermal_sys: Registered thermal governor 'step_wise'
[    0.289125] thermal_sys: Registered thermal governor 'user_space'
[    0.289125] thermal_sys: Registered thermal governor 'power_allocator'
[    0.293612] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.293634] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.293636] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.293638] pci 0000:00:01.0:   bridge window [mem 0xaa000000-0xab0fffff]
[    0.293639] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.293642] pci 0000:00:1d.0: PCI bridge to [bus 02]
[    0.293646] pci 0000:00:1d.0:   bridge window [io  0x4000-0x4fff]
[    0.293649] pci 0000:00:1d.0:   bridge window [mem 0xab300000-0xab3fffff]
[    0.293653] pci 0000:00:1d.3: PCI bridge to [bus 03]
[    0.293654] pci 0000:00:1d.3:   bridge window [io  0x3000-0x3fff]
[    0.293657] pci 0000:00:1d.3:   bridge window [mem 0xab200000-0xab2fffff]
[    0.293662] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.293663] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.293663] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.293664] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000e3fff window]
[    0.293664] pci_bus 0000:00: resource 8 [mem 0x000e4000-0x000e7fff window]
[    0.293665] pci_bus 0000:00: resource 9 [mem 0x000e8000-0x000ebfff window]
[    0.293666] pci_bus 0000:00: resource 10 [mem 0x000ec000-0x000effff window]
[    0.293666] pci_bus 0000:00: resource 11 [mem 0xa0000000-0xdfffffff window]
[    0.293667] pci_bus 0000:00: resource 12 [mem 0xfc800000-0xfe7fffff window]
[    0.293668] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.293668] pci_bus 0000:01: resource 1 [mem 0xaa000000-0xab0fffff]
[    0.293669] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xa9ffffff 64bit pref]
[    0.293670] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.293670] pci_bus 0000:02: resource 1 [mem 0xab300000-0xab3fffff]
[    0.293671] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.293671] pci_bus 0000:03: resource 1 [mem 0xab200000-0xab2fffff]
[    0.293803] NET: Registered protocol family 2
[    0.293906] tcp_listen_portaddr_hash hash table entries: 8192 (order: 5, 131072 bytes, linear)
[    0.293957] TCP established hash table entries: 131072 (order: 8, 1048576 bytes, linear)
[    0.294071] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes, linear)
[    0.294119] TCP: Hash tables configured (established 131072 bind 65536)
[    0.294145] UDP hash table entries: 8192 (order: 6, 262144 bytes, linear)
[    0.294173] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes, linear)
[    0.294214] NET: Registered protocol family 1
[    0.294216] NET: Registered protocol family 44
[    0.294457] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.294464] pci 0000:01:00.1: D0 power state depends on 0000:01:00.0
[    0.294474] PCI: CLS 64 bytes, default 64
[    0.294523] Trying to unpack rootfs image as initramfs...
[    0.422051] Freeing initrd memory: 85964K
[    0.450685] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.450689] software IO TLB: mapped [mem 0x91e8d000-0x95e8d000] (64MB)
[    0.450776] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.450836] check: Scanning for low memory corruption every 60 seconds
[    0.451090] Initialise system trusted keyrings
[    0.451095] Key type blacklist registered
[    0.451111] workingset: timestamp_bits=36 max_order=22 bucket_order=0
[    0.451870] zbud: loaded
[    0.452059] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.452142] fuse: init (API version 7.31)
[    0.452150] *** VALIDATE fuse ***
[    0.452151] *** VALIDATE fuse ***
[    0.452205] Platform Keyring initialized
[    0.454377] Key type asymmetric registered
[    0.454378] Asymmetric key parser 'x509' registered
[    0.454382] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 244)
[    0.454396] io scheduler mq-deadline registered
[    0.454938] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.454965] efifb: probing for efifb
[    0.454976] efifb: showing boot graphics
[    0.460754] efifb: framebuffer at 0xa0000000, using 8640k, total 8640k
[    0.460754] efifb: mode is 1920x1080x32, linelength=8192, pages=1
[    0.460754] efifb: scrolling: redraw
[    0.460755] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.460778] fbcon: Deferring console take-over
[    0.460778] fb0: EFI VGA frame buffer device
[    0.460782] intel_idle: does not run on family 6 model 165
[    0.460889] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.460902] ACPI: Sleep Button [SLPB]
[    0.460921] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.460930] ACPI: Power Button [PWRB]
[    0.460945] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.460963] ACPI: Power Button [PWRF]
[    0.461218] Monitor-Mwait will be used to enter C-1 state
[    0.461219] Monitor-Mwait will be used to enter C-2 state
[    0.462415] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.483519] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.484687] Linux agpgart interface v0.103
[    0.486006] loop: module loaded
[    0.486108] libphy: Fixed MDIO Bus: probed
[    0.486109] tun: Universal TUN/TAP device driver, 1.6
[    0.486122] PPP generic driver version 2.4.2
[    0.486146] VFIO - User Level meta-driver version: 0.3
[    0.486198] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.486199] ehci-pci: EHCI PCI platform driver
[    0.486204] ehci-platform: EHCI generic platform driver
[    0.486209] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.486209] ohci-pci: OHCI PCI platform driver
[    0.486213] ohci-platform: OHCI generic platform driver
[    0.486216] uhci_hcd: USB Universal Host Controller Interface driver
[    0.486348] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.486351] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.487408] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x110 quirks 0x0000000000009810
[    0.487411] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.487535] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.04
[    0.487536] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487536] usb usb1: Product: xHCI Host Controller
[    0.487537] usb usb1: Manufacturer: Linux 5.4.0-74-generic xhci-hcd
[    0.487538] usb usb1: SerialNumber: 0000:00:14.0
[    0.487588] hub 1-0:1.0: USB hub found
[    0.487603] hub 1-0:1.0: 16 ports detected
[    0.487828] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.487830] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.487831] xhci_hcd 0000:00:14.0: Host supports USB 3.1 Enhanced SuperSpeed
[    0.487849] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.04
[    0.487850] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487850] usb usb2: Product: xHCI Host Controller
[    0.487851] usb usb2: Manufacturer: Linux 5.4.0-74-generic xhci-hcd
[    0.487851] usb usb2: SerialNumber: 0000:00:14.0
[    0.487894] hub 2-0:1.0: USB hub found
[    0.487903] hub 2-0:1.0: 8 ports detected
[    0.488032] i8042: PNP: No PS/2 controller found.
[    0.488054] mousedev: PS/2 mouse device common for all mice
[    0.488124] rtc_cmos rtc_cmos: RTC can wake from S4
[    0.488741] rtc_cmos rtc_cmos: registered as rtc0
[    0.488750] rtc_cmos rtc_cmos: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.488753] i2c /dev entries driver
[    0.488775] device-mapper: uevent: version 1.0.3
[    0.488803] device-mapper: ioctl: 4.41.0-ioctl (2019-09-16) initialised: dm-devel@redhat.com
[    0.488812] platform eisa.0: Probing EISA bus 0
[    0.488813] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.488814] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.488814] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.488815] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.488815] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.488816] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.488816] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.488817] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.488817] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.488818] platform eisa.0: EISA: Detected 0 cards
[    0.488819] intel_pstate: CPU model not supported
[    0.488943] ledtrig-cpu: registered to indicate activity on CPUs
[    0.488945] EFI Variables Facility v0.08 2004-May-17
[    0.493278] intel_pmc_core INT33A1:00:  initialized
[    0.493321] drop_monitor: Initializing network drop monitor service
[    0.493421] NET: Registered protocol family 10
[    0.496747] Segment Routing with IPv6
[    0.496761] NET: Registered protocol family 17
[    0.496807] Key type dns_resolver registered
[    0.497165] RAS: Correctable Errors collector initialized.
[    0.497185] microcode: sig=0xa0653, pf=0x2, revision=0xea
[    0.497310] microcode: Microcode Update Driver: v2.2.
[    0.497313] IPI shorthand broadcast: enabled
[    0.497316] sched_clock: Marking stable (496884216, 423904)->(501492122, -4184002)
[    0.497462] registered taskstats version 1
[    0.497469] Loading compiled-in X.509 certificates
[    0.497936] Loaded X.509 cert 'Build time autogenerated kernel key: 84f483cb2a9c7595af8120fb37a1c4d574413ba6'
[    0.498337] Loaded X.509 cert 'Canonical Ltd. Live Patch Signing: 14df34d1a87cf37625abec039ef2bf521249b969'
[    0.498736] Loaded X.509 cert 'Canonical Ltd. Kernel Module Signing: 88f752e560a1e0737e31163a466ad7b70a850c19'
[    0.498757] zswap: loaded using pool lzo/zbud
[    0.498796] Key type ._fscrypt registered
[    0.498796] Key type .fscrypt registered
[    0.501567] Key type big_key registered
[    0.502901] Key type encrypted registered
[    0.502903] AppArmor: AppArmor sha1 policy hashing enabled
[    0.503223] integrity: Loading X.509 certificate: UEFI:MokListRT
[    0.503237] integrity: Loaded X.509 cert 'SomeOrg: shim: a01ee84e9b37ace407961cc468c5909447878469'
[    0.503237] integrity: Loading X.509 certificate: UEFI:MokListRT
[    0.503393] integrity: Loaded X.509 cert 'Canonical Ltd. Master Certificate Authority: ad91990bc22ab1f517048c23b6655a268e345a63'
[    0.503478] ima: No TPM chip found, activating TPM-bypass!
[    0.503482] ima: Allocated hash algorithm: sha1
[    0.503486] ima: No architecture policies found
[    0.503492] evm: Initialising EVM extended attributes:
[    0.503492] evm: security.selinux
[    0.503492] evm: security.SMACK64
[    0.503493] evm: security.SMACK64EXEC
[    0.503493] evm: security.SMACK64TRANSMUTE
[    0.503493] evm: security.SMACK64MMAP
[    0.503494] evm: security.apparmor
[    0.503494] evm: security.ima
[    0.503494] evm: security.capability
[    0.503494] evm: HMAC attrs: 0x1
[    0.504397] PM:   Magic number: 8:985:978
[    0.504603] rtc_cmos rtc_cmos: setting system clock to 2024-01-23T08:58:58 UTC (1706000338)
[    0.506019] Freeing unused decrypted memory: 2040K
[    0.506226] Freeing unused kernel image memory: 2736K
[    0.562723] Write protecting the kernel read-only data: 22528k
[    0.563111] Freeing unused kernel image memory: 2008K
[    0.563210] Freeing unused kernel image memory: 1136K
[    0.569446] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    0.569448] Run /init as init process
[    0.612565] acpi PNP0C14:01: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:00)
[    0.614868] ahci 0000:00:17.0: version 3.0
[    0.615607] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.615615] r8169 0000:02:00.0: enabling device (0000 -> 0003)
[    0.617157] i801_smbus 0000:00:1f.4: SMBus using PCI interrupt
[    0.621114] cryptd: max_cpu_qlen set to 1000
[    0.624831] AVX2 version of gcm_enc/dec engaged.
[    0.624832] AES CTR mode by8 optimization enabled
[    0.626695] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.626697] ahci 0000:00:17.0: flags: 64bit ncq sntf clo only pio slum part ems deso sadm sds apst 
[    0.631659] libphy: r8169: probed
[    0.631794] r8169 0000:02:00.0 eth0: RTL8168h/8111h, 1c:61:b4:6d:38:4f, XID 541, IRQ 126
[    0.631795] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.631810] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.631818] r8169 0000:03:00.0: enabling device (0000 -> 0003)
[    0.640978] checking generic (a0000000 870000) vs hw (a0000000 8000000)
[    0.640979] fb0: switching to nouveaufb from EFI VGA
[    0.641054] nouveau 0000:01:00.0: NVIDIA GK208B (b060b0b1)
[    0.647765] libphy: r8169: probed
[    0.647895] r8169 0000:03:00.0 eth1: RTL8168h/8111h, a8:a1:59:6e:1f:8b, XID 541, IRQ 128
[    0.647896] r8169 0000:03:00.0 eth1: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.687150] scsi host0: ahci
[    0.687341] scsi host1: ahci
[    0.687515] scsi host2: ahci
[    0.687601] scsi host3: ahci
[    0.687649] scsi host4: ahci
[    0.687693] scsi host5: ahci
[    0.687717] ata1: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419100 irq 125
[    0.687719] ata2: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419180 irq 125
[    0.687726] ata3: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419200 irq 125
[    0.687728] ata4: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419280 irq 125
[    0.687731] ata5: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419300 irq 125
[    0.687734] ata6: SATA max UDMA/133 abar m2048@0xab419000 port 0xab419380 irq 125
[    0.750641] nouveau 0000:01:00.0: bios: version 80.28.b8.00.05
[    0.751311] nouveau 0000:01:00.0: fb: 2048 MiB GDDR5
[    0.807321] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    0.830840] r8169 0000:03:00.0 enp3s0: renamed from eth1
[    0.834654] usb 1-6: new low-speed USB device number 2 using xhci_hcd

```

---

### Post by kotgc on 2024-01-23
Code 2/2:
```

[    1.002832] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.002888] ata2: SATA link down (SStatus 4 SControl 300)
[    1.002923] ata3: SATA link down (SStatus 4 SControl 300)
[    1.002977] ata5: SATA link down (SStatus 4 SControl 300)
[    1.003014] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.003620] ata1.00: ATA-10: INTEL SSDSC2KW240H6,  LSBG200, max UDMA/133
[    1.003621] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    1.003818] ata4.00: ATA-10: TS120GSSD220S, P1025F8, max UDMA/133
[    1.003819] ata4.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 32), AA
[    1.003968] ata4.00: READ LOG DMA EXT failed, trying PIO
[    1.003968] ata4.00: failed to get Identify Device Data, Emask 0x40
[    1.003974] ata4.00: failed to set xfermode (err_mask=0x40)
[    1.003978] fbcon: Taking over console
[    1.009248] usb 1-6: New USB device found, idVendor=04d9, idProduct=1503, bcdDevice= 3.10
[    1.009249] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.009250] usb 1-6: Product: USB Keyboard
[    1.009251] usb 1-6: Manufacturer:  
[    1.055063] hidraw: raw HID events driver (C) Jiri Kosina
[    1.079046] usbcore: registered new interface driver usbhid
[    1.079046] usbhid: USB HID core driver
[    1.080233] input:   USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:04D9:1503.0001/input/input3
[    1.142651] usb 1-9: new full-speed USB device number 3 using xhci_hcd
[     1.142844] hid-generic 0003:04D9:1503.0001: input,hidraw0: USB HID v1.10  Keyboard [  USB Keyboard] on usb-0000:00:14.0-6/input0
[     1.142919] input:   USB Keyboard System Control as  /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input4
[     1.202780] input:   USB Keyboard Consumer Control as  /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:04D9:1503.0002/input/input5
[     1.202866] hid-generic 0003:04D9:1503.0002: input,hidraw1: USB HID v1.10  Device [  USB Keyboard] on usb-0000:00:14.0-6/input1
[    1.296885] usb 1-9: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.10
[    1.296886] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.296886] usb 1-9: Product: USB Receiver
[    1.296887] usb 1-9: Manufacturer: Logitech
[     1.298953] input: Logitech USB Receiver as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:046D:C52B.0003/input/input6
[     1.358733] hid-generic 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11  Keyboard [Logitech USB Receiver] on usb-0000:00:14.0-9/input0
[     1.360402] input: Logitech USB Receiver Mouse as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input7
[     1.360520] input: Logitech USB Receiver Consumer Control as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input8
[     1.418719] input: Logitech USB Receiver System Control as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:046D:C52B.0004/input/input9
[     1.418841] hid-generic 0003:046D:C52B.0004: input,hiddev0,hidraw3: USB  HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-9/input1
[     1.420056] hid-generic 0003:046D:C52B.0005: hiddev1,hidraw4: USB HID  v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-9/input2
[    1.470719] tsc: Refined TSC clocksource calibration: 3696.086 MHz
[    1.470722] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x6a8dc8d4270, max_idle_ns: 881590498619 ns
[    1.478682] clocksource: Switched to clocksource tsc
[     1.806899] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw2: USB  HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-9/input2
[     1.927780] input: Logitech Unifying Device. Wireless PID:402d Keyboard  as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input11
[     1.927860] input: Logitech Unifying Device. Wireless PID:402d Mouse as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input12
[     1.927944] hid-generic 0003:046D:402D.0006: input,hidraw3: USB HID v1.11  Keyboard [Logitech Unifying Device. Wireless PID:402d] on  usb-0000:00:14.0-9/input2:1
[    2.059524] [TTM] Zone  kernel: Available graphics memory: 8143928 KiB
[    2.059525] [TTM] Zone   dma32: Available graphics memory: 2097152 KiB
[    2.059525] [TTM] Initializing pool allocator
[    2.059527] [TTM] Initializing DMA pool allocator
[    2.059548] nouveau 0000:01:00.0: DRM: VRAM: 2048 MiB
[    2.059549] nouveau 0000:01:00.0: DRM: GART: 1048576 MiB
[    2.059551] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
[    2.059551] nouveau 0000:01:00.0: DRM: DCB version 4.0
[    2.059552] nouveau 0000:01:00.0: DRM: DCB outp 00: 01000f02 00020030
[    2.059553] nouveau 0000:01:00.0: DRM: DCB outp 01: 02011f62 00020010
[    2.059554] nouveau 0000:01:00.0: DRM: DCB outp 02: 02022f10 00000000
[    2.059554] nouveau 0000:01:00.0: DRM: DCB conn 00: 00001031
[    2.059555] nouveau 0000:01:00.0: DRM: DCB conn 01: 00002161
[    2.059555] nouveau 0000:01:00.0: DRM: DCB conn 02: 00000200
[    2.059963] nouveau 0000:01:00.0: DRM: MM: using COPY for buffer copies
[    2.060581] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.060581] [drm] Driver supports precise vblank timestamp query.
[     2.225781] logitech-hidpp-device 0003:046D:402D.0006: hidraw3: USB HID  v1.11 Keyboard [Logitech M560] on usb-0000:00:14.0-9/input2:1
[    2.338159] nouveau 0000:01:00.0: DRM: allocated 1920x1080 fb: 0x80000, bo 000000003f12be75
[    2.338233] fbcon: nouveaudrmfb (fb0) is primary device
[    2.390482] Console: switching to colour frame buffer device 128x48
[    2.390858] nouveau 0000:01:00.0: fb0: nouveaudrmfb frame buffer device
[    2.406913] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 0
[    2.406914] nouveau 0000:01:00.0: DRM: Disabling PCI power management to avoid bug
[    6.206782] ata6: SATA link down (SStatus 4 SControl 300)
[    6.207585] ata1.00: configured for UDMA/133
[    6.207728] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSC2KW24 G200 PQ: 0 ANSI: 5
[    6.207860] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.208132] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/224 GiB)
[    6.208165] sd 0:0:0:0: [sda] Write Protect is off
[    6.208166] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.208229] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.224578]  sda: sda1 sda2
[    6.224818] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.522359] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    6.523820] ata4.00: configured for UDMA/133
[    6.523917] scsi 3:0:0:0: Direct-Access     ATA      TS120GSSD220S    5F8  PQ: 0 ANSI: 5
[    6.523989] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[    6.524099] sd 3:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    6.524104] sd 3:0:0:0: [sdb] Write Protect is off
[    6.524105] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.524114] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.542582]  sdb: sdb1 sdb2
[    6.542792] sd 3:0:0:0: [sdb] Attached SCSI disk
[    6.958688] raid6: avx2x4   gen() 42325 MB/s
[    7.006688] raid6: avx2x4   xor() 26140 MB/s
[    7.054687] raid6: avx2x2   gen() 36362 MB/s
[    7.102675] raid6: avx2x2   xor() 23459 MB/s
[    7.150687] raid6: avx2x1   gen() 30463 MB/s
[    7.198687] raid6: avx2x1   xor() 21380 MB/s
[    7.246674] raid6: sse2x4   gen() 17749 MB/s
[    7.294688] raid6: sse2x4   xor() 11291 MB/s
[    7.342677] raid6: sse2x2   gen() 15146 MB/s
[    7.390688] raid6: sse2x2   xor() 10192 MB/s
[    7.438690] raid6: sse2x1   gen() 13442 MB/s
[    7.486674] raid6: sse2x1   xor()  7968 MB/s
[    7.486674] raid6: using algorithm avx2x4 gen() 42325 MB/s
[    7.486675] raid6: .... xor() 26140 MB/s, rmw enabled
[    7.486675] raid6: using avx2x2 recovery algorithm
[    7.488317] xor: automatically using best checksumming function   avx       
[    7.498229] Btrfs loaded, crc32c=crc32c-intel
[    7.556420] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    7.742700] systemd[1]: Inserted module 'autofs4'
[     7.764874] systemd[1]: systemd 245.4-4ubuntu3.7 running in system mode.  (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP  +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS  +KMOD +IDN2 -IDN +PCRE2 default-hierarchy=hybrid)
[    7.782803] systemd[1]: Detected architecture x86-64.
[    7.819155] systemd[1]: Set hostname to <linuxmint>.
[    7.966004] systemd[1]: Created slice system-modprobe.slice.
[    7.966156] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    7.966291] systemd[1]: Created slice User and Session Slice.
[    7.966318] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    7.966447] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    7.966467] systemd[1]: Reached target User and Group Name Lookups.
[    7.966473] systemd[1]: Reached target Remote File Systems.
[    7.966476] systemd[1]: Reached target Slices.
[    7.966511] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[    7.966552] systemd[1]: Listening on LVM2 poll daemon socket.
[    7.966585] systemd[1]: Listening on Syslog Socket.
[    7.967273] systemd[1]: Listening on Process Core Dump Socket.
[    7.967311] systemd[1]: Listening on fsck to fsckd communication Socket.
[    7.967334] systemd[1]: Listening on initctl Compatibility Named Pipe.
[    7.967406] systemd[1]: Listening on Journal Audit Socket.
[    7.967442] systemd[1]: Listening on Journal Socket (/dev/log).
[    7.967481] systemd[1]: Listening on Journal Socket.
[    7.967524] systemd[1]: Listening on udev Control Socket.
[    7.967554] systemd[1]: Listening on udev Kernel Socket.
[    7.968027] systemd[1]: Mounting Huge Pages File System...
[    7.968451] systemd[1]: Mounting POSIX Message Queue File System...
[    7.968903] systemd[1]: Mounting Kernel Debug File System...
[    7.969405] systemd[1]: Mounting Kernel Trace File System...
[    7.970137] systemd[1]: Starting Journal Service...
[    7.970604] systemd[1]: Starting Availability of block devices...
[    7.971264] systemd[1]: Starting Set the console keyboard layout...
[    7.971752] systemd[1]: Starting Create list of static device nodes for the current kernel...
[    7.972202] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
[    7.972226] systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
[    7.972562] systemd[1]: Condition check resulted in Set Up Additional Binary Formats being skipped.
[    7.972577] systemd[1]: Condition check resulted in File System Check on Root Device being skipped.
[    7.973530] systemd[1]: Starting Load Kernel Modules...
[    7.974159] systemd[1]: Starting Remount Root and Kernel File Systems...
[    7.974809] systemd[1]: Starting udev Coldplug all Devices...
[    7.975596] systemd[1]: Starting Uncomplicated firewall...
[    7.976854] systemd[1]: Mounted Huge Pages File System.
[    7.976976] systemd[1]: Mounted POSIX Message Queue File System.
[    7.977070] systemd[1]: Mounted Kernel Debug File System.
[    7.977155] systemd[1]: Mounted Kernel Trace File System.
[    7.977556] systemd[1]: Finished Availability of block devices.
[    7.977906] systemd[1]: Finished Create list of static device nodes for the current kernel.
[    7.978621] systemd[1]: Finished Uncomplicated firewall.
[    7.981262] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[    7.981996] systemd[1]: Finished Remount Root and Kernel File Systems.
[    7.982574] systemd[1]: Activating swap /swapfile...
[    7.986145] systemd[1]: Condition check resulted in Rebuild Hardware Database being skipped.
[    7.986176] systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
[    7.986862] systemd[1]: Starting Load/Save Random Seed...
[    7.988692] systemd[1]: Starting Create System Users...
[    7.992374] lp: driver loaded but no devices found
[    7.996736] ppdev: user-space parallel port driver
[    8.001171] systemd[1]: Finished Load Kernel Modules.
[    8.001987] systemd[1]: Mounting FUSE Control File System...
[    8.002746] systemd[1]: Mounting Kernel Configuration File System...
[    8.003572] systemd[1]: Starting Apply Kernel Variables...
[    8.004617] systemd[1]: Finished Load/Save Random Seed.
[    8.005163] systemd[1]: Mounted FUSE Control File System.
[    8.005264] systemd[1]: Mounted Kernel Configuration File System.
[    8.006393] systemd[1]: Finished Create System Users.
[    8.007156] systemd[1]: Starting Create Static Device Nodes in /dev...
[    8.017241] systemd[1]: Finished Apply Kernel Variables.
[    8.017565] systemd[1]: Started Journal Service.
[    8.022736] systemd-journald[373]: Received client request to flush runtime journal.
[    8.038747] Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k SSFS
[    8.226781] intel_pch_thermal 0000:00:12.0: enabling device (0000 -> 0002)
[    8.230651] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    8.426435] intel_rapl_common: Found RAPL domain package
[    8.426436] intel_rapl_common: Found RAPL domain core
[    8.426437] intel_rapl_common: Found RAPL domain dram
[    8.426439] intel_rapl_common: RAPL package-0 domain package locked by BIOS
[    8.426442] intel_rapl_common: RAPL package-0 domain dram locked by BIOS
[     8.437679] audit: type=1400 audit(1706000346.426:2): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="libreoffice-senddoc"  pid=638 comm="apparmor_parser"
[    8.438402] audit: type=1400  audit(1706000346.426:3): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="nvidia_modprobe" pid=643  comm="apparmor_parser"
[    8.438404] audit: type=1400  audit(1706000346.426:4): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="nvidia_modprobe//kmod" pid=643  comm="apparmor_parser"
[    8.438560] audit: type=1400  audit(1706000346.426:5): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="lsb_release" pid=635 comm="apparmor_parser"
[     8.438811] audit: type=1400 audit(1706000346.430:6): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="/usr/bin/man"  pid=642 comm="apparmor_parser"
[    8.438813] audit: type=1400  audit(1706000346.430:7): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="man_filter" pid=642 comm="apparmor_parser"
[     8.438815] audit: type=1400 audit(1706000346.430:8): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="man_groff" pid=642  comm="apparmor_parser"
[    8.439404] audit: type=1400  audit(1706000346.430:9): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="libreoffice-oopslash" pid=640  comm="apparmor_parser"
[    8.442134] audit: type=1400  audit(1706000346.430:10): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="libreoffice-xpdfimport" pid=647  comm="apparmor_parser"
[    8.442189] audit: type=1400  audit(1706000346.430:11): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/sbin/tcpdump" pid=641  comm="apparmor_parser"
[    8.484870] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    8.485171] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    8.485237] snd_hda_intel 0000:01:00.1: Disabling MSI
[    8.485240] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    8.502308] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC897: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    8.502310] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.502311] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    8.502312] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    8.502313] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    8.502314] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    8.502315] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    8.502316] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    8.535216] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    8.535256] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
[    8.535300] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[    8.535334] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[    8.535369] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[     9.191089] Generic FE-GE Realtek PHY r8169-200:00: attached PHY driver  [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-200:00, irq=IGNORE)
[    9.303880] r8169 0000:02:00.0 enp2s0: Link is Down
[     9.306601] Generic FE-GE Realtek PHY r8169-300:00: attached PHY driver  [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-300:00, irq=IGNORE)
[    9.415922] r8169 0000:03:00.0 enp3s0: Link is Down
[   12.805320] r8169 0000:02:00.0 enp2s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   12.805328] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   13.183235] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input21
[   13.183291] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input22
[   13.183338] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input23
[   13.183384] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input24
[   13.183427] input: HDA NVidia HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input25
[   13.919967] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   13.919980] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   25.805101] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   25.999129] logitech-hidpp-device 0003:046D:402D.0006: HID++ 2.0 device connected.
[   26.241098] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.271080] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.287080] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.301082] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.317085] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.333082] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.349084] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[   26.363064] logitech-hidpp-device 0003:046D:402D.0006: error in parameter
[    26.371114] input: Logitech Wireless Mouse M560 as  /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.2/0003:046D:C52B.0005/0003:046D:402D.0006/input/input26

```

---

