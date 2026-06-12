---
title: "Problems with Kernel and /boot partition"
date: 2012-12-21
forum: General Help
---

### Post by RAND0M1ZER on 2012-12-21
Hello, so I'm in a bit of a jam and I was hoping my issue wouldn't be too difficult to fix.

What happened is my Ubuntu 12.04 LTS server was giving my errors when I was trying to do updates because my /boot partition was 99% full.

I thought I could fix this by removing some old kernels that I was no longer using but instead I managed to muck up the kernel I was using (3.2.0-35)

If I hold shift at boot to enter grub and then choose a previous version I'm able to get into my system fine.

How would I:
1) Revert to previous version of the kernel and then update
2) Fix my issue with available space on /boot

Any help would be greatly appreciated, THANKS!

---

### Post by oldfred on 2012-12-21
I am a desktop user and always use synaptic.

But I have this in my notes for command line. Someone with server may know better ways.

       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
# similar to this with all the versions except the one or two most recent. 
sudo apt-get purge /boot/vmlinuz-3.0.0-12-server

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by RAND0M1ZER on 2012-12-21
So I would do that when I've booted into a working kernel?

sudo apt-get purge /boot/vmlinuz-3.0.0-12-server


I don't want to mess things up further :S

---

### Post by oldfred on 2012-12-21
That was just an example, you have to use whatever the ls vmlinuz lists as all the kernels but not the one you are running. 
Usually best to also leave one other as a backup.

---

### Post by RAND0M1ZER on 2012-12-21
Okay so I need to run that command once for every old kernel I want removed? and that should free up some space?

And if I do it to the newest kernel which I already messed up will it automatically remove it as the default boot option?

---

### Post by steeldriver on 2012-12-21
I think you would need to remove/purge the** linux-image** package corresponding to each unwanted vmlinuz image, e.g.

```
$ ls /boot/vmlinuz*
/boot/[COLOR=Red]vmlinuz-3.2.0-29-generic-pae[/COLOR]  /boot/vmlinuz-3.2.0-32-generic-pae  /boot/vmlinuz-3.2.0-34-generic-pae
/boot/vmlinuz-3.2.0-31-generic-pae  /boot/vmlinuz-3.2.0-33-generic-pae  /boot/vmlinuz-3.2.0-35-generic-pae
$
$ sudo apt-get purge [COLOR=Red]linux-image-3.2.0-29-generic-pae[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.2.0-29-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 113 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 100345 files and directories currently installed.)
Removing linux-image-3.2.0-29-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic-pae /boot/vmlinuz-3.2.0-29-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-29-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic-pae /boot/vmlinuz-3.2.0-29-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-33-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-33-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-31-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-31-generic-pae
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-29-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic-pae /boot/vmlinuz-3.2.0-29-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic-pae /boot/vmlinuz-3.2.0-29-generic-pae
$
$ ls /boot/vmlinuz*
/boot/[COLOR=Red]vmlinuz-3.2.0-31-generic-pae[/COLOR]  /boot/vmlinuz-3.2.0-33-generic-pae  /boot/vmlinuz-3.2.0-35-generic-pae
/boot/vmlinuz-3.2.0-32-generic-pae  /boot/vmlinuz-3.2.0-34-generic-pae

```

---

### Post by RAND0M1ZER on 2012-12-22
Thanks you so so much! That fixed it, although I had to manually remove some files in /boot using the rm command to make some room before it would work. It rebuilt the grub file for 3.2.0-35 and its back up and running.

One last question though, I still have 95% of /boot filled and when I try sudo apt-get purge linux-image-3.2.0-xx-generic-pae I get,

```

administrator@Server:/boot$ sudo apt-get purge linux-image-3.2.0-27-generic-pae
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-image-3.2.0-27-generic-pae:i386 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But when I go to the /boot directory I can see that I still have files associated with those kernels there taking up space.

```

