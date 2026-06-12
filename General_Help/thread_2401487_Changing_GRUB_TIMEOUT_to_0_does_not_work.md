---
title: "Changing GRUB_TIMEOUT to 0 does not work"
date: 2018-09-18
forum: General Help
---

### Post by gorbov12 on 2018-09-18
Hello,

I am trying to get the bootloader to boot directly into Ubuntu without waiting 10 seconds before doing so. I've looked around for an answer and followed the steps carefully, but the bootloader continues to appear but this time with a 7 second delay. Here's a screenshot to show you that I've indeed set GRUB_TIMEOUT to 0:

[https://imgur.com/xfzHyXV](https://imgur.com/xfzHyXV)

Any tips on how to fix this? Thanks

---

### Post by plucky on 2018-09-19
> **gorbov12 said:**
> Hello,

I am trying to get the bootloader to boot directly into Ubuntu without waiting 10 seconds before doing so. I've looked around for an answer and followed the steps carefully, but the bootloader continues to appear but this time with a 7 second delay. Here's a screenshot to show you that I've indeed set GRUB_TIMEOUT to 0:

[https://imgur.com/xfzHyXV](https://imgur.com/xfzHyXV)

Any tips on how to fix this? Thanks

Have you run ```
sudo update-grub
```?

---

### Post by ajgreeny on 2018-09-19
Let's see the full content of **/etc/default/grub** to be sure you have done all that is needed for what you want.

Is this a single boot system or do you have more than one OS available from grub?

---

