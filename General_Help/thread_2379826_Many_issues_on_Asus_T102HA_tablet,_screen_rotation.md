---
title: "Many issues on Asus T102HA tablet, screen rotation, right click, screen brightness..."
date: 2017-12-10
forum: General Help
---

### Post by grandkodiak2 on 2017-12-10
Hey all, trying to figure out a few issues after installed on my Asus T102H touch tablet.

1st: the grub and the log in screen now default to portrait mode after installing from live usb, and the touchpad and touchscreen alignments dont rotate with the screen (they are in landscape still even though screen is rotated!). I added a "xrandr -o right" script to the startup and it works, but ONLY after the graphic loggin screen. Any reason why it changed to begin with? even windows now is in portrait but automatically rotates if i just turn the tablet. logging off or switching user reverts the screen back to portrait, then logging back in runs the script again obviously and corrects, but rather annoying that all of the sudden the screen defaults to portrait with nonmatching input alignment.

2nd: on that note, any way to get auto rotate to work? turning the tablet doesnt trigger rotation.

3rd: *resolved*

4th: power button turns of screen, but wont turn it back on. if you turn the screen off, you have to hold the button to reset to get the screen to wake back up. changing the power buttons mode in preferences has no effect (is suspend vs hibernate)

5th: screen brightness does not change with the slider, its always at max despite slider location.

6th: how do i mount the SD card? it doesnt appear to be detected even in gparted or fdisk. plugging the sd card in automounts but then freezes the system. starting with the card in, its not automounted or detected.

7th: wifi doesnt auto connect after first adding it, everytime you start the computer you have to turn off wifi, turn it back on, and manually hit connect to the wifi thats saved.

Thanks! Other then that all other functionality seems to be working as if it were an OEM install!

---

### Post by howefield on 2017-12-10
What version of Ubuntu have you installed on the machine ?

---

### Post by leeuwenburg on 2018-11-28
> **grandkodiak2 said:**
> Hey all, trying to figure out a few issues after installed on my Asus T102H touch tablet.
1st: the grub and the log in screen now default to portrait mode after installing from live usb, and the touchpad and touchscreen alignments dont rotate with the screen (they are in landscape still even though screen is rotated!). I added a "xrandr -o right" script to the startup and it works, but ONLY after the graphic loggin screen. Any reason why it changed to begin with? even windows now is in portrait but automatically rotates if i just turn the tablet. logging off or switching user reverts the screen back to portrait, then logging back in runs the script again obviously and corrects, but rather annoying that all of the sudden the screen defaults to portrait with nonmatching input alignment.


Hi i'm in the same zone as you are. Also the Asus T102Ha. 
My problem is that Xrandr commands don't seem to work at all.
I tried to fiddle around with the [COLOR=#000000][FONT=monospace]iio-sensor-proxy.  After unstalling that the screen worked fine *(not auto rotating) and my sound was gone :(

My question to you is, how did you manage to ass thr xrandr -o right script to the startup?


[/FONT][/COLOR]

---

