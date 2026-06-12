---
title: "WUBI /host mount"
date: 2013-08-15
forum: General Help
---

### Post by jose_rojas2 on 2013-08-15
I have installed Ubuntu 13.04 with Wubi under Windows 8 Pro, but I want to move the directory where the NTFS partition gets mounted, how to I disable this /host mount or at least edit it so I can mount it somewhere else?

---

### Post by deadflowr on 2013-08-15
You can't.
/host is your Windows machine, which you might have guessed is the host that WUBI is running inside.
WUBI sets up a virtual file/file system within Windows which Ubuntu uses as a fake partition, so unmounted it would mean disconnecting your ubuntu install.

And beside, WUBI on Windows8 is unsupported. You should look into a real dual-boot.

---

### Post by oldfred on 2013-08-15
If you installed Windows 8 yourself in MBR, then wubi does work. It does not work on gpt partitions which all new Windows 8 pre-installed systems have.
 Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)


 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)


You may be able to edit the BCD, but I do not know all the details of which files have to be where.

 How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

      
 BCDedit to remove
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu/145605#145605](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu/145605#145605)


 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

