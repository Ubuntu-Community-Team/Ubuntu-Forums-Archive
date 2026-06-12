---
title: "Ubuntu newbe... accidentally messed stuff up?"
date: 2024-04-08
forum: General Help
---

### Post by mongo42 on 2024-04-08
Hi all,

Despite using Ubuntu for several years, I am still extremely wet behind the ears.  I simply wanted to find out the installed version of Grub via the command "grub-install" but accidentally entered a lower case "-v" as opposed to an uppercase "-V".  Looking at the man page for "grub-install" I see that a lowercase "v" simply means "verbose" not "version".  Below is the output I got (note that I did not elevate my privileges first... no "sodu"... did this save my bacon?).  Did I mess up my existing Grub installation by overwriting it?  Thanks!

> Your Command, Oh Master? grub-install -v
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ...found.
Installing for x86_64-efi platform.
grub-install: info: cannot open `/boot/grub/device.map': No such file or directory.
grub-install: info: /dev/sda1 is not present.
grub-install: info: Looking for /dev/sda1.
grub-install: info: /dev/sda is a parent of /dev/sda1.
grub-install: info: /dev/sda1 starts from 2048.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: warning: disk does not exist, so falling back to partition device /dev/sda1.
grub-install: info: /dev/sda1 is present.
grub-install: info: Looking for /dev/sda1.
grub-install: info: /dev/sda is a parent of /dev/sda1.
grub-install: info: /dev/sda1 starts from 2048.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: warning: disk does not exist, so falling back to partition device /dev/sda1.
grub-install: info: /dev/sda1 is present.
grub-install: info: Looking for /dev/sda1.
grub-install: info: /dev/sda is a parent of /dev/sda1.
grub-install: info: /dev/sda1 starts from 2048.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: warning: disk does not exist, so falling back to partition device /dev/sda1.
grub-install: info: drive = 1.
grub-install: error: disk `hostdisk//dev/sda1' not found.

---

### Post by MAFoElffen on 2024-04-08
So it had an incomplete grub-install verbose command, since no device  given defaulted to /dev/sda, without any elevated permissions...

It didn't do anything. Because it couldn't find /dev/sda1, nor /dev/sda... It also looks like, since you meant to just check the version, you did it without using 'sudo', which you wouldn't need to, to check the version of... So it didn't have write permissions to do anything anyways.

FYI, instead do:
```

grub-install -V
# OR
grub-install --version

```
So no harm, no foul.

---

### Post by mongo42 on 2024-04-08
That's exactly what I wanted to hear (read)!  I have (in the past) really messed stuff up by a simple typo on previous installs, that I am somewhat paranoid (I would make a terrible Sys Admin).  Thanks!

---

### Post by oldfred on 2024-04-08
I have run grub-install from my UEFI install without errors. 
It defaults to use ESP - efi system partition mounted in fstab.
So do you not have an ESP in fstab? Or is it from a drive that now does not exist, by UUID.
Post in code tags, using # in Forum's Go Advanced editor.
cat /etc/fstab
lsblk -f

---

