---
title: "Burg install on non-standard partition"
date: 2013-05-15
forum: General Help
---

### Post by xenocrates on 2013-05-15
Hi everybody :)

I have a little problem. I bought this new ASUS N56VJ laptop, which comes with Windows 8 64-bit pre-installed. I decided to dual-boot with Ubuntu 13.04 and just use the empty partion, which was already there, for Ubuntu. I chose to install with EFI-support. The thing is, that I think grub2 was installed on a partion called /dev/sda1 (it's a FAT32 partion mounted to /boot/efi - ubuntu is on /dev/sda5 and windows is on /dev/sda4). During the install, I got a warning, saying that grub was installed far from the beginning of the hard disk and that it might cause problems during boot. So far no boot problems have occured, but now I want to use Burg instead of grub2. When I try to run the command
```
sudo burg-install "hd0"
``` or ```
sudo burg-install /dev/sda
``` I get the following output:
```

/usr/sbin/burg-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.

```
If I try ```
sudo burg-install /dev/sda1
``` (or /dev/sda5) I get this message
```

/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.

```

My question now, is: How do I install Burg? I have tried searching the web, but so far I have not found a solution to my problem. I hope any of you guys can help me. If you need more info, just tell me how to fetch it, and I will post it right away.

Thanks in advance :)

---

### Post by xenocrates on 2013-06-01
Does nobody have an idea for me? I have tried using grub2 with gfxmenu enabled, but it's infinitely more difficult to create themes for grub2 :(

---

