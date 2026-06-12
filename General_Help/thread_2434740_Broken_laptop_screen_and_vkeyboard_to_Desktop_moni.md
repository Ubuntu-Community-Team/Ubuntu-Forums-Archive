---
title: "Broken laptop screen and vkeyboard to Desktop monitor and usb keyboard?"
date: 2020-01-10
forum: General Help
---

### Post by josephchrzempiec on 2020-01-10
Hello  i need to somehow mirror the laptop screen which is broken to a Desktop screen. Problem is when i plug in a my Desktop screen it goes right to Second monitor. I can right click on the desktop and select change background or i can open a Terminal But that is all. The Screen on the laptop is broken and the keyboard is also broken. So i use a Usb keyboard. Is there a way in Terminal i can change the settings to mirror the screens from first to second?



Joseph

---

### Post by CatKiller on 2020-01-10
You should be able to use xrandr's --output options to set your monitor as the primary display and turn off the broken one. Otherwise you can use its --same-as option to mirror the display.

---

### Post by josephchrzempiec on 2020-01-10
Hello the problem is i can not get into xrandr's at all on the second screen. I have no icons or anything to get to settings. I only learn about xrandr a few moments ago. and Not sure if there is a way in Terminal to do that.

---

### Post by coffeecat on 2020-01-10
Support, not chat.

*Thread moved to **General Help** sub-forum.*

---

### Post by josephchrzempiec on 2020-01-10
Hello thank you for moving me in the right direction.

I kind of figure out how to do it in Terminal xrandr --output LVDS-1 --off and it turns it off and everything goes to my hdmi screen. but it if reboot it comes back. Is there a permanent way of just going to the hdmi?

---

### Post by CatKiller on 2020-01-10
> **josephchrzempiec said:**
> Is there a permanent way of just going to the hdmi?

The permanent way is to create an xorg.conf that does the same thing as your xrandr command, now that you know that it works. A semi-permanent way would be to run your command in one of the scripts that runs at login.

---

### Post by josephchrzempiec on 2020-01-10
Hello i did mange to find this that helped a lot [https://unix.stackexchange.com/questions/399739/disable-laptop-screen-and-use-only-vga](https://unix.stackexchange.com/questions/399739/disable-laptop-screen-and-use-only-vga) under answer it shows to edit the Grub area and update the grub. So i have tried it and rebooted that seem to work. Thank you all for helping me and pointing me in the right direction.


Joseph

---

