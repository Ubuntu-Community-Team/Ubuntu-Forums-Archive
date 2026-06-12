---
title: "XP, Vista, Ubuntu all on GRUB?(no windows boot loader)"
date: 2006-12-05
forum: General Help
---

### Post by cortk on 2006-12-05
I have GRUB working but it is currently going like this:
GRUB
->Ubuntu normal
->Ubuntu safe mode
->Ubuntu memory test
->Windows Boot Loader
--->Windows XP
--->Windows Vista


How do I configure grub so it goes something like this:
GRUB
->Ubuntu normal
->Ubuntu safe mode
->Ubuntu memory test
->Windows XP
->Windows Vista


Or this:
GRUB
->Ubuntu normal
->Ubuntu safe mode
->Ubuntu memory test
->Windows XP
->Windows Boot Loader
--->Windows Vista


There's an image here with the boot folder... bootloader... i think, directory:
[http://www.vistabootpro.org/images/screenies/VBP3Settings.png](http://www.vistabootpro.org/images/screenies/VBP3Settings.png)

Just that 5728 up would be my version and the XP's boot is correct... ntldr

---

### Post by Forceflow on 2006-12-05
Try editing menu.lst. There is a bulk message "other operating systems". You could try removing that. (Beware: I don't know whether or not this will work - I'm new to linux, but I recently had to edit that file.)

---

### Post by steve.horsley on 2006-12-05
See this howto. It contains examples of loading windows (use chainloader) and also of hiding partitions from windows.

---

### Post by cortk on 2006-12-06
"this" howto? Which howto?

---

### Post by steve.horsley on 2006-12-06
> **cortk said:**
> "this" howto? Which howto?

WTF? Where did that go???
Sorry. Must be finger trouble.

[http://tldp.org/HOWTO/Multiboot-with-GRUB.html](http://tldp.org/HOWTO/Multiboot-with-GRUB.html)
[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

These two look much the same to me except one is single-page.

---

