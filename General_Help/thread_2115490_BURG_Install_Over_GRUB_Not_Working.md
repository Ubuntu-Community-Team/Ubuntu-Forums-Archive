---
title: "BURG Install Over GRUB Not Working"
date: 2013-02-13
forum: General Help
---

### Post by diannnicles on 2013-02-13
Hi, new to the forum and fairly new to Ubuntu here. I have Ubuntu 12.10 installed alongside Windows 8 on a GPT disk. I installed BURG because I like having everything look nice. But whenever I boot up the computer, grub2 loads instead of burg. 

Here's what I have done: 

```
sudo add-apt-repository ppa:n-muench/burg
sudo apt-get update 
sudo apt-get install burg burg-themes
sudo burg-install /dev/sda --force
```

I used --force because this

```
/usr/sbin/burg-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
```

came up. 

Attached is my hard drive setup.

---

### Post by oldfred on 2013-02-13
Burg has not been maintained for a while, it looks like last upload was Oct 2010.

Grub2 has changed a lot since then with sub-menus, but it still is only for BIOS/MBR boot not UEFI and you have UEFI.

Also gpt partitions do not have the embedding area just after MBR, so you cannot just install a BIOS boot loader without a bios_grub. I do use gpt with BIOS, but have to have bios_grub partition.

I would not even think about burg with UEFI.

---

