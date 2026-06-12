---
title: "Change Font Colour - Ububntu 22.04"
date: 2022-09-05
forum: General Help
---

### Post by Quarkrad on 2022-09-05
I normally change my grub font colour and for some time have done this via Grub Customizer.  However, since 22.04 I have not been able to do this.  This is my /etc/default/grub output:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#grub background
GRUB_BACKGROUND="/home/dad/Documents/icons/grub.png"

export GRUB_COLOR_NORMAL="yellow/black"
export GRUB_COLOR_HIGHLIGHT="red/black"
export GRUB_MENU_PICTURE="/home/dad/Documents/icons/grub.png"
#GRUB_FONT="/boot/grub/unicode.pf2"
``` 

Any help appreciated.  From what I have searched the above should work.

---

### Post by Quarkrad on 2022-09-05
Note:  The change in grub background does work

---

### Post by tea for one on 2022-09-05
I have followed this information from [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
> Editing /etc/grub.d/05_debian_theme

You can have 3 font colors: a menu color, menu highlight color and a normal color. The normal color will appear above and below the box. The menu color will appear as the box and the regular line color, while the menu highlight line will appear where the cursor is as the selected line.
Enter sudo nano /etc/grub.d/05_debian_theme

At line 122 where you see this line:
echo "if background_image make_system_path_relative_to_its_root "${1}"; then"
add these three lines below with your color choices after line 122 and save the file:

echo " set color_normal=cyan/black"
echo " set menu_color_normal=yellow/black"
echo " set menu_color_highlight=red/black"
Don't forget to run ```
sudo update-grub
```

I do not use Grub Customizer so I do not know if there will be any conflict.
It has been reported that Grub Customizer can change the contents of /etc/grub.d.
[https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

---

### Post by Quarkrad on 2022-09-05
That did the trick - thank you

---

