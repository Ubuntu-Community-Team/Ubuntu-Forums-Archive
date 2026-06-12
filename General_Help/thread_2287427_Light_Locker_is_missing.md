---
title: "Light Locker is missing"
date: 2015-07-19
forum: General Help
---

### Post by ckrles on 2015-07-19
HI, I installed ubuntu 14.04 lts on my laptop. I couldn't control brightness. I reset to maximum on every boot. So I went to terminal and ran:

*sudo gedit /etc/rc.local*     and I copied [I]echo 3 > /sys/class/backlight/acpi_video0/brightness

[/I]Now I can set the brightness to a level I'm comfortable with, but I find that Light Locker has disappeared from my setting menu. So now I can't control its options.

Any way to reinstall it or take it back? altough I don't know if it will reset brightness to maximum again.

I tried deleting *echo 3 > /sys/class/backlight/acpi_video0/brightness* to see if it came back, but no luck[I].
 
[/I]That is the way I found to solve the brightness setting. But I would reaa¡lly appreciate another one which doesn't seem to delete light locker.

Thank you very much.


Edit: I've just thought of searching for it in software center and there it was. I installed it but now it appears as a program, not included in the menu setting. By the way, on my menu setting I can see that the icon for the keyboard is missing when I choose a mac theme. I don't know why. It comes back when I restore the default theme.

As I stated before I would really appreciate that you could tell me a way to set the brightness other than the one I stated.

---

### Post by Frogs Hair on 2015-07-19
I've not used Light Locker , but have used the linked fix for_ intel_ graphics on 14.04. Both the Mac theme and Light Locker are 3rd party software so I couldn't even guess what the problem might be. [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

---

