---
title: "After Swap Format Grub Screen Error"
date: 2020-04-23
forum: General Help
---

### Post by tempaccount44 on 2020-04-23
Hello.
Yesterday I tried to install Ubuntu 18.04 to my USB Stick.
Created and set partitions on it. 
sdc1 : ext4, mount point / 
sdc2 : swap area
sdc3 : fat32, storage area

When I go next, ubuntu warned me with this:

[B]sda2 swap area will format
sdc1 will format
sdc2 will format
sdc3 will format[/B]

sdc was my Usb Stick, but why sda2 will format? 
Anyway I clicked next to learn if it fails. 
And after that, now I cannot enter my main system (linux mint on sda), 
only grub screen appears

/etc/fstab file:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=cfa69753-1281-4426-b366-efb23f6e8d34 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=DC0D-3AE7  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda4 during installation
UUID=32b02b87-fac6-467e-a52f-35110d1750a1 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=170b6689-668a-4931-ad85-5fd2d546315d swap            swap    sw              0       0
```


swapon command:
```
ubuntu@ubuntu:~$ swapon
NAME      TYPE      SIZE USED PRIO
/dev/sda2 partition 7.5G   0B   -2

```

free -m command:
```
ubuntu@ubuntu:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7851        1162        2996         744        3692        5647
Swap:          7629           0        7629
```


How can I fix this?

---

### Post by sisco311 on 2020-04-23
Is that the content of the fstab from Linux Mint?

What is the output of:
```
sudo blkid
```
?

---

### Post by tempaccount4444 on 2020-04-23
> **sisco311 said:**
> Is that the content of the fstab from Linux Mint?

What is the output of:
```
sudo blkid
```
?

Yes, linux mint is on sda (hdd)
Windows is on sdb (ssd)

Output: [http://paste.ubuntu.com/p/GKqJg5fbGm/]("http://paste.ubuntu.com/p/GKqJg5fbGm/")

(sorry it's hard to paste from mobile, had to upload there)

---

### Post by CatKiller on 2020-04-23
I have no idea why the installer wanted to format your existing swap partition; it will *use* any swap partitions it finds, so I guess it got confused.

However, formatting the swap partition will have changed its UUID, so the fstab for your Mint install is now looking in the wrong place. You can boot from an installer (Mint or Ubuntu, doesn't matter), mount the partition that has your Mint install on, and change the swap entry to point to the new UUID, which sisco311's command should have shown you (I'm also on mobile, so I haven't looked at your output).

You may also need to reconfigure Grub so that its hibernation resume entry is pointing to the right place, which you can either do once you've successfully booted or from a chroot from that installer.

---

### Post by sisco311 on 2020-04-23
@tempaccount4444    No problem. We are here to help.

From your first post, my impression was that the Ubuntu installer reformatted the swap partition of Linux Mint, but the partition's UUID did not change. 

So we have to dig deeper. Please provide your boot-info: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And please elaborate on what is happening when you try to boot to Mint. (Error messages...)

---

### Post by tempaccount4444 on 2020-04-23
sudo blkid output is

sda2 uuid="d32d6970..." type="swap" partuuid="b0d509ce..."

But in etc/fstab file (mint's fstab):
Dev/sda2 swap
Uuid=170b6689..

So it looks you're right, it's different uuid

So, I should replace d32d6970.. To 170b6689..
Right?


edit: it didnt work. Still stuck at grub screen :/

---

### Post by tempaccount4444 on 2020-04-23
> **CatKiller said:**
> You may also need to reconfigure Grub so that its hibernation resume entry is pointing to the right place, which you can either do once you've successfully booted or from a chroot from that installer.

I changed the uuid with output of blkid, but I dont know how to reconfigure grub

---

### Post by tempaccount4444 on 2020-04-23
> **sisco311 said:**
> @tempaccount4444    No problem. We are here to help.

From your first post, my impression was that the Ubuntu installer reformatted the swap partition of Linux Mint, but the partition's UUID did not change. 

So we have to dig deeper. Please provide your boot-info: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And please elaborate on what is happening when you try to boot to Mint. (Error messages...)


[https://paste.ubuntu.com/p/zQNwxY6ydk](https://paste.ubuntu.com/p/zQNwxY6ydk)

---

### Post by sisco311 on 2020-04-23
Hmmm, Instead of changing the UUID in your system's config files (fstab/grub) it would be (or is) more effective to reset the original UUID of the partition:
```
sudo mkswap --uuid *UUID* *device*
```

---

### Post by tempaccount4444 on 2020-04-23
> **sisco311 said:**
> Hmmm, Instead of changing the UUID in your system's config files (fstab/grub) it would be (or is) more effective to reset the original UUID of the partition:
```
sudo mkswap --uuid *UUID* *device*
```

Should I edit the code before paste to terminal, or paste completely same?

Edit: okay device is "/dev/sda2"
But which uuid I should use?

Edit2: I used the uuid which output of blkid. 
* sudo swapoff /dev/sda2
* sudo mkswap --uuid d32d69..7549 /dev/sda2
* sudo swapon /dev/sda2

But still I stuck at grub screen

---

### Post by CatKiller on 2020-04-23
> **tempaccount4444 said:**
> But still I stuck at grub screen

> **sisco311 said:**
> And please elaborate on what is happening when you try to boot to Mint. (Error messages...)

This is critical information. fstab tries to mount the swap partition, and Grub tries to see if there's a hibernation image in there, and both of them need to be looking in the right place to work, but we're only guessing at what the problem might be based on your description, which isn't a lot to go on at the moment.

---

### Post by tempaccount4444 on 2020-04-23
> **sisco311 said:**
> @tempaccount4444    No problem. We are here to help.

From your first post, my impression was that the Ubuntu installer reformatted the swap partition of Linux Mint, but the partition's UUID did not change. 

So we have to dig deeper. Please provide your boot-info: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And please elaborate on what is happening when you try to boot to Mint. (Error messages...)

> **CatKiller said:**
> This is critical information. fstab tries to mount the swap partition, and Grub tries to see if there's a hibernation image in there, and both of them need to be looking in the right place to work, but we're only guessing at what the problem might be based on your description, which isn't a lot to go on at the moment.

There is no error message, when I open the pc, this screen appears: 

GNU GRUB version 2.02
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. 

grub>

---

### Post by tempaccount4444 on 2020-04-23
After installing Ubuntu on my SSD (sdb), grub screen changed and I can managed to enter Linux Mint. 

I dont know how it fixed.
I wish I know how to fix grub configuration but I guess that it is hard. 

If you know what fixed the problem please tell me. 

Thank you for your supports by the way

---

### Post by CatKiller on 2020-04-23
Glad to hear it's working again. 

> **tempaccount4444 said:**
> I wish I know how to fix grub configuration but I guess that it is hard. 

It's not hard, it's just fiddly.

At the point where an operating system loads, there's no operating system loaded to load the operating system: that's called the bootstrapping problem, and is where the term "booting" comes from. The way Grub works is that it packages up everything that's needed to load an operating system into something that can be dumped into RAM and executed  (called the Initial RAM filesystem). When you want to change how the machine boots, you need to change the configuration and then package the changed environment into a new initramfs.

When you successfully installed Ubuntu, it needed to generate a new initramfs anyway (so it can boot) and, in doing so, it found your swap partition and your Mint install and used that information in the configuration that it generated.

---

### Post by oldfred on 2020-04-23
This was your issue.

```
search.fs_uuid a02fd866-77fd-4521-9733-e8c927f35b1a root hd2,gpt1 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

