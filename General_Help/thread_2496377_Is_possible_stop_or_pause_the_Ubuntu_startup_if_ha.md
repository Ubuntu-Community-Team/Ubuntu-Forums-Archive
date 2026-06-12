---
title: "Is possible stop or pause the Ubuntu startup if happen boot errors ?"
date: 2024-03-25
forum: General Help
---

### Post by aug7744 on 2024-03-25
Thanks for reading my topic.
Using in grub
GRUB_CMDLINE_LINUX_DEFAULT=#"quiet splash"
is showed lines for services and commands in Ubuntu boot startup.
Each line has an "OK" if was completed and "Failed" if not was possible run the command or other type of error.
Ubuntu allow stop or pause the boot startup process if not was possible run an command or service resulting in "FAILED" ?
Here randomly not is correctly mounted an mount pointing to /opt and nohang service is because the disk is HDD and are being done somes tasks at same time as the /home , /opt , an custom mount point /data and nohang.service. Randomly not have enough time to mount the partitions and need an OS reset in next boot all run correctly.

Have an nice week.

---

### Post by Rubi1200 on 2024-03-27
Not clear to me what you want to do.

Do you get to the login and desktop? Can you use your Ubuntu normally once logged in?

Perhaps checking your fstab file might give you some clues if something is not being mounted/mounted correctly.

---

### Post by grahammechanical on 2024-03-27
> Ubuntu allow stop or pause the boot startup process if not was possible run an command or service resulting in "FAILED" ?

The answer must be "NO"

The Linux bootloader (Grub) loads the operating system which may be Ubuntu or some other operating system. Therefore, Ubuntu is not in control of the boot process. Grub is in control.

If Grub hits a problem it will stop the boot process and offer a Grub command line where the user can put in certain Grub Commands.

Regards

---

### Post by aug7744 on 2024-03-28
Thanks for your reply.
Now I need see if grub allow stop the boot process if happen when "failed" message.
However the font used in messages look as if is being used ubuntu files.

---

