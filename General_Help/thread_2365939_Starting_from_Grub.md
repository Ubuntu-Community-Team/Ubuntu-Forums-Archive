---
title: "Starting from Grub"
date: 2017-07-12
forum: General Help
---

### Post by rasmus91 on 2017-07-12
Hi there.

I was using my 64 bit laptop today, when I rebooted it, and I was brought up short by the grub 2 CLI (not the rescue, the full client, mind you). I identified my  partitions quickly, but I can't get it to start. It's an UEFI install, with custom partitioning. From grub it's as follows:

```
(hd0,gpt1)
``` contains the root partition. All of the root structure, as far as I can tell, however lies in 
```
(hd0,gpt1)/@/
``` so if I wish to list the content of the boot folder for an example, I have to do: 
```
ls (hd0,gpt1)/@/boot
```

[see list command results]("https://goo.gl/photos/KLXFrLXNf1r5fxaq7")

```
(hd0,gpt2)
``` contains /home and
```
(hd0,gpt3)
```  contains /opt

Hd1 has a fat partition containing the EFI stuff.

How do I go about booting this?

---

