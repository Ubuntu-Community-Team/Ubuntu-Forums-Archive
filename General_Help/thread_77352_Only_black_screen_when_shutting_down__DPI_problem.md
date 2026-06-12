---
title: "Only black screen when shutting down / DPI problem?"
date: 2005-10-16
forum: General Help
---

### Post by federico_lu on 2005-10-16
Hello,
I have two smaller problems.

The first one is, that when I shut down the computer, there is only a black screen with a blinking cursor. It doesn't hang, and shuts down correctly, but I want to see what happens, I mean all the stuff when I stopps the services etc.

The second problem is, that some windows in the control centre of KDE (or now "System Settings" are too big, so that important buttons like the Admin Mode or Apply / OK are out of the visible screen area. Since I use a resolution of 1024x768, this is quite annoying, I think my res should be high enough to see everything? Some people told me now that depending of the DPI setting of my Xserver, fonts can be too big / small. How can I find out my correct DPI setting, and where do I change it?

thanks in advance for your help

---

### Post by greatshape on 2005-10-17
[QUOTE=federico_lu]Hello,
I have two smaller problems.

The first one is, that when I shut down the computer, there is only a black screen with a blinking cursor. It doesn't hang, and shuts down correctly, but I want to see what happens, I mean all the stuff when I stopps the services etc.

The second problem is, that some windows in the control centre of KDE (or now "System Settings" are too big, so that important buttons like the Admin Mode or Apply / OK are out of the visible screen area. Since I use a resolution of 1024x768, this is quite annoying, I think my res should be high enough to see everything? Some people told me now that depending of the DPI setting of my Xserver, fonts can be too big / small. How can I find out my correct DPI setting, and where do I change it?

thanks in advance for your help[/QUOTE]


I have the same problem with shutting down.(black screen with cursor, and that's it)
I have it on two kubuntu systems (both upgraded from hoary) and
also on a fresh install with ubuntu 5.10 on a laptop.
I don't like it also, but i have no idea how to solve it.
I start to wonder, Isn't it like this with all breezy systems???
Or are there people out there who do have a normal shutdown screen?

regards Steve

---

### Post by Segovia on 2005-10-17
[QUOTE=federico_lu]when I shut down the computer, there is only a black screen with a blinking cursor.[/QUOTE]
It's the same for me too.

I'm not sure about changing DPI in KDE.  If you have a reasonably new monitor, it will use the monitor DPMS info to find out the exact physical size of your screen and set the DPI accordingly.  If you change the DPI manually, not only will the fonts change, but *everything* displayed on the screen will change.  Seems rather drastic just because one program (that's not used often) is oversized.  ;)

JRiddell mentioned on his kdedevelopers.org blog that he is aware of the problem you describe, so perhaps it'll get fixed?

---

### Post by Teroedni on 2005-10-17
Hmm i dont get the problem
When i shutdown on Brezzy 5.10 i can see the shutting down of modules and such in console.
Try using pnp=no in the bios and see if that works for you


I have had problems in my low end pc , but thats because the acpi in bios and the connection on the motherboards have been wrong.

---

### Post by federico_lu on 2005-10-17
[QUOTE=Segovia]
...
I'm not sure about changing DPI in KDE.  If you have a reasonably new monitor, it will use the monitor DPMS info to find out the exact physical size of your screen and set the DPI accordingly.  If you change the DPI manually, not only will the fonts change, but *everything* displayed on the screen will change.  Seems rather drastic just because one program (that's not used often) is oversized.  ;)
...
[/QUOTE]

I can live with it, that's right, but in fact most, nearly all of the windows in the "System Settings" dialog are oversized. But I've found out that when using the standart look however, everything's fine again, so I'd just run "kdesu kcontrol" now everytime I have to use it.
The thing with the DPI setting was only an idea, don't know if it would work, it's only because I saw a screenshot of the new System Settings dialog from a user who also uses my resolution, only that on his screenshot the fonts and other things looked a bit smaller, even better than on my screen. Not significantly smaller, but enough to fit everything (nicely) on the screen.

Anyway thanks to every user who has and who will write something about the problems described in this thread ;)

---

### Post by Segovia on 2005-10-17
[QUOTE=federico_lu]The thing with the DPI setting was only an idea, don't know if it would work[/QUOTE]
It'll work, no doubt.  Depending on which way you adjust it, you can make everything smaller, or larger.  I read a howto a long time ago about changing the DPI in KDE, I don't recall all the details, but it seemed fairly complicated... especially compared to the GUI tools in windows and gnome which accomplish the same thing at the click of the mouse.

I used Kanotix for a few months, and he (Kano) has got a script to do it, I don't know if it'd work on Kubuntu or not.

---

### Post by Segovia on 2005-10-17
OK, here we go.  Found this on KUDOS:

[http://kudos.berlios.de/kf/kf1.html#setxdpi](http://kudos.berlios.de/kf/kf1.html#setxdpi)

---

### Post by gha on 2005-11-04
I also had the problem of no text display on shutdown or reboot after installing Kubuntu 5.10 (Breezy). After a brief message that KDM was shutting down, there was only a blank screen with flashing cursor at upper left. I have a desktop system with S3 ProSavage graphics adapter and 1024x768 LCD monitor.

In my case the problem appeared to be caused by the the shell script '/etc/init.d/usplash'. Deactivating it with 'sudo chmod -x /etc/init.d/usplash' allowed the shutdown/reboot text to be displayed. However the shutdown/reboot sequence still attempted to call the script and the text would include a 'permission denied' message for running '/etc/init.d/usplash'.

I found the best solution was just to delete all lines in '/etc/init.d/usplash' file apart from the first line which identifies it a shell script. It then becomes a shell script without any action. Keep a backup of the original file.

These modifications did NOT prevent the usplash graphical screen from being displayed and exiting normally at bootup, despite the the following comments noted at the beginning of the usplash script:
# The usplash script makes sure that usplash exits at the end of 
# the boot sequence and re-run the console-screen.sh script to make
# sure that the console fonts are actually set

Ideally the shutdown/reboot text would be displayed in a usplash graphical screen, but I understand that usplash has not been fully implemented in Breezy, and that no usplash screen on shutdown/reboot is expected behaviour.

[A further minor problem on my system was that the extreme right hand end of the text display was offscreen (the ']' in '[ok]' was missing). Adding vga=769 to the kernel boot parameters in '/boot/grub/menu.lst' cured this.

---

