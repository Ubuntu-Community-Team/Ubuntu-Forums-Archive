---
title: "MMIO write FAULT after boot"
date: 2021-12-26
forum: General Help
---

### Post by atreidespaul on 2021-12-26
I see these errors when I turn on the laptop. The machine is working fine, but I have no idea what to do with these errors. Help me please
[[img]https://i.ibb.co/tDmLMrD/AH8-UBDOqpkk-1.jpg[/img]](https://ibb.co/hV7YRzV)


My laptop
[[IMG]https://i.ibb.co/rfSYNrr/il-Ny7-D6lv-Pg.jpg[/IMG]]("https://ibb.co/WpwZjJJ")
[IMG]https://ibb.co/5syP636[/IMG]
[IMG]https://ibb.co/5syP636[/IMG]

---

### Post by ajgreeny on 2021-12-26
I suspect that you need a proprietary driver for the graphic card that you are using but lets see the info first.

To show more information about the hardware you have please show us the output of terminal command ```
inxi -Fzx
```
Though you can also go to the Additional Drivers utility from the menu or Applications, depending on your *Buntu version.  This should show you any drivers recommended for that GeForce card, though that is, I think an old card.

---

### Post by atreidespaul on 2021-12-26
> **ajgreeny said:**
> I suspect that you need a proprietary driver for the graphic card that you are using but lets see the info first.

To show more information about the hardware you have please show us the output of terminal command ```
inxi -Fzx
```
Though you can also go to the Additional Drivers utility from the menu or Applications, depending on your *Buntu version.  This should show you any drivers recommended for that GeForce card, though that is, I think an old card.

Thank you for answer. My graphic card is NVIDIA Geforce GT 620M. The most interesting thing is that the list of drivers is empty.

[[img]https://i.ibb.co/Z605Zjn/screen.jpg[/img]](https://ibb.co/XZq1wQh)
[[img]https://i.ibb.co/pZZvbx2/screen1.jpg[/img]](https://ibb.co/3WWy471)
[[img]https://i.ibb.co/513fhBX/screen2.jpg[/img]](https://ibb.co/0nLdyhp)

---

### Post by ajgreeny on 2021-12-27
OK.
Perhaps that's because there are no proprietary drivers any more for that old card, meaning that the nouveau driver is the only one you can use.
If the OS runs well just ignore those warnings and accept things as they are.

In future please do not add large images to your posts but use the attachment facility from the Reply to Thread window, the paperclip icon in the toolbar, then point to the image on your hard disk.

---

### Post by atreidespaul on 2021-12-27
Problem is solved! I manage to install nvidia driver by folowing commands:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
ubuntu-drivers devices
sudo apt install nvidia-driver-495
```

Thanks, [[COLOR=#C61919]ajgreeny[/COLOR]]("https://ubuntuforums.org/member.php?u=27747")[COLOR=#000000] [/COLOR]

---

