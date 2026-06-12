---
title: "After an update ended up in emergency mode"
date: 2019-10-21
forum: General Help
---

### Post by serhin on 2019-10-21
Hello!

I am using Ubuntu 18.04 with KDE in dual boot with Windows 10. The package manager has done an update and after this system is booting in the emergency mode.

The output for the entering emergency mode is next: 

[IMG]https://cdn1.savepice.ru/uploads/2019/10/22/982915dd9c844632896137a7bf2edf33-full.jpg[/IMG]

Rebooting and setting "systemctl reboot" had no impact. Also, after pressing Control-D, the system tries to boot again, tries to processes the disk and enters emergency mode nearby 44 percent.
I have tried to launch the "fsck" from "Recovery mode", because in system logs I have found some problems from it hat does not show up in the output. However, after launch in this mode, system does not respond to any actions. So, I am not even able to select "fsck" option.

I would be glad if someone could help me with this situation. I am quite new in Ubuntu, so I might need some explanation of what happens.

Anyway, thank you in advance!

---

### Post by deadflowr on 2019-10-22
Try booting into an older kernel.
(At the boot screen ; where it lists Ubuntu and Windows to choose from.
select the Second Ubuntu option Advanced Options and then select the second ubuntu kernel listsed.\
The list should show something like
```
Ubuntu, with Linux some number-string
Ubuntu, with Linux some number-string (recover mode)
Ubuntu, with Linux some-other-number string
Ubuntu, with  Linux some-other-number string (recovery mode)
```

You would select the some-other-number string without the (recovery mode) line,
if that makes sense.

See if that gets you back into thew desktop, at least.

---

### Post by serhin on 2019-10-22
I tried older version of kernel, problem is still the same. System still enters the emergency mode on 44 percent of file check of the disk.

---

### Post by serhin on 2019-10-22
Sorry, I forgot to cite the post. I tried an older version of the kernel, the problem is still the same. The system still enters the emergency mode on 44 percent of the file check of the disk.

---

### Post by deadflowr on 2019-10-22
If you still have the installer media you used to install Kubuntu, you can use that to boot into what is known as a Live Session.
(marked as the Try Kubuntu option in the boot menu.)

Then you can try running fsck on the partition in trouble.
See: [https://help.ubuntu.com/community/FilesystemTroubleshooting]("https://help.ubuntu.com/community/FilesystemTroubleshooting")
for tips and pointers on the best fsck options to try.

---

### Post by serhin on 2019-10-22
Thank You very much! I have booted from flash drive which I used as an installer. I ran fsck and it located and fixed several issues on one of the partitions. Now everything works perfectly!

---

