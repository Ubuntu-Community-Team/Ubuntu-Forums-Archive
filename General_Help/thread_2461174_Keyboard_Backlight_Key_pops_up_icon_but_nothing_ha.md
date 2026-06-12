---
title: "Keyboard Backlight Key pops up icon but nothing happens"
date: 2021-04-25
forum: General Help
---

### Post by bpazolli on 2021-04-25
I can't turn off my keyboard backlight on my Toshiba Portege Z930. I'm running Ubuntu 20.04.1 LTS. The laptop has a backlight key accessed by Fn+Z and it pops up an icon on the screen with a key and lines coming from it, but it has no effect. I've tried verious combinations of the following command in the terminal from what I've read in other answers:
```
echo 0 > sudo tee /sys/class/leds/toshiba::kbd_backlight/brightness
```
but again no effect.

I also tried editing /etc/default/grub to have acpi=off as that was mentioned in one of the posts to no effect as per below.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

Any ideas?

---

### Post by bpazolli on 2021-04-26
Some more details! I worked out that I can turn the keyboard backlight off in the bios settings. I also worked out that ```
echo 0| sudo tee /sys/class/leds/toshiba::kbd_backlight/brightness
``` was just writing 0 to a file. If I viewed that file it had the number 255 in it before and after the command. Since turning off the keyboard light it has 0 before and after any similar command with any number. Seems for whatever reason writing to the file /sys/class/leds/toshiba::kbd_backlight/brightness, doesn't work. The vim text editor doesn't throw up any issue when writing to the file. It is like some other process is just overwriting my changes.

The typical function for the backlight is to time out after a key not being pressed for a certain amount of time. Not sure if that function is somehow creating an issue.

---