You did not have your external drive plugged in when you ran Boot-Repair report. Which will be hd2,gpt1 & UUID of install on external. 
And when you installed to external, it installed grub to ESP on internal drive making boot into external drive the default.
Only difference is the UUID & root to find full install's grub.cfg.

You can edit /boot/efi/EFI/ubuntu/grub.cfg, but if from within install may have permission issues.
Or from inside your install on hard drive, reinstall grub.

Whenever I install to sdb, or an external drive, first thing I do is edit UEFI boot back to main working install.
If you want to boot external from other computers, you have to have an ESP on that drive and before editing /EFI/Boot & /EFI/ubuntu move them to external drive's ESP. I would do this whether always booting from same system or not, as then  it would still be bootable, if you have issues on main drive.

UEFI only directly boots external drives from /EFI/Boot/bootx64.efi. The version of grub/shim that is renamed to bootx64.efi also requires the additional boot files in /EFI/ubuntu. 

If only booting from same internal drive, you can just run sudo update-grub and it will add the install in external drive to your grub boot stanza.

---

### Post by tempaccount4444 on 2020-04-23
@CatKiller

Thank you for the answer and help

---

### Post by tempaccount4444 on 2020-04-23
@oldfred

Thanks for explaining but I didnt understand about
"external" device

Mint was installed on internal hdd (sda)
Windows was installed on internal ssd (sdb)

---

### Post by oldfred on 2020-04-23
You said this in first post:
> Yesterday I tried to install Ubuntu 18.04 to my USB Stick.

A full  install of Ubuntu to any external device will install grub to first drive seen.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

---

### Post by tempaccount4444 on 2020-04-23
Oh, I understood. 
Thank you sir

---

