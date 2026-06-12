---
title: "bootloader problem"
date: 2006-11-10
forum: General Help
---

### Post by welsh on 2006-11-10
ok, so i had SUSE and i decided to switch to Ubuntu instead. So i got the cd and installed it then took the cd out and restarted. Now here lies my problem, its a dual boot system with windows xp prof and ubuntu now. The SUSE partition got formated with the boot loader on it, now whenever i start up i get this error message:
```
GRUB Loading Stage1.5. GRUB loading, please wait... 
Error 17
```
when i installed ubuntu it didnt install a boot loader with it which u know isnt good cause the one its trying to use just doenst exist, can anyone help?

---

### Post by adwait on 2006-11-10
Well, Ubuntu should have installed the bootloader. nyway, boot off the live cd and use
```
sudo grub-install /dev/<your HD>
```

That should re install GRUB on your hard disk.

---

### Post by welsh on 2006-11-10
hey, i tried what you said and this is what i typed in and what i got out as a result:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

---

