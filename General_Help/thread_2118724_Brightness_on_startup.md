---
title: "Brightness on startup"
date: 2013-02-22
forum: General Help
---

### Post by sim085 on 2013-02-22
Hello,

Unfortunately I do not have a working battery on this laptop (it is always plugged). The problem I have is that on startup my screen Brightness is always set to the minimum possible. 

Each time I have to go to “System Settings > Brightness and Lock” and have to set the Brightness level again. I do not have the “Dim screen to save power”.

Is there a way so that Ubuntu will not change my Brightness settings on startup?

---

### Post by albandy on 2013-02-22
try adding this to your kernel boot parameters: acpi_backlight=vendor

---

### Post by sim085 on 2013-02-22
> **albandy said:**
> try adding this to your kernel boot parameters: acpi_backlight=vendor

Hi, thanks for your reply. However I am quite new to Ubuntu and linux in general. From where can I edit kernel boot parameters?

---

### Post by albandy on 2013-02-22
> **sim085 said:**
> Hi, thanks for your reply. However I am quite new to Ubuntu and linux in general. From where can I edit kernel boot parameters?

Ok, lets do it:

0.- Open a terminal
1.- edit /etc/default/grub: sudo gedit /etc/default/grub

2.- Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

3.- save the file
4.- type: sudo update-grub
5. reboot

---

### Post by sim085 on 2013-02-22
Thank you, will try it when I am back home.

---

### Post by rcayea on 2013-02-22
Sorry to the original poster for jumping in on his post, however, I just tried the suggested fix as I have the same problem on a new ASUS laptop and it didn't work for me. Hopefully it works for you.

---

