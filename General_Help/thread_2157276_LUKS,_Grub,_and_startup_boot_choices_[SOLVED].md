---
title: "LUKS, Grub, and startup boot choices [SOLVED]"
date: 2013-06-24
forum: General Help
---

### Post by ofnuts on 2013-06-24
I am running Kubuntu 12.10 on a LUKS-encrypted disk. The whole thing is working fine(*), but... on my previous PC, where I had a an unencrypted 10.04, I would get the Grub menu on startup, allowing me to choose a boot image or to run memtest. But I don't get this menu when I boot 12.10, it goes direcrtly to the LUKS passphrase. I did have a glimpse of the menu a couple of times... without knowing what made it show up (and didn't have the time to make a choice).  

The grub.cfg is indeed listing 3 images and memtest86. Is there something special to do to activate the menu? Or some key combo to get the menu when booting?

(*) one caveat though: there isn't that much space on /boot, so you can only get 3 or 4 kernels images before it fills up. And the automatic installations of new images don't clean up the old ones. I don't know what happens when the disk fills up while a new image is configured.... it may not be pretty.

---

### Post by Cheesemill on 2013-06-24
Try increasing the grub timeout so you can see the menu. Open the file for editing by doing...
```
kdesudo kate /etc/default/grub
```
and change the GRUB_TIMEOUT value to something larger.
Then update grub by running...
```
sudo update-grub
```

The fact that you are using a LUKS encrypted disk makes no difference at all. Grub acts just as it would in a normal installation.

---

### Post by ofnuts on 2013-06-25
The timeout is already set to 10 but googling for GRUB_TIMEOUT got me the answer. Ubuntu hides this menu unless you have another opsys installed (my previous system could also boot Windows... until I put that partition to better use). It seems holding the shift key while booting makes the menu appear, so I'll try this at next reboot. This would be sufficient. Thx for the heads up.

---