administrator@Server:/boot$ ls
abi-3.2.0-24-generic
abi-3.2.0-25-generic
abi-3.2.0-26-generic
abi-3.2.0-27-generic
abi-3.2.0-29-generic
abi-3.2.0-31-generic
abi-3.2.0-32-generic
abi-3.2.0-33-generic
abi-3.2.0-34-generic
abi-3.2.0-35-generic
config-3.2.0-25-generic
config-3.2.0-26-generic
config-3.2.0-27-generic
config-3.2.0-29-generic
config-3.2.0-31-generic
config-3.2.0-32-generic
config-3.2.0-33-generic
config-3.2.0-34-generic
config-3.2.0-35-generic
grub
initrd.img-3.2.0-25-generic
initrd.img-3.2.0-26-generic
initrd.img-3.2.0-27-generic
initrd.img-3.2.0-29-generic
initrd.img-3.2.0-31-generic
initrd.img-3.2.0-32-generic
initrd.img-3.2.0-33-generic
initrd.img-3.2.0-34-generic
initrd.img-3.2.0-35-generic
lost+found
memtest86+.bin
memtest86+_multiboot.bin
System.map-3.2.0-24-generic
System.map-3.2.0-25-generic
System.map-3.2.0-26-generic
System.map-3.2.0-27-generic
System.map-3.2.0-29-generic
System.map-3.2.0-31-generic
System.map-3.2.0-32-generic
System.map-3.2.0-33-generic
System.map-3.2.0-34-generic
System.map-3.2.0-35-generic
vmlinuz-3.2.0-26-generic
vmlinuz-3.2.0-27-generic
vmlinuz-3.2.0-29-generic
vmlinuz-3.2.0-31-generic
vmlinuz-3.2.0-32-generic
vmlinuz-3.2.0-33-generic
vmlinuz-3.2.0-34-generic
vmlinuz-3.2.0-35-generic

```

Thanks again for the help everyone.

---

### Post by oldfred on 2012-12-22
I thought the purge as opposed to a remove would also remove those files, but obviously it did not.

You can also remove those except of course for the one you are using and probably one backup. Just be consistent on which you save.

You are running the desktop 32 bit version. Do you have the gui also?

---

### Post by steeldriver on 2012-12-22
Yes I agree, that's odd - I just did a further test (been meaning to clean out some old kernels on my 12.04 server anyway) and even [FONT=Courier New]apt-get remove[/FONT] took care of everything in /boot:

```
$ dpkg -l | grep linux-image
ii  linux-image-[COLOR=Red]3.2.0-31[/COLOR]-generic-pae   3.2.0-31.50                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic-pae   3.2.0-32.51                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae   3.2.0-33.52                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic-pae   3.2.0-34.53                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae            3.2.0.35.40                  Generic Linux kernel image

``````
$ ls /boot/*-[COLOR=Red]3.2.0-31[/COLOR]*
/boot/abi-3.2.0-31-generic-pae     /boot/initrd.img-3.2.0-31-generic-pae  /boot/vmlinuz-3.2.0-31-generic-pae
/boot/config-3.2.0-31-generic-pae  /boot/System.map-3.2.0-31-generic-pae
``````
$ sudo apt-get remove linux-image-[COLOR=Red]3.2.0-31[/COLOR]-generic-pae
Reading package lists... Done
.
.
.
done
``````
$ ls /boot/*-[COLOR=Red]3.2.0-31[/COLOR]*
ls: cannot access /boot/*-[COLOR=Red]3.2.0-31[/COLOR]*: No such file or directory

```It does leave *something* behind - dpkg says the package is 'rc' (**r**emoved - but **c**onfiguration files remain):

```

$ dpkg -l | grep linux-image
**[COLOR=Red]rc[/COLOR]  linux-image-[COLOR=Red]3.2.0-31[/COLOR]-generic-pae   3.2.0-31.50                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP**
ii  linux-image-3.2.0-32-generic-pae   3.2.0-32.51                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae   3.2.0-33.52                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic-pae   3.2.0-34.53                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                  Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae            3.2.0.35.40                  Generic Linux kernel image
$

```A subsequent purge finally nails it by running /etc/kernel/postrm.d/initramfs-tools again - after which dpkg shows nothing

```
$ sudo apt-get purge linux-image-[COLOR=Red]3.2.0-31[/COLOR]-generic-pae
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.2.0-31-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 91593 files and directories currently installed.)
Removing linux-image-3.2.0-31-generic-pae ...
Purging configuration files for linux-image-3.2.0-31-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae

```If you are running a GUI then ubuntu-tweak has a nice tool for all this

---

### Post by RAND0M1ZER on 2012-12-22
Actually I'm running Ubuntu Server without a GUI, I guess I'll just remove them manually then. It was probably something I did earlier that messed it up, so that's why its not working.

Thanks

---

