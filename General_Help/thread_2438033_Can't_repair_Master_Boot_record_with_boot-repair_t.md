---
title: "Can't repair Master Boot record with boot-repair tool. Xubuntu/Windows 7"
date: 2020-03-04
forum: General Help
---

### Post by sic698 on 2020-03-04
Hi Guys,

I am unable to boot into any of my two operating systems, my 1st Partition is Xubuntu encrypted with Luks and my 2nd partition is windows 7 Pro.

When I run a live usb of ubuntu 18.04 LTS and then run boot-repair I get the following message 
[B]
You may want to retry after decrypting your partitions. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))
Do you want to continue?[/B]

I click on no and the operation is aborted, if I click yes and I continue the repair it doesn't repair my boot-records properly and I am unable to boot into either partition and no grub menu appears, all I get is a windows 7 repair window which never repairs the master boot record.

Thank you for having a look :)

---

### Post by sic698 on 2020-03-04
[IMG]https://ibb.co/sQwPzn7[/IMG]

---

### Post by oldfred on 2020-03-04
To repair or even just run report, Boot-Repair needs to see your system.
So if encrypted you have to mount and decrypt your install.

---

### Post by sic698 on 2020-03-04
Hi oldfred,

Thanks for replying to my post, Im unsure which commands I need to type in terminal to mount and decrypt my install

Can you provide assistance ?

thank you

---

### Post by sic698 on 2020-03-04
is there any one else that can help me ?

---

### Post by oldfred on 2020-03-04
I do not know LVM nor encryption. 
Some links:
Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

### Post by sic698 on 2020-03-04
```
**Setup ~ Desktop (Live) CD, Adding the tools to manage encrypted partitions**

 Resizing  an encrypted partition must be performed from a live CD and support for  encryption and LVM are not included on the live CD. 
1. Boot the live (Desktop) CD and install lvm2 and cryptsetup. 
sudo apt-get update && sudo apt-get install lvm2 cryptsetup2. Load the cryptsetup module. 
sudo modprobe dm-crypt3. Decrypt your file system. 
sudo cryptsetup luksOpen /dev/sda5 crypt14. Get the live CD to recognize (activate) your LVM. 
sudo vgscan --mknodes
sudo vgchange -ay
```



"step 3" 
sudo cryptsetup luksOpen /dev/sda5 crypt14. Get the live CD to recognize (activate) your LVM. 

After step 3 I enter my password and I get the following [B]message "Cannot use device /dev/sda5 which is in use (already mapped or mounted)."

[/B]im not sure how to proceed from here

---

### Post by oldfred on 2020-03-04
Is sda5 your encrypted partition?
those look like older instrucions.
Did you try the first link first?

---

### Post by sic698 on 2020-03-04
im using the 1st link you posted with instructions

[HTML]sudo apt-get install lvm2   #This step may or may not be required.
sudo pvscan                 #Use this to verify your LVM partition(s) is/are detected.
sudo vgscan                 #Scans for LVM Volume Group(s)
sudo vgchange -ay           #Activates LVM Volume Group(s)
sudo lvscan                 #Scans for available Logical Volumes
sudo mount /dev/YourVolGroup00/YourLogVol00 /YourMountPoint[/HTML]

[HTML]ubuntu@ubuntu:~$ sudo apt-get install lvm2
Reading package lists... Done
Building dependency tree   

ubuntu@ubuntu:~$ sudo lvscan
ubuntu@ubuntu:~$ 

    

sudo mount /dev/YourVolGroup00/YourLogVol00 /YourMountPoint 

I m stuck here I dont know what my volgroup is or my yourlogvol00 or /yourmountpoint is

Reading state information... Done
lvm2 is already the newest version (2.02.176-4.1ubuntu3.18.04.2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[/HTML]

```
ubuntu@ubuntu:~$ sudo pvscan
  No matching physical volumes found
ubuntu@ubuntu:~$ 


```

```
ubuntu@ubuntu:~$ sudo vgscan 
  Reading volume groups from cache.

```

ubuntu@ubuntu:~$ sudo vgchange -ay
ubuntu@ubuntu:~$

---

### Post by sic698 on 2020-03-04
[https://pasteboard.co/IXBnxQH.png](https://pasteboard.co/IXBnxQH.png)


heres a link of my gparted setup oldfred thanks for your help

---

### Post by sic698 on 2020-03-04
[HTML]ubuntu@ubuntu:~$ sudo modprobe dm-crypt
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 crypt1
Enter passphrase for /dev/sda5: 
ubuntu@ubuntu:~$ sudo vgscan --mknodes
  Reading volume groups from cache.
  Found volume group "xubuntu-vg" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -ay
  2 logical volume(s) in volume group "xubuntu-vg" now active
ubuntu@ubuntu:~$ 

[/HTML]


Heres the latest Im now launching boot-repair to see if it can repair my boot record

---

### Post by sic698 on 2020-03-04
You may want to retry after decrypting your partitions. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))
Do you want to continue?

