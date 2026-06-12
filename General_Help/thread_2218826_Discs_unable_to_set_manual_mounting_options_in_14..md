---
title: "Discs unable to set manual mounting options in 14.04"
date: 2014-04-22
forum: General Help
---

### Post by adrian89 on 2014-04-22
I've done a fresh install of 14.04 after I seen that the online upgrade process from 13.10 left me with a lot of unsolvable bugs.
The issue is that I cannot set manual mounting options from Discs on ext4 partition I used the same options as I did in past releases and worked(it also worked after I first did the upgrade).
Gparted can mount it, but I need to set it to mount on boot.

This is the error I get when trying to mount from Discs:
> Error mounting system-managed device /dev/sda8: Command-line `mount "/media/Tot-Ubuntu"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda8,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


 (udisks-error-quark, 0)

I have the following fields set:
Mount on startup- checked
Show in launcher- checked

Mounting options- nosuid,nodev,nofail,x-gfx-show
Mounting point- /media/Tot-Ubuntu
Identified by- LABEL=Tot-Ubuntu
Filesystem type- auto(tried setting it as ext4 also but no luck)

Tried mounting it with UUID but still no luck from Discs.
Only my ntfs partitions can mount.

[COLOR=#333333][FONT=UbuntuRegular]Solved it by modifying fstab. Probably a bug or something since I set the mounting options same as previous Ubuntu releases.
[/FONT][/COLOR]

---

