---
title: "Update Manager error - E: dpkg was interrupted..."
date: 2008-06-11
forum: General Help
---

### Post by realityundefined on 2008-06-11
Forgive me, as I'm fairly new to Ubuntu and Linux.  When attempting to install updates from Update Manager, I get this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

Okay, so I do what it says, and get this:

```
job@ubutop:~$ sudo dpkg --configure -a
[sudo] password for job: 
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
```
Go to update manager, get the same thing all over again.  Help?

Thanks in advance.

---

### Post by mixtri on 2008-06-11
i thinks you can try running ssynaptic - select Edit from the menu then fix broken packages option.
I had this problem once and fixed it that way.

---

### Post by ruckstande on 2008-06-11
I'm having this same issue. I open the package manager now and get the error and then the package manager closes. I also have 3 kernels in the Grub menu. Is that normal? I started getting these errors after the second kernel appeared but the package manager would still work.

Got it to appear, the fix packages option didn't work.

---

### Post by realityundefined on 2008-06-11
I get the same error when trying to open synaptic... synaptic doesn't run either.

I have 2 kernels in grub on my laptop.  Desktop has 3, but updates fine.

---

### Post by plucky on 2008-06-11
realityundefined,


Open a terminal and ```
df
``` Your should find your boot partition is too full.

> gzip: stdout: No space left on device

Either increase the size of this partition or remove some of the older kernels in the /boot directory.```
ls -l /boot
``` lowercase L not a 1

To remove a kernel ```
sudo apt-get purge linux-image<some number>-generic
``` You need to fill in the number of the kernel you want to remove.


Good Luck

---

### Post by cariboo on 2008-06-11
Have a look at the eight line it will tell you what the problem is. To possibley fix this, in a terminal enter:

```
sudo apt-get clean
```

This will remove archived files from var/cache/apt/archives

Jim

---

