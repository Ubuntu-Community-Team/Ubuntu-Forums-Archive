---
title: "Grub Customizer error with Burg"
date: 2016-09-10
forum: General Help
---

### Post by ultimatehawkeye on 2016-09-10
Hi there,

I'm having an error after launching Grub Customizer with Burg installed. When I start it up it says:
[INDENT]
burg-mkconfig couldn't be executed successfully. error message:
Generating burg.cfg
/usr/sbin/burg-probe: error: cannot stat '/boot/burg/locale'.
No path or device is specified.
Try '/usr/sbin/burg-probe --help' for more information
[/INDENT]

Most solutions I've found have not worked out for me, so any assistance will be appreciated :)

Thanks,
Will

---

### Post by oldfred on 2016-09-11
Burg is very old, not supported anymore.
It writes its own files to use in place of grub.

Grub customizer writes its own replacement of grub2 files also. So I see conflicts in trying to get both to work.

What is it that you are trying to do? On what system?

I generally just use grub2 and customize it myself.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

