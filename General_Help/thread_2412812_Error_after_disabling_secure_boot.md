---
title: "Error after disabling secure boot"
date: 2019-02-17
forum: General Help
---

### Post by toad007toad007 on 2019-02-17
So I disabled secure boot in order to get support for Intel's Platform Trust Technology with the latest mainline kernel (4.20.10). I am able to boot into the new kernel and everything seems to work fine except for GSConnect. However upon booting, just after grub loads I get the following error....

error: file '/grub/x86_64-efi/vbe.mod not found
Press and key to continue

In stays like for like 2-3 seconds then boots fine. Keep in mind secure boot WAS enabled when I first installed 18.04. I just turned it off to upgrade the kernel. Fixed one problem and got another I guess...lol. Any help is appreciated!!!

EDIT: I tried running boot-repair and it did nothing,but here is my paste bin link...
[http://paste.ubuntu.com.p/wGfXSS6B3z](http://paste.ubuntu.com.p/wGfXSS6B3z)

---

### Post by toad007toad007 on 2019-02-17
Figured it out. Edited my grub config file to comment the GRUB_VIDEO_BACKEND="vbe" line...all works fine now.

---

