---
title: "How do I change the screen brightness with a keyboard shortcut?"
date: 2021-04-26
forum: General Help
---

### Post by Paddy Landau on 2021-04-26
I have been searching how to change my screen's brightness with a keyboard shortcut, because my keyboard doesn't have a physical key.

A tool such as xrandr isn't suitable, because it messes with my Night Light setting.

From the terminal or from Alt+F2, these two commands correctly raise or lower the screen's brightness respectively:
```
xdotool key XF86MonBrightnessUp
xdotool key XF86MonBrightnessDown
```
However, if I add these to my custom keyboard shortcuts, they don't work.

I created a basic script to do the same thing, and I discovered something odd. This script works when run from the terminal or Alt+F2, but not from a keyboard shortcut:
```
#!/usr/bin/env bash
xdotool key XF86MonBrightnessUp
```
However, this does work from a keyboard shortcut:
```
#!/usr/bin/env bash
zenity --info --text='Brightness up'
xdotool key XF86MonBrightnessUp
```
Of course, there's the inconvenience of pressing Enter to close Zenity's display before it works.

Putting Zenity into the background prevents it from working:
```
#!/usr/bin/env bash
zenity --info --text='Brightness up' &
xdotool key XF86MonBrightnessUp
```
Obviously, running Zenity to put something on the screen somehow "activates" the screen from Bash's point of view.

How can I achieve what I'm after without having to display something on the screen?

---

### Post by Xian on 2021-04-26
Can you use xbacklight with your GFX to control the brightness?

Brightness Down (example):
$ xbacklight -1

Brightness Up (example):
$ xbacklight +5

If it works test it by adding it:
[COLOR=#242729][FONT=Arial]Settings &#8594; Keyboard &#8594; Application Shortcuts

Reboot may be required.[/FONT][/COLOR]

---

### Post by Paddy Landau on 2021-04-27
Thank you for the reply, Xian.

Unfortunately, xbacklight does nothing whatsoever to my screen display, even after rebooting. There's no error message; it just does nothing. I've also tried using -display :0.

---

### Post by Paddy Landau on 2021-04-27
I've discovered the solution, with a bit of intuition and some trial-and-error.

The keys XF86MonBrightnessDown and XF86MonBrightnessUp are assigned in dconf respectively to
[FONT=courier new]/org/gnome/settings-daemon/plugins/media-keys/screen-brightness-down-static
/org/gnome/settings-daemon/plugins/media-keys/screen-brightness-up-static[/FONT]

Changing the key assignments to something that I could use (I chose <Super>F11 and <Super>F12) didn't work.

However, I found that using those assignments on a different key worked:
[FONT=courier new]/org/gnome/settings-daemon/plugins/media-keys/screen-brightness-down
/org/gnome/settings-daemon/plugins/media-keys/screen-brightness-up[/FONT]

Problem solved!

---

### Post by Impavidus on 2021-04-27
Alternatively, the brightness is available in the /sys pseudofilesystem. You can read the current brightness, the max brightness and set a new brightness.```
$ cd /sys/class/backlight/acpi_video0
$ ls
actual_brightness  bl_power  brightness  device  max_brightness  power  scale  subsystem  type  uevent
$ cat actual_brightness
16
$ cat max_brightness
20
$ echo 4 | sudo tee brightness
## This make my screen very dim
$ cat actual_brightness
4
```
This tends to be somewhat hardware dependent. Just have a look around there.

---

### Post by davelacorneille on 2022-03-12
Your problem with xdotool is that your keyboard shortcut and the xdotool key overlap.  You need to clear the key with:

xdotool key --clearmodifiers XF86MonBrightnessDown

---

### Post by Paddy Landau on 2022-03-12
> **davelacorneille said:**
> Your problem with xdotool is that your keyboard shortcut and the xdotool key overlap.  You need to clear the key with:

xdotool key --clearmodifiers XF86MonBrightnessDown
Hah! I wish that I'd thought of that!

Thank you — this will be useful in future.

---

