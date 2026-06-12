---
title: "grub disappear and xp default"
date: 2008-07-09
forum: General Help
---

### Post by hammerofthegods on 2008-07-09
Hello. I currently have a dual boot of both xp and ubuntu. I am trying to make it so that grub doesnt show up while booting due to other people using the same computer that only want to use xp. Is there any way i could make grub disappear and by default have it load windows xp? I am completely new to ubuntu and if there is a way could you please explain it as simple as possible? Thank you in advance.

---

### Post by iaculallad on 2008-07-09
You could try editing your /boot/grub/menu.lst file:

```
gksudo gedit /boot/grub/menu.lst
```

And, if you want to make windoze xp your default boot OS, change the **default** setting in your menu.lst to point to xp.

i.e:

> default 0

would be my option if I wanted to boot using Ubuntu 7.10, kernel2.6.22-15-generic. (Using the sample menu.lst boot option below)

and

> default 1

If I wanted to boot using title Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)

And so forth...

```

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=6d422661-145e-4c07-9cbb-8428c17a2b1f ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-15-generic
#quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=6d422661-145e-4c07-9cbb-8428c17a2b1f ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

```

EDIT: Too hide the menu, uncomment the **#hiddenmenu** setting.

---

### Post by mikewhatever on 2008-07-09
To hide grub, locate the following section and uncomment the last line in it. Uncomment means removing the hash sign #.
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Setting timeout to 0 is not recommended, since you'd not be able to choose Ubuntu, if XP is set as default. 3-5 sec is a more reasonable value. It would give you time to hit ESQ key to see GRUB menu and choose Ubuntu to boot.

To set XP as default OS to boot, count the word 'title' starting with Ubuntu's kernel. Once you get to XP, subtract 1 and change the value in the following section:
> default   0

If there is only one linux kernel, you should get 5-1=4, so it would be default   4.

---

### Post by ettercap on 2008-07-09
download startup manager..

sudo apt-get install startupmanager


then select  ur default os

---

### Post by hammerofthegods on 2008-07-10
> **ettercap said:**
> download startup manager..

sudo apt-get install startupmanager


then select  ur default os

Thank you lots man! It worked :)

---

