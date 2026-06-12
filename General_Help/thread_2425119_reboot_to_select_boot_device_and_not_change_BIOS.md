---
title: "reboot to select boot device and not change BIOS"
date: 2019-08-20
forum: General Help
---

### Post by bjlockie on 2019-08-20
I have UEFI fastboot set in my BIOS so the computer boots fast but I can't select an alternate boot device.
This seems to work for me but I don't think there is any standard for getting the BIOS settings screen when using UEFI fastboot.

`systemctl reboot --firmware-setup`

Does anyone know of a command to reboot to select the boot device only and not change the BIOS?

---

### Post by oldfred on 2019-08-20
Do not know if this still works or not.
[https://ubuntuforums.org/showthread.php?t=1310463](https://ubuntuforums.org/showthread.php?t=1310463)

[https://ubuntuforums.org/showthread.php?t=2309436&page=2&p=13423016#post13423016](https://ubuntuforums.org/showthread.php?t=2309436&page=2&p=13423016#post13423016)

---

### Post by bjlockie on 2019-08-21
sudo efibootmgr --bootnext 0002
worked.
Thanks for the reply.

---

