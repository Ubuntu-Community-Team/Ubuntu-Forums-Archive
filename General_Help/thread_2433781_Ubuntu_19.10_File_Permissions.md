---
title: "Ubuntu 19.10 File Permissions"
date: 2019-12-25
forum: General Help
---

### Post by Redalien0304 on 2019-12-25
[COLOR=#000000]Have a Dell Latitude E6500 with Ubuntu 19.10 with Cinnamon DE. Cannot Edit Brightness Settings in /sys/devices/platform/dell-laptop/leds/[/COLOR]dell::kbd_backlight. Can edit Brightness File the changes do not Save. max_Bightness Cannot save Gives me Error "Could not save the file [COLOR=#000000]/sys/devices/platform/dell-laptop/leds/[/COLOR]dell::kbd_backlight/max_brightness", Unexpected error: Error writing to file: input/output error.
Have tried Using Sudo Nemo & Sudo su doe not work for me.

---

### Post by CatKiller on 2019-12-25
Those [aren't really files](https://en.wikipedia.org/wiki/Sysfs). You can pass values to them with echo or read from them with cat, but you can't open them with a text editor.

---

### Post by Redalien0304 on 2019-12-25
I tried that already did not work.

[https://askubuntu.com/questions/1076393/dell-keyboard-backlight-is-not-working](https://askubuntu.com/questions/1076393/dell-keyboard-backlight-is-not-working)

tried all steps from the link above
echo 4 | sudo tee /sys/devices/platform/dell-laptop/leds/dell\:\:kbd_backlight/brightness
did not change the values.
or am i missing something?

---

### Post by Redalien0304 on 2019-12-26
Bump Anyone?

---

### Post by bernard010 on 2019-12-26
> [COLOR=#000000]Cannot Edit Brightness Settings in /sys/devices/platform/dell-laptop/leds/[/COLOR]dell::kbd_backlight
I can offer this documentation:    [https://help.ubuntu.com/stable/ubuntu-help/display-brightness.html.en](https://help.ubuntu.com/stable/ubuntu-help/display-brightness.html.en)

Did you check your power saving settings ? Automatically control screen brightness to reduce battery usage.
           
                 [https://help.ubuntu.com/stable/ubuntu-help/power.html.en](https://help.ubuntu.com/stable/ubuntu-help/power.html.en)

I hope this will help.

---

### Post by Redalien0304 on 2019-12-26
Yep checked that already. Just cannot change the values for the keyboard backlight.

---

### Post by Redalien0304 on 2019-12-30
Bump Anyone??

---

### Post by Redalien0304 on 2020-01-06
Bump Anyone?? On file permissions for Keyboard Backlight?

---

### Post by CatKiller on 2020-01-06
> **Redalien0304 said:**
> Bump Anyone?? On file permissions for Keyboard Backlight?

It's got nothing to do with file permissions because *they aren't files*. They're an interface to how the kernel configures the hardware's own options.

On my Dell laptop keyboard, max_brightness is 2.

---

