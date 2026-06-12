---
title: "The bootloader could not be installed"
date: 2022-12-30
forum: General Help
---

### Post by speedruntrainer on 2022-12-30
Hello everyone.

I decided to install Lubuntu 22.04.1 next to Windows 10. So I created a 25GB partition inside Windows to install it on, created a bootable USB with Rufus and tried to install Lubuntu.
So I chose the option to replace the partition in the installer so I could choose the partition that I created in Windows.
So I let it install and about 3/4 done, I get this error message:

The bootloader could not be installed. The installation command
<pre>grub-install --target=x86_x64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --force</pre> returned code 1.

What do I need to do to make this work and what's wrong? I get no further information than this.
Hope someone can help with this.


It's solved. I just had to choose the USB without UEFI and it worked flawlessly. Now I don't have sound from HDMI though :/
Thanks in advace.

---

