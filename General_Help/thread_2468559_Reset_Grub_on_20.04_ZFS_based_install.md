---
title: "Reset Grub on 20.04 ZFS based install ?"
date: 2021-11-03
forum: General Help
---

### Post by mat_london on 2021-11-03
Hi All,
I've got a home server running the default ZFS partition setup that you can choose when installing 20.04 i.e. bpool, rpool + I have another data pool
It's been running for a year fault free but I installed Grub Customizer without realising Grub Customizer doesn't really work with ZFS.
Once Grub Customizer has been used all the automatic grub updates and ability to boot to snapshots no longer work and I need this functionality.
So the question is does anyone know how to reset or reinstall grub on a default Ubuntu ZFS system so that it goes back to normal behaviour ?
Thanks in advance

---

### Post by Tadaen_Sylvermane on 2021-11-03
I don't know for sure. My guess is that it would be similar to getting into any other file system. In this case load a live disk and make sure to install the zfs-utils package? I'm assuming there is a way to import existing pools. Then chroot and do as normal effectively following the steps that you did in the first place when setting it up.

---

### Post by oldfred on 2021-11-03
Grub Customizer creates its own proxy files in the grub scripts folder. You may be able to restore the backups, but often easier just to do a new total reinstall of grub. If you edited any grub settings those will be lost. You can backup /etc/default/grub as that has some of the edited settings.

I preferred to learn how to edit grub directly, but some like the convenience of a gui with Grub Customizer.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

