---
title: "GfxBoot image missing"
date: 2006-12-10
forum: General Help
---

### Post by hadiriazi on 2006-12-10
Hi all;

I have followed this [HowTo]("http://ubuntuforums.org/showthread.php?t=208855&page=2&highlight=gfxboot"), and now when I boot the system I get:
**graphics file "/boot/grub/message.ubugrey" missing, Press any ...**

I did this:

```
sudo apt-get remove grub
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
sudo cp message.ubugrey /boot/grub/
sudo gedit /boot/grub/menu.lst
and make it use gfxboot
gfxmenu /boot/grub/message.ubugrey

sudo grub
grub> find /boot/grub/stage1

```
at the last command I get the command not found output, so I tried doing this:

```
grub-install /dev/**sda**
```
what is it that I'm doing wrong here? please help.

---

### Post by se0siris on 2006-12-29
Do you have a seperate boot partition?

It's a problem I've just ran in to. If your /boot is on its own partition, try changing
```
gfxmenu /boot/grub/message.ubugrey
```
to just
```
gfxmenu /grub/message.ubugrey
```

---

