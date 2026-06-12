---
title: "Theme on Bootable USB"
date: 2020-07-07
forum: General Help
---

### Post by Disabled20241022 on 2020-07-07
I have downloaded a theme called Vimix and i have this in my grub.cfg
[COLOR=#000000]theme=/boot/grub/themes/Vimix/theme.txt
All the files of grub2 are on my external usb drive (ssd), i have it booting on startup.
What i would like to know is how do i install a theme on a bootable usb where linux is not installed?
To be clear, i am not trying to change my theme on my computer, i would like to change the grub2 bootloader theme on my usb drive. so standard commands to install doe not apply.
[/COLOR]
Please explain everything because i am a newbie.

---

### Post by Disabled20241022 on 2020-07-13
Anyone?

---

### Post by wildmanne39 on 2020-07-13
Hello ayudha, you can bump your thread once every twelve hours to keep your thread in view of the volunteers here, if you do not bump it your thread falls out of view and probably will not get seen.

---

### Post by C.S.Cameron on 2020-07-14
It depends on how your USB was made. If made using UNetbootin and similar syslinux type tools, editing syslinux.cfg or txt.cfg similar to the way you edited grub.cfg on your main computer grub.cfg should work. if you are using a mkusb persistent install, edit /boot/grub/grub.cfg on partition 2, usbboot. If you are using a full install to USB do it exactly the same as your main drive. If those methods don't work let us know the tool you used to make the USB.

---

### Post by Disabled20241022 on 2020-07-14
The USB (which actually is a SDD drive, external) is already made, i made it by installing grub2 on it by hand, no software used. i have it working but i just can't seen to get the theme working.
i have boot/grub/themes/theme.txt and all the other files in the themes folder.
The grub.cfg is also in the grub folder and the only thing that is in there is one line that sets the theme. ```
[COLOR=#000000][FONT=&amp]theme=/boot/grub/themes/theme.txt i also used set theme)
[/FONT][/COLOR]
```
I have never changed a theme in linux so i don't know how to do it, been at it for months now. i recon that it is different for a USB is it not? since linux is not installed there. (new to linux here)

---

### Post by Disabled20241022 on 2020-07-16
I also tried to put the folder in different places and i have then changed the folder structure in grub.cfg but nothing seems to work.

---

### Post by Disabled20241022 on 2020-07-17
If i install the theme it will install it on my linux install partition and not on my usb drive

---

### Post by Frogs Hair on 2020-07-17
Is this a[ persistent]("https://www.fosslinux.com/24376/how-to-create-a-ubuntu-persistent-storage-live-usb-drive.htm#:~:text=How%20to%20create%20a%20Ubuntu%20Persistent%20Storage%20Live,install%20the%20mkusb%20package.%20...%20More%20items...%20") USB ?

---

### Post by Disabled20241022 on 2020-07-17
i dunno what that is. but what i can tell you is that it is just a data drive, SSD (so not really a usb) it is connected externally. i store data on it and use live linux iso's to boot on system restart and install linux. there is no actual linux installed on it.
So its just a SSD drive with grub2 insalled on it. i have linux installed on a other harddrive which is in my laptop. + windows. but i dont want to change the theme on this one.

---

### Post by Frogs Hair on 2020-07-18
A live disk/usb drive won't allow you to save changes including themes. I tried the same grub theme on my installation some days ago and the install script ran, but the theme never changed. I have not looked into it further.

---

### Post by Disabled20241022 on 2020-07-18
It's not a live linux usb tho.
its just grub2 that is booted on startup. grub from the usb (external ssd card/drive) so that i can run different programs.
this theme i try to change.

prehaps you can tell me where they normally should be placed, in what directory's and what code is inside the grub.cfg

---

### Post by Frogs Hair on 2020-07-18
Vimix is the theme I tried and i think the best info is on the developers page. The terminal closed before i could see what was going on. I know the installer found the partitions and updated grub yet no theme was installed.   

[https://github.com/vinceliuice/grub2-themes](https://github.com/vinceliuice/grub2-themes)

---

### Post by Disabled20241022 on 2020-07-18
yes that is on linux (terminal) this needs to be installed on a USB where there is no linux just grub2. i don't understand how to do that, thinking that is impossible and that it should be done manually instead.

---

### Post by Frogs Hair on 2020-07-18
The theme folder and .cfg are in file system usr/share/grub/, but there are multiple grub folders in other locations in the file system.

---

### Post by Disabled20241022 on 2020-07-19
Finally, after months of working on this i finally cracked the code :)
this is what i needed to add.

```
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
```

For me only the first 2 are unclear what they do exactly. term?
also, the export theme was needed for submenu's so it seemed.

Edit: ok, on second thought it isn't quite finished.
When going to [https://github.com/vinceliuice/grub2-themes/blob/master/screenshots/grub-theme-slaze.jpg](https://github.com/vinceliuice/grub2-themes/blob/master/screenshots/grub-theme-slaze.jpg) the background is much sleeker. the 'colors' on the left fade into each other really nicely and on my own setup it is not so nice.
And for the lettertype, is different and mine is much smaller, more margins or is it padding.
even the icons seem different or just smaller.

Does anyone know what is wrong with the lettertype?
This is from my theme
```
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

I have 1600x900 screen and the loadfont /boot/grub/themes/Slaze/dejavu_sans_16.pf2 is to small for my screen and 
loadfont /boot/grub/themes/Slaze/dejavu_sans_24.pf2 is to big which distorts the letters a little. **How do i get these in between, say 18 or 20?**

---