### Post by realityundefined on 2008-06-11
Indeed, the boot partition is full.  Tried to remedy by removing older kernels.  
```
job@ubutop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5             11435740   3916076   6943336  37% /
varrun                  777648       104    777544   1% /var/run
varlock                 777648         0    777648   0% /var/lock
udev                    777648        64    777584   1% /dev
devshm                  777648        12    777636   1% /dev/shm
lrm                     777648     38176    739472   5% /lib/modules/2.6.24-17-generic/volatile
/dev/sdb6                45099     39619      3074  93% /boot
gvfs-fuse-daemon      11435740   3916076   6943336  37% /home/job/.gvfs
job@ubutop:~$ ls -l /boot
total 39442
-rw-r--r-- 1 root root  422607 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-05-01 13:59 abi-2.6.24-17-generic
-rw-r--r-- 1 root root  422667 2008-05-28 22:39 abi-2.6.24-18-generic
-rw-r--r-- 1 root root   79964 2008-04-10 12:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80071 2008-05-01 13:59 config-2.6.24-17-generic
-rw-r--r-- 1 root root   80071 2008-05-28 22:39 config-2.6.24-18-generic
drwxr-xr-x 2 root  999    1024 2008-06-11 15:55 grub
-rw-r--r-- 1 root  999 7877341 2008-04-25 10:18 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7349268 2008-04-22 14:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 7446055 2008-05-26 20:34 initrd.img-2.6.24-17-generic
-rw-r--r-- 1 root root 7446133 2008-05-26 20:33 initrd.img-2.6.24-17-generic.bak
drwxr-xr-x 2 root root   12288 2008-04-25 14:09 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905012 2008-05-01 13:59 System.map-2.6.24-17-generic
-rw-r--r-- 1 root root  905012 2008-05-28 22:39 System.map-2.6.24-18-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921944 2008-05-01 13:59 vmlinuz-2.6.24-17-generic
-rw-r--r-- 1 root root 1921528 2008-05-28 22:39 vmlinuz-2.6.24-18-generic
job@ubutop:~$ sudo apt-get purge linux-image 2.6.24.16-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

The last line is starting to become terribly familiar.  What next?

---

### Post by avtolle on 2008-06-11
Run that command again.

---

### Post by realityundefined on 2008-06-11
```
job@ubutop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
job@ubutop:~$ sudo apt-get purge linux-image 2.6.24-16-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
job@ubutop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
job@ubutop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
```

looks the same as before to me...

---

### Post by plucky on 2008-06-11
> sudo apt-get purge linux-image 2.6.24.16-generic

That command is not correct.You missed a -


```
sudo apt-get purge linux-image-2.6.24-16-generic
```

Try that and it should try to remove that kernel and update menu.lst


Good Luck,


p.s After the kernel is removed then retry the ```
sudo dpkg --configure -a
```

---

### Post by realityundefined on 2008-06-11
hmmm.  still not working....

```
job@ubutop:~$ sudo apt-get purge linux-image-2.6.24-16-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
job@ubutop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
```
Thanks for the assistance... my apologies for being such a noob.

---

### Post by plucky on 2008-06-11
Wow Don't know why that doesn't work.Maybe try 
```
sudo apt-get deinstall linux-image-2.6.24-16-generic
```


All we are doing is trying to get some space back in your /boot partition.

---

### Post by realityundefined on 2008-06-11
nope.  E: invalid operation deinstall....

I guess I can probably enlarge the boot partition.  I have PartedMagic on CD...somewhere in the disorganization.  I'd rather not.  The CD ROM conked out on this lappy, so if I go that route, the HD's coming out and going in another PC for the partition work.  I don't know if we're running out of options, or what.  No matter, I really appreciate the help.

---

### Post by plucky on 2008-06-11
Yes deinstall doesn't work for me as well,even though it is an option in apt-get.

Try

```
sudo apt-get remove linux-image-2.6.24-16-generic
```

There must be a way to get this to work.

---

### Post by realityundefined on 2008-06-11
no luck with that either.  I get the same must run dpkg --configure -a message.  when input, that gives the same results as before.  I won't bother copying them here again.

---

### Post by plucky on 2008-06-11
Lets just try deleting some files from the /boot directory

> -rw-r--r-- 1 root root  422607 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-05-01 13:59 abi-2.6.24-17-generic
-rw-r--r-- 1 root root  422667 2008-05-28 22:39 abi-2.6.24-18-generic
-rw-r--r-- 1 root root   79964 2008-04-10 12:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80071 2008-05-01 13:59 config-2.6.24-17-generic
-rw-r--r-- 1 root root   80071 2008-05-28 22:39 config-2.6.24-18-generic
drwxr-xr-x 2 root  999    1024 2008-06-11 15:55 grub
-rw-r--r-- 1 root  999 7877341 2008-04-25 10:18 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7349268 2008-04-22 14:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 7446055 2008-05-26 20:34 initrd.img-2.6.24-17-generic
-rw-r--r-- 1 root root 7446133 2008-05-26 20:33 initrd.img-2.6.24-17-generic.bak
drwxr-xr-x 2 root root   12288 2008-04-25 14:09 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905012 2008-05-01 13:59 System.map-2.6.24-17-generic
-rw-r--r-- 1 root root  905012 2008-05-28 22:39 System.map-2.6.24-18-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921944 2008-05-01 13:59 vmlinuz-2.6.24-17-generic
-rw-r--r-- 1 root root 1921528 2008-05-28 22:39 vmlinuz-2.6.24-18-generic


```
cd /boot
ls -l
sudo rm initrd.img-2.6.24-16-generic.bak
sudo rm initrd.img-2.6.24-17-generic.bak
```

1) Go to /boot directory
2) make sure you are there
3) Delete these two files as they should only be backups.

```
sudo dpkg --configure -a
```

should now work.


The problem with this strategy is that sometime in the future you will again run into this problem,because your /boot partition is too small.

Can I ask why you have a separate /boot partition and not a seperate /home partition?

---

### Post by iaculallad on 2008-06-11
Try this on your terminal:

```
sudo apt-get install linux-util
```

After a successful install of linux-util:

```
sudo dpkg --configure -a
```

---

### Post by realityundefined on 2008-06-11
Breathe easy, it's working again.  Thank you so much for all the help.

---

### Post by friedfisherman on 2008-06-11
i had similar problem, but don't want to run into it again, how can i increase my boot partition size?

---

### Post by ruckstande on 2008-06-11
> **plucky said:**
> Lets just try deleting some files from the /boot directory



```
cd /boot
ls -l
sudo rm initrd.img-2.6.24-16-generic.bak
sudo rm initrd.img-2.6.24-17-generic.bak
```

1) Go to /boot directory
2) make sure you are there
3) Delete these two files as they should only be backups.

```
sudo dpkg --configure -a
```

should now work.


The problem with this strategy is that sometime in the future you will again run into this problem,because your /boot partition is too small.

Can I ask why you have a separate /boot partition and not a seperate /home partition?

This worked for me thank you. I'll tell you why I have a /boot partition. I have Ubuntu installed on a 250gb laptop hard drive. Apparently at the time I didn't know that the bios limit on my Dell laptop was around 150gb. I dual boot Windows and Linux so as per some install instructions I needed to have a /boot partition to get around the 250gb limit. Thanks for the help.

---

### Post by plucky on 2008-06-12
> **friedfisherman said:**
> i had similar problem, but don't want to run into it again, how can i increase my boot partition size?


You will probably need to shrink a partition next to your boot partition.You can use the Partition editor on the Live CD or download the [Gparted Live CD](http://gparted.sourceforge.net/) and burn to a CD.This is a very useful tool to have.

You cannot resize partitions when they are mounted,so you have to use an offline tool,which the Live CD or Gparted Cd is.The problem with resizing partitions is that the new partitions will change the UUID which can cause problems with booting and mounting.

Please post the output of ```
sudo fdisk -l
```

---

