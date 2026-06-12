---
title: "Ubuntu doesn't boot"
date: 2014-07-25
forum: General Help
---

### Post by thibault3 on 2014-07-25
Hello forum

I've been using ubuntu 14.04 for a while now and I really like it.
I've been dual booting together with windows 8.1
But today, the boot menu where you can choose what you want to boot dissapeared...
I managed to use boot repair and before I repaired anything, I made an url:
[http://paste.ubuntu.com/7854201/](http://paste.ubuntu.com/7854201/)
Can anyone help me or point me to the specific forum? (in case I missed xd)

Thanks in advance

---

### Post by thibault3 on 2014-07-25
It is solved, after +-6 hours searching and fooling around I managed to solve it with boot repair, man uefi is a Royal pain in the butt.

---

### Post by oldfred on 2014-07-25
It looks like you ran Boot-Repair in Legacy/BIOS/CSM mode. Be sure to always boot in UEFI mode as both Windows & Ubuntu are in UEFI boot mode.

Windows likes to make itself first in boot order. And some vendors have modified UEFI to only boot Windows. It looks like yours is a Sony which has that issue.

Did you run Boot-Repair before and it ran its 'buggy' UEFI fix? Some other renames work better than the one Boot-Repair does. Boot-Repair renames bootmgfw.efi.

       One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )

      
  HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
With encryption but you do not have to
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)

 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)

      
 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