Im getting this in boot repair.......

---

### Post by sic698 on 2020-03-04
my current gparted setup

[https://pasteboard.co/IXBvG9c.png](https://pasteboard.co/IXBvG9c.png)

---

### Post by oldfred on 2020-03-04
Is this an old encrypted /home and not a LVM full drive install with encryption?

Ubuntu has not supported encrypted /home for several versions.
What version of Ubuntu?
Is it still a supported version?

Includes chroot. /home encryption:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by sic698 on 2020-03-04
this is xubuntu 18.04 lts

---

### Post by sic698 on 2020-03-05
```
Hello I tested the following commands in my laptop - yeah I deleted everything in /dev/sda1 and I got it working again - so here it is:
  
[LIST]
[*]Get a live-image and boot from it.

[*]First lets get a clean /dev/sda1 - open **GParted**; reformat /dev/sda1 with **ext2** and don't forget to confirm the changes and then set the **"boot" flag**  (right click on the partition --> select "Manage Flags" --> check  the box next to "boot" [this automatically causes the "esp" flag to be  set to] --> click the "Close" button).

[*]Now we will prepare everything to chroot into the installed system and then we will switch into it (via chroot):
  sudo cryptsetup luksOpen /dev/sda5 sda5_crypt
sudo vgscan --mknodes
sudo vgchange -ay
sudo mount /dev/mapper/ubuntu--vg-root /mnt
sudo mount /dev/sda1 /mnt/boot
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt

[*]Okay let's delete and reinstall GRUB: apt purge grub-common (have your terminal in  fullscreen-mode due to ncurses), this might ask you if it shall delete  everything - select yes; now lets reinstall it with apt install grub-pc here select /dev/sda when asked.


[*]Lastly we need to reinstall a kernel to get the needed **initrd.img-*** and **vmlinuz-*** images into "/boot/". We get currently-installed kernels with apt list --installed linux-image-* and now we reinstall this kernel with apt install linux-image-[version-numbers]-generic --reinstall - don't forget to exchange the brackets with an actual version number.

[*]Almost done; exit chroot with Ctrl + d, or just type exit, and then reboot (via GUI menus or with sudo reboot)!

[/LIST]

```


[B]Okay let's delete and reinstall GRUB: apt purge grub-common (have your terminal in  fullscreen-mode due to ncurses), this might ask you if it shall delete  everything - select yes; now lets reinstall it with apt install grub-pc here select /dev/sda when asked.

[/B]I get stuck right at this step and I get the following errors in my terminal

```
root@xubuntu:/# apt purge grub-common
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@xubuntu:/# sudo dpkg --configure -a
Setting up linux-firmware (1.173.15) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-28-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-5.3.0-26-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-5.0.0-32-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-5.0.0-31-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-5.0.0-27-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-5.0.0-25-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-5.0.0-23-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
update-initramfs: Generating /boot/initrd.img-4.18.0-25-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-28-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-5fd0a4ed-5bfd-4901-804d-045564b26365 - 
root@xubuntu:/# 
```DE]

---

### Post by sic698 on 2020-03-05
Im now able to boot into grub and I see both my operating systems xbuntu and windows 7 using the instructions posted above

I am able to boot into windows, however I am not able to boot into my xubuntu os, Im get into the xbuntu splash screen and I than I get a black window with the following error

gave up waiting for root file system device common problems
-bootarg (cat /proc/cmdline)
-check root delay = did he system wait long enough)
-Missing modules (cat /proc/moduls; ls/dev

Busybox v.1.27.2

intitramfs 78.5144 random crng init done
intitramfs

I reinstalled the kernal ubuntu wiht linux 5.3.0-40-genric

---

### Post by sic698 on 2020-03-05
alert /dev/mapper/xubuntu--vg-root does not exist dropping to shell.

---

### Post by yancek on 2020-03-05
> alert /dev/mapper/xubuntu--vg-root does not exist dropping to shell. 

Do you see anything relating to that in your /etc/fstab or /etc/crypttab file?  You reported errors for the 2nd file in an earlier post.  I don't use encryption so I'm guessing but taking a look at these files certainly won't harm anything.

You didn't indicate whether any changes were made to the system just prior to this problem, were there?  Was the Xubuntu encrypted partition functional previously?

---

