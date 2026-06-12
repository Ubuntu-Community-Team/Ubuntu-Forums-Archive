---
title: "Ubuntu 22.04 stuck in emergency mode"
date: 2023-04-30
forum: General Help
---

### Post by mageshwaran on 2023-04-30
Hi,
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292138&stc=1&thumb=1[/IMG]
   My laptop with ubuntu 22.04 stuck in the emergency mode. I don't get how it stuck in this mode. I have attached the files for the reference. After pressing control + D, it says transaction for graphical.target/start is destructive. 
I checked the UUID number obtained using blkid with that in the fstab, and they matches.

  Please suggest a way to resolve this problem. 

Thanks[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292138&stc=1&thumb=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292143&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292144&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292142&stc=1[/IMG]

---

### Post by idmbe on 2023-04-30
try this:
[https://askubuntu.com/questions/685946/how-to-exit-emergency-mode-and-boot-to-default-mode](https://askubuntu.com/questions/685946/how-to-exit-emergency-mode-and-boot-to-default-mode)

---

### Post by grahammechanical on 2023-04-30
You ran update-grub but did you run grub-install /dev/sda1?

That should replace any damaged Grub boot files with valid boot files.

Regards

---

### Post by mageshwaran on 2023-04-30
Thanks. I am trying mount -a but getting back "mount not found". When I run apt install mount, it says that the newest version is already installed. Can you suggest anything?

when I did df -h, the partition regarding /boot/efi is not visible.

---

### Post by idmbe on 2023-05-12
Type this and see results and if you can share it with us:
```
cat /etc/fstab
```

---

