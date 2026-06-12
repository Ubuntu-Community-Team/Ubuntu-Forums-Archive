---
title: "unable to boot into OS"
date: 2013-05-21
forum: General Help
---

### Post by rmcellig on 2013-05-21
I am using Australis MATE which is based on Ubuntu 12.04. Never had any problems booting into it until now. This is my GRUB entry:

title Australis LTS (Mate Edition) (sda6)
  uuid 00965684-5c30-4e06-8e41-f8e47ccee349
  kernel /vmlinuz root=/dev/sda6 ro

What should I do? Is there anything I can post back that may help? I'd like to capture the notices that appear on startup but I am not sure if there is a way to do this or maybe there is a log file or something similar?

Thanks!!!

---

### Post by Bucky Ball on 2013-05-21
Have you tried:

```
# title Australis LTS (Mate Edition) (sda6)
uuid 00965684-5c30-4e06-8e41-f8e47ccee349
kernel /vmlinuz root=/dev/sda6 ro
```

It would help if you could be more specific. What is actually happening from the moment you boot the machine to when it crashes and how is it crashing?

---

### Post by oldfred on 2013-05-21
That is not a grub2 type entry. If based on Ubuntu 12.04, I would think it would use grub2? Or does it use another boot loader as it is not a full install?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by rmcellig on 2013-05-21
I use Grub4DOS that is part of Puppy Linux. The other distros work fine (WattOS, Bodhi Linux). I had the same issue with Manjaro and all I had to do was tweak this part of it:

kernel /vmlinuz root=/dev/sda6 ro

The error I get on startup is a KP error

---

### Post by rmcellig on 2013-05-21
This is exactly what I am seeing on startup:

Please append a correct “root=” boot option: here are the available partitions:

kernel panic - not syncing: VFS: unable to mount root fs on unknown -block (0,0)

Pid: 1, comm: swapper/0 Not tainted 3.5.0 -30-generic  #51 precise 1-ubuntu

Call trace:

---

### Post by rmcellig on 2013-05-21
I have been using Grub4DOS because it is pretty straight forward. If there is another way to create a Grub2 menu that is pretty straight forward, please let me know. I would really appreciate it!!


Thanks!!!

---

### Post by rmcellig on 2013-05-21
Problem solved!


I installed and reconfigured my grub menu using Grub- customizer.

I would still like to know if there are alternate ways to set up Grub. Thanks!!

---

### Post by oldfred on 2013-05-21
I use grub2, but it has a bit of a learning curve as it has a lot of new capabilities that then make it more complex.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

