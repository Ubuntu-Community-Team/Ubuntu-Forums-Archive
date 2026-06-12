---
title: "Grub menu not working with HDMI"
date: 2022-03-18
forum: General Help
---

### Post by us-palermo on 2022-03-18
Just upgraded my pc from a Lenovo t400 to a Asrock Deskmini X300 Ryzen 5 3400G

When I boot into grub my screen tells me Asus "Out of Range" I wait 15 seconds later and I can boot into xubuntu this is with a HDMI connection cable 

when I boot into grub with a vga cable I am able to select either my xubuntu os or my windows 10 os with no issues and boot into both?

how do I fix this issue?

---

### Post by MAFoElffen on 2022-03-20
At the Grub Menu, using the VGA cable, press <C> to go to Grub command-line... 
```

videoinfo

```
Take a picture of the output to that command with a camera, or write down what the preferred resolution is of the display. 

Next, type eixt to get back to your Grub Menu. Boot normally.  Open a graphical terminal, and type
```

xrandr -q

```
This should be your display resolutions, in relation to your graphics GPU...

Grub can only display what it sees from your Display, and is capable as seen through your BIOS... (at that stage and level). Higher graphics are seen in later stages of the boot process. So sometimes it needs help. 

Edit /etc/default/grub to set the at that resolution. Run update-grub to update the settings.

---

