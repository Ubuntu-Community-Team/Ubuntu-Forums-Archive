---
title: "Which Grub?"
date: 2018-10-10
forum: General Help
---

### Post by hakelm on 2018-10-10
I have a multi boot system. Today I installed a 3rd Ubuntu but the resulting grub configuration doesn't seem to work properly. My default Ubuntu won't boot. 
Now I want to reconfigure grub and I have 3 different /boot/grub/grub.cfg. 
Which one should I edit and use?
How do I know which grub configuration is used when booting?
H

---

### Post by Impavidus on 2018-10-10
Typically, the system in control of grub is the last system installed or the last system on which an update to grub was installed. That should be the system booted with the top entry in the grub menu. You can put a different system in control of grub if you boot that system, then use it to reinstall grub.

Do you use bios or uefi?

Edit: [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) may also help. Create the summary. It should tell you where grub looks for its config files.

---

### Post by hakelm on 2018-10-10
Thanks!
[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") did the trick.
H

---

### Post by oldfred on 2018-10-10
I use UEFI now, and fully back up my ESP - efi system partition. 
I have multiple installs and last install overwrites /EFI/ubuntu folder. But only real change is the configfile entry in /EFI/ubuntu/grub.cfg on which system to boot.

If one of your other installs does a full grub reinstall, it may then overwrite your ESP again. 

Or if BIOS most grub updates will change the entry in the MBR to that version. With BIOS there is a grub setting on where to install/reinstall grub and you can blank that out. Have not found similar setting for UEFI as Ubuntu's grub only wants to install  to first drive's ESP.

---

