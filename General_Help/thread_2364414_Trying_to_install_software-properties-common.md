---
title: "Trying to install software-properties-common"
date: 2017-06-23
forum: General Help
---

### Post by lingtalfi on 2017-06-23
I'm trying to install the let's encrypt certbot on my machine.

```
ling@host:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```

And at some point it goes down to enabling ppa.

```
sudo add-apt-repository ppa:certbot/certbot
```

The command above doesn't work on my machine:
```
sudo: add-apt-repository: command not found
```

Googling ppa I found that the first step to enable ppa is to install software-properties-common,
but here is what I get:

```
ling@host:~$ sudo apt-get install software-properties-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-81-generic : Depends: linux-image-4.4.0-81-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-81-generic but it is not going to be installed
                       Recommends: thermald but it is not going to be installed
 software-properties-common : Depends: python3-software-properties (= 0.96.20.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


And now I'm stuck.
I've no clue what I'm supposed to do.

I tried this:

```
ling@host:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-75-generic linux-image-4.4.0-81-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-75-generic linux-image-4.4.0-81-generic
0 upgraded, 2 newly installed, 0 to remove and 148 not upgraded.
14 not fully installed or removed.
Need to get 0 B/79.7 MB of archives.
After this operation, 134 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 278594 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-81-generic_4.4.0-81.104_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-81-generic (4.4.0-81.104) ...
Selecting previously unselected package linux-image-4.4.0-75-generic.
Preparing to unpack .../linux-image-4.4.0-75-generic_4.4.0-75.96_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-75-generic (4.4.0-75.96) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-75-generic_4.4.0-75.96_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-75-generic' to '/boot/vmlinuz-4.4.0-75-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-75-generic_4.4.0-75.96_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Do you have any idea why the commands don't work?

---

### Post by deadflowr on 2017-06-23
Run
```
sudo apt-get autoremove
```
post results if any.

The reason it's failing is because you have no space left to install the new kernel images.
see:
> cannot copy extracted data for './boot/vmlinuz-4.4.0-75-generic' to '/boot/vmlinuz-4.4.0-75-generic.dpkg-new': failed to write (No space left on device)

---

### Post by lingtalfi on 2017-06-23
```
ling@host:~$ sudo apt-get autoremove
[sudo] password for ling: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic linux-image-4.4.0-78-generic linux-image-extra-4.4.0-78-generic
0 upgraded, 0 newly installed, 4 to remove and 148 not upgraded.
8 not fully installed or removed.
After this operation, 297 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 279552 files and directories currently installed.)
Removing linux-image-extra-4.4.0-78-generic (4.4.0-78.99) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-78-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-78-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-78-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-78-generic (4.4.0-78.99) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-78-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Removing linux-headers-4.4.0-78-generic (4.4.0-78.99) ...
Removing linux-headers-4.4.0-78 (4.4.0-78.99) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-78-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


> The reason it's failing is because you have no space left to install the new kernel images.

It makes sense.
So I need to make some room...

Thanks.

---

### Post by lingtalfi on 2017-06-26
However, I still have plenty of room on /dev/sda2 (about 139G):

```

ling@host:home/ling# df -H
Filesystem      Size  Used Avail Use% Mounted on
udev            8.4G     0  8.4G   0% /dev
tmpfs           1.7G  152M  1.6G  10% /run
/dev/sda2       251G  100G  139G  42% /
tmpfs           8.4G     0  8.4G   0% /dev/shm
tmpfs           5.3M     0  5.3M   0% /run/lock
tmpfs           8.4G     0  8.4G   0% /sys/fs/cgroup
/dev/sda1       189M  176M     0 100% /boot
tmpfs           1.7G     0  1.7G   0% /run/user/1002
tmpfs           1.7G     0  1.7G   0% /run/user/1001

```


So, does the install process does not use /dev/sda2?

---

### Post by deadflowr on 2017-06-26
But boot is still full
And you won't fix anything until you fix the full boot partition, since you cannot fix the broken packaging until you can install the packages it wants you to install.
And those cannot be installed if you have no space for them to be installed to.

Try removing just a single kernel image like
```
sudo dpkg -P linux-image-4.4.0-71-generic
```
See if that frees up space, or actaully works without errors...

---

