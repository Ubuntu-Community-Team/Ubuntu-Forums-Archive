---
title: "[URGENT] GRUB2 borked.. would like to fix before reboot"
date: 2014-03-07
forum: General Help
---

### Post by travisn000 on 2014-03-07
I used grub-customizer to modify my grub2 background, as well as change the order of some of the menu entries..  it started getting a bunch of errors, so I removed it, but the errors persist. 

Now everytime I try to run 'update-grub' I get errors;  the same errors also seem to prevent me from re-installing grub after removing it:

```

root@Ubuntu-Aspire-M5-583P:~# apt-get remove grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed

#######  <..completed without error..>  ########

root@Ubuntu-Aspire-M5-583P:~# apt-get install grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed

#######  <..removed non-related output>  ########

Generating grub.cfg ...
using custom appearance settings
Found background image: /home/tln/back.jpg
Found Windows Boot Manager on /dev/sdb2@/EFI/Microsoft/Boot/bootmgfw.efi
Found PCLinuxOS on /dev/sdb7
Found Windows Boot Manager on /dev/sdb2@/EFI/Microsoft/Boot/bootmgfw.efi
Found PCLinuxOS on /dev/sdb7
terminate called after throwing an instance of 'AssertException'
Aborted (core dumped)
dpkg: error processing grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 134
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 (= 2.00-19ubuntu2.1); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 grub-efi-amd64
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Ubuntu-Aspire-M5-583P:~# 


```

I'm guessing there is some corrupt config somewhere that was not removed with apt-get remove, but I'm not sure where to look.

Thanks!

---

### Post by phidia on 2014-03-07
Let [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") help you.

---

### Post by travisn000 on 2014-03-07
Thanks..  looks like it worked; seems I should have used apt-get purge, not remove to purge the config files ;D

> 
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7052456/](http://paste.ubuntu.com/7052456/)

In case you still experience boot problem, indicate this URL to:
(email removed) or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (256GB) disk!

The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

You may want to retry after activating the [Backup and rename Windows EFI files] option.


---

### Post by travisn000 on 2014-03-07
Thanks..  looks like it worked; seems I should have used apt-get purge, not remove to purge the config files ;D

> 
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7052456/](http://paste.ubuntu.com/7052456/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (256GB) disk!

The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

You may want to retry after activating the [Backup and rename Windows EFI files] option.


---

