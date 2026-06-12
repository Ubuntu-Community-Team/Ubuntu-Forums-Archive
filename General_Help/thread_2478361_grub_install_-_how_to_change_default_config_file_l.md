---
title: "grub install - how to change default config file location"
date: 2022-08-24
forum: General Help
---

### Post by vatharian on 2022-08-24
It appears that grub installed from Ubuntu, searches for grub.cfg for some reason in /EFI/ubuntu/, instead of /EFI/BOOT. This breaks my tools. How do I control that location? I saw it hardcoded in binary grubx64.efi, but there are no relevant options in grub-install.

---

### Post by tea for one on 2022-08-24
I do not have a directory /EFI/ubuntu

Boot files are found in the ESP (EFI System Partition) i.e. \EFI\ubuntu\shimx64.efi
grub.cfg is located in /boot/grub

> **vatharian said:**
> This breaks my tools.
What are these tools and what is their function?

---

### Post by vatharian on 2022-08-24
> **tea for one said:**
> I do not have a directory /EFI/ubuntu

Relative to ESP, of course, not in OS.

> **tea for one said:**
> What are these tools and what is their function?

Irrelevant, but I have other Linux systems on same disk that come without any bootloader and my tools supply custom grub.cfg on each boot.

---

### Post by Dennis N on 2022-08-24
There are two grub.cfg files. The one in the /EFI/ubuntu folder in the EFI system partition is used by the boot loader (also in the /EFI/ubuntu folder) to specify the location of the OS to boot. The one at /boot/grub/grub.cfg is a script that generates the grub menu you see each time you start up.

---

### Post by vatharian on 2022-08-24
/boot/grub/grub.cfg is part of an OS, not of an ESP. inside bootloader, grub has no access to it.

/EFI/ubuntu (or /boot/efi/EFI/ubuntu from OS' perspective) is the one I am interested in - the one that is actually used by grub during the boot process to draw the menu on screen and populate said menu with entires of OSes to boot.

problem is the /ubuntu/ part of the path. If I install grub from redhat it ends up in /EFI/redhat (or /boot/efi/EFI/redhat), so I easily can end up with two or three different set of config files and binaries with no control which one is used.

The vanilla, proper location is either in /grub/grub.cfg (or /boot/efi/grub/grub.cfg - that's OLD and deprecated as of grub version 2.02-beta3 if I recall correctly) and or /EFI/BOOT/grub.cfg (or /boot/efi/EFI/BOOT/grub.cfg)

My question is how do I force grub-install to use the last location? it somehow hardcodes the path into the grubx64.efi binary. If I move hte config file to proper location grub ends up in CLI. When asked to execute load_env or configfile it expects them to be in /EFI/ubuntu, and I have to specify path explicitly.

---

### Post by Dennis N on 2022-08-24
> /EFI/ubuntu (or /boot/efi/EFI/ubuntu from OS' perspective) is the one I am interested in - the one that is actually used by grub during the boot process to draw the menu on screen and populate said menu with entires of OSes to boot.

Well, you're wrong about that. the grub menu is generated (drawn) using  /boot/grub/grub.cfg

---

### Post by vatharian on 2022-08-24
Then why when I delete /boot partition (and every single filesystem containing /boot or other Linux OS) and leave just the ESP partition it still works?

---

### Post by dragonfly41 on 2022-08-24
Sidestepping the main argument, if your tools are customising access perhaps add rEFInd to the mix? Works fine for my dual boot. Configuration, themes etc.,are in refind.conf.

---

### Post by yancek on 2022-08-24
>  It appears that grub installed from Ubuntu, searches for grub.cfg for some reason in /EFI/ubuntu/, instead of /EFI/BOOT. T

That (EFI/ubuntu) is the standard location for an EFI install of Ubuntu.  If you look at the grub.cfg file there you will see it is a simple 3 line file pointing to the partition on which Ubuntu's filesystem is actually installed.  When running update-grub, it is the grub.cfg file on the filesystem partition which is modified.  The grub.cfg in EFI/ubuntu isn't changed unless there is a reinstall or a user modifies it.  WD.  The codse below is the entire grub.cfg file on one of my laptops for grub.cfg on  the EFI partition.  Yours should be similar.

Have you modified this file?  Why do you use a separate boot partition?  Are you using LVM?  Do you use separate boot partition on each partition?  

>  problem is the /ubuntu/ part of the path. If I install grub from redhat  it ends up in /EFI/redhat (or /boot/efi/EFI/redhat), so I easily can end  up with two or three different set of config files and binaries with no  control which one is used.

Why would you not have control over them?  You can easily change which is booting, red hat, ubuntu or whatever in the BIOS firmware or with efibootmgr.

>  My question is how do I force grub-install to use the last location? 

If you want the path  to be " /boot/efi/EFI/BOOT/grub.cfg)" copy the files from the original default location.

>  Then why when I delete /boot partition (and every single filesystem containing /boot or other Linux OS) 

I don't understand what you are saying.  If you delete the filesystem partition there is nothing to boot, no OS so what works?

---

### Post by oldfred on 2022-08-24
In the beginning I tried changing the distributor in grub's config file. That used to create a unique entry in UEFI, using that description.
Very old versions of grub added new ESP entry like /EFI/kubuntu, but no grub.cfg in /EFI/kubuntu.
They would set efi_distributor variable to be same as grub_distributor, but only search for grub in /EFI/ubuntu.
Then somewhat newer versions of grub added a grub.cfg in /EFI/kubuntu, but still only used the grub.cfg in /EFI/ubuntu.
One version, I think Debian, embedded the entire grub.cfg in grubx64.efi. 

I still try with every version of Ubuntu and yes, something is hardcoded. And I think it is only in Ubuntu's version of grub.

Old/related.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561712](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561712)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783)
> All of these are grubx64.efi with different grub.cfg with  different configfile entries for different UUIDs.
/efi/BOOT/bootx64.efi
/efi/trusty/grubx64.efi
 /efi/ubuntu/grubx64.efi
 /efi/vivid/grubx64.efi
 But they all use the one grub.cfg in /efi/ubuntu.
                                       [                ]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783/+index#")

---

### Post by yancek on 2022-08-24
I think it would probably take a lot of knowledge of how Grub works and the Ubuntu Grub to do this during an install.  I saw a thread on another forum where a member did something similar using a command like the one below.  Need to create the mount point and mount them before using them.  I haven't tried this so I don't know that it will work.

```
 sudo grub-install --boot-directory=/boot/custom and --efi-directory=/efi/custom
 
```

---

### Post by pbear42 on 2022-08-24
> **vatharian said:**
> Then why when I delete /boot partition (and every single filesystem containing /boot or other Linux OS) and leave just the ESP partition it still works?

How are we supposed to know, when you insist on playing hide-the-ball on what tools you're using to boot?

Fact remains, it's the grub.cfg file in /boot/grub which is used to compose the boot menu.  Also, that it's the file generated by update-grub.  No experience with Red Hat, but same thing in Fedora, except it's /boot/grub2.

As for the original question, don't know, but good chance the destination is specified in one of the scripts in /etc/grub.d.  Might be coded into one of the Grub packages, though, and not easily modified by the user.

---

