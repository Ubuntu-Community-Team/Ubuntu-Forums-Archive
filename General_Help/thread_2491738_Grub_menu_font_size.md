---
title: "Grub menu font size"
date: 2023-10-19
forum: General Help
---

### Post by Disabled20241022 on 2023-10-19
I want to know how i can change my resolution or the font size of my grub menu.
However this is not your avarage installation of grub, it is not installed on a harddrive it is on a live USB, it has no grub on it as a normal linux system does, there is actually not even a terminal that is workable because it needs to be changed manually in the cfg file.
I am using this to install linux, on a reboot i launch the USB and i get the grub menu from the USB itself, where no linux is installed on it just this bootable grub and it is minimal in files.
This is what i can adjust but somehow gfxmode or fontsize doesnt work, what to do? the menu is so tiny!

[B]/media/me/UEFI/boot/grub/grub.cfg
[/B]```
insmod gfxtermterminal_output gfxterm
loadfont /boot/grub/themes/Slaze/dejavu_sans_12.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_14.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_16.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_24.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_32.pf2
loadfont /boot/grub/themes/Slaze/dejavu_sans_48.pf2
loadfont /boot/grub/themes/Slaze/terminus-12.pf2
loadfont /boot/grub/themes/Slaze/terminus-14.pf2
loadfont /boot/grub/themes/Slaze/terminus-16.pf2
loadfont /boot/grub/themes/Slaze/terminus-18.pf2
insmod jpeg
insmod png
theme=/boot/grub/themes/Slaze/theme.txt
export theme


default=0


menuentry "Start PopOS" --class pop-os {
    search --fs-uuid B7CB-0780 --set=root
    chainloader /EFI/BOOT/BOOTX64.EFI
}
menuentry "Installeer PopOS 22.04" --class pop-os {
    search --fs-uuid 437c782d-5a06-47a5-a7b6-b6ddb99b4559 --set=root
    linux /casper_pop-os_22.04_amd64_intel_debug_88/vmlinuz.efi boot=casper quiet splash
    initrd /casper_pop-os_22.04_amd64_intel_debug_88/initrd.gz
}
menuentry " " {
  true
}
menuentry "Opnieuw opstarten" --class restart {
    reboot
}
menuentry "Afsluiten" --class shutdown {
    halt
}
menuentry "Opstartopties" --class kbd {
    fwsetup
}
```

And i have this also:
[B]/media/me/UEFI/boot/grub/themes/Slaze/theme.txt
[/B]```
# GRUB2 gfxmenu Linux theme# Designed for any resolution


# Global Property
title-text: ""
desktop-image: "background.jpg"
desktop-color: "#000000"
terminal-font: "Terminus Regular 14"
terminal-box: "terminal_box_*.png"
terminal-left: "0"
terminal-top: "0"
terminal-width: "100%"
terminal-height: "100%"
terminal-border: "0"


# Show the boot menu
+ boot_menu {
  left = 30%
  top = 30%
  width = 45%
  height = 60%
  item_font = "Terminus Regular 18"
  item_color = "#cccccc"
  selected_item_color = "#ffffff"
  icon_width = 42
  icon_height = 42
  item_icon_space = 20
  item_height = 41
  item_padding = 4
  item_spacing = 7
  selected_item_pixmap_style = "select_*.png"
}


# Show a countdown message using the label component
+ label {
  top = 82%
  left = 32%
  width = 30%
  align = "center"
  id = "__timeout__"
  text = "Booting in %d seconds"
  color = "#cccccc"
  font = "DejaVu Sans Regular 16"
}
```

Thanks for the help guys! And girls!

---

### Post by MAFoElffen on 2023-10-19
Since manually... Have you tried setting your 'gfxmode' to set the resolution manually? Default is usually set to
```

set gfxmode=auto

```
If you did something in the form of
```

set gfxmode=640x480

```
... to override that.

---

### Post by Disabled20241022 on 2023-10-19
Yes i have tried that but it doesnt do anything.

---

### Post by Disabled20241022 on 2023-11-13
Anyone?

---

### Post by ajgreeny on 2023-11-13
Where is the /etc/default/grub file that you normally need to edit to make these changes to the menu resolution sited?
Is it on the live USB or on your full install hard disk?

I have never used grub in the manner you're asking about so I wonder if you edited the wrong file of those two, if there actually are two of them in existence.

---

### Post by Disabled20241022 on 2023-11-13
Everything being used is on this live USB.
there is no etc/ directory there.
there is a other location which has the grub.cfg file but it is just pointing to (as seen abovE) **/media/me/UEFI/boot/grub/grub.cfg**

---

### Post by dragonfly41 on 2023-11-13
Another thought  .. if you try *adding* rEFInd you can create custom themes. I use the rEFInd GUI and theme changes are made in rEFInd.conf.

[https://rodsbooks.com/refind/themes.html](https://rodsbooks.com/refind/themes.html)

---

### Post by MAFoElffen on 2023-11-13
<<Not an Ubuntu Support Thread, but is just Grub2 theming...>>

Dang. Post this
```

ls /boot/grub/fonts
find / -name *.ttf 2>/dev/null

```
The first command will show you which fonts are in your grub directory. The second, on an Ubuntu system, will show you were all the /ttf font files are on that system... You have everything in a themes directory right?

If you needed larger fonts, then this command will convert it to grub format of a specified size, and put into the grub font directory:
```

sudo grub-mkfont -s 18 -o /boot/grub/fonts/DejuVuSansMono_24.pf2 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf

If you did have Ubuntu, and had a /etc/default/grub file, then you wold edit it and add this line
[code]
GRUB_FONT=/boot/grub/fonts/DejaVuSansMono_24.pf2

```
But since it sounds like you do not have Ubuntu, nor a /etc/default/grub file, because your USB disk does not have Ubuntu, but just Grub2 (???) and it has a static grub.cfg file. Then you would change your lines that use loadfont, that it it doesn't have the font in the assumed, grub/font directory, then you have to specify the absolute path to the filename. Which "is there" and "is okay".

I do not see anything wrong with either file. Everything looks good.

Possibly... I would check from Grub CLI "lsfonts" to verify that the fonts loaded are the specified names in the theme file.

---

### Post by Disabled20241022 on 2023-11-13
Could you help me out, im a bit of a newbie to all of this. what do i do?

---

### Post by MAFoElffen on 2023-11-13
At the Grub Menu, type the <C> key, which will drop you down to a Grub prompt.
```

GRUB >

```
enter
```

lsfonts

```
Take a picture to the fonts it says is there... For example, look at the attached screenshot

---

### Post by Disabled20241022 on 2023-11-15
Even the grub terminal is very tiny but i got this as a result.

---

### Post by Disabled20241022 on 2023-11-24
anyone?

---

### Post by dragonfly41 on 2023-11-24
Workaround.

I have no idea why your main core grub doesn't work. But as I posted in #7 , I have rEFInd installed and I have researched dabbling with themes.

[https://rodsbooks.com/refind/themes.html](https://rodsbooks.com/refind/themes.html)

and /usr/share/refind/fonts

If you explore Synaptic you might find that refind is in repo to try out in your USB. But this is a huge guess.  Fonts characters are in *.png files.

For example ubuntu-mono-12 up to ubuntu-mono-28.

themes are in refind.conf

sudo locate refind.conf

[FONT=monospace][COLOR=#000000]/usr/share/refind/refind/refind.conf-sample[/COLOR]
[/FONT]

---

