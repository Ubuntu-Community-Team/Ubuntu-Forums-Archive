---
title: "update-initramfs hangs"
date: 2008-01-19
forum: General Help
---

### Post by skulda on 2008-01-19
Hey!
I'm not really sure, how it happened. But after yesterdays security updates, my kubuntu gutsy doesn't boot anymore, I'm receiving a kernel panic. I'm using dmcrypt for my root partition (not for boot) and suppose, there is a problem with cryptsetup which causes the kernel panic.
Booting from a live cd, mounting local filesystems and chroot into the system on my harddisk I get the following problem when running "dpkg --configure -a" (which I'm ordered to run by apt-get upgrade i.e.)
```
root@ubuntu:/# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up cryptsetup (2:1.0.5-2ubuntu2.1) ...
update-initramfs: deferring update (trigger activated)              
```
And then nothing happens, I don't get a new prompt or anything. Pressing ctrl-c results in```
dpkg: error processing cryptsetup (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script killed by signal (Interrupt)

```
I already tried reinstalling udev, a hint I found in another forum. But that did not change anything.

Does anyone have an idea about what to do, because I can't really work with the system like that. And reinstalling the complete system is not what I really want to do...
Thanks in advance
Skulda

---

### Post by PriceChild on 2008-01-19
*moved and bumped*

---

### Post by skulda on 2008-01-19
Hey!
doesn't anyone have an idea? Is there anything unclear in the description of the problem?

I tried some things, installed new versions of some tools and now I get the following in the chroot environment:
```

root@ubuntu:/boot# dpkg --configure -a
Setting up cryptsetup (2:1.0.5-2ubuntu2.1) ...
update-initramfs: deferring update (trigger activated)
dpkg: error processing cryptsetup (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
cat: /proc/cmdline: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
device-mapper: version ioctl failed: Invalid argument
Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver
Command failed
cryptsetup: WARNING: failed to determine cipher modules to load for root
Errors were encountered while processing:
 cryptsetup

```

---

### Post by kvonb on 2008-01-19
-

---

### Post by skulda on 2008-01-19
Hey!
thanks for the hint! I tried the the backup-file and was at least able to reboot into the system.
But my problem is far from being solved. For now, I'm not able to install any new software or updates, because while doing so update-initramfs is run and hangs again.

So I would still be glad if anyone had an idea about what to do.
Skulda

---

### Post by kvonb on 2008-01-20
-

---

### Post by metalheart on 2008-01-20
There is an option for update-initramfs -b to give alternate boot directory. If you booted from Live CD to chroot, your boot files are on this root (/dev/sda5/boot in my case). The real boot files are on /dev/sda1/boot.

---

### Post by dmartin on 2008-02-17
I have this exact same problem on my headless server.  I've had Ubuntu on this box for about 2 1/2 years, and I am not doing any kind of chroot environments or anything wierd.  Something is really wrong.  This is definitely not something I caused -- just a normal apt-get update and apt-get upgrade to get up to date.

---

### Post by derhannes on 2008-02-27
Hello,

same thing happened on my computer, so I filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/185380](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/185380). Perhaps you are interested in its outcome, too.

---

### Post by derhannes on 2008-02-27
Following the instructions given [HERE]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/185380") , the problem was solved on my system:

My /etc/crypttab consisted of a line that contained a comment (starting with "#"):

```
root /dev/sda4 none luks,retry=1,cipher=aes-lrw-benbi # ab Kernel 2.6.20 (gutsy, feisty): cipher=aes-lrw-benbi
```

After putting the comment in a separate line
```
root /dev/sda4 none luks,retry=1,cipher=aes-lrw-benbi 
# ab Kernel 2.6.20 (gutsy, feisty): cipher=aes-lrw-benbi
```
the upgrade worked fine.

---

