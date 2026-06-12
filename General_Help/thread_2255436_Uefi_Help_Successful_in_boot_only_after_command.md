---
title: "Uefi Help Successful in boot only after command"
date: 2014-12-05
forum: General Help
---

### Post by vmehta1 on 2014-12-05
Basically my only OS installed is ubuntu via uefi mode and it works but on each boot I have to input the following configfile (hd0,2)/boot/grub/grub.cfg is there a way for it to work without having to do this each time I tried manually adding the grub.cfg in the boot folder it does not seem to do anything thanks in advnace! ;)

---

### Post by ajgreeny on 2014-12-05
Did you follow all the information in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which is very detailed for both single boot and dual boot situations.  Have a good read through that and then come back again if it gets you nowhere.

It may also help if you follow all the info in Boot-Repair in my signature, and if needed post the pastebin link to show us the report it makes.

---

### Post by oldfred on 2014-12-05
You should have a grub.cfg with the config file entry in /boot/efi/EFI/ubuntu.

Mine looks like this:

```
search.fs_uuid  45de38c8-6748-4634-b207-628d9aa8b42b root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

The UUID or drive hd0,gpt3 is the drive, partition where my /boot in my Ubuntu is. Mine is in / (root) not a separate partition. And it just is telling system where to find the grub.cfg with all the boot stanzas.

---

