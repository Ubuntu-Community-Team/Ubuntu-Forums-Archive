---
title: "Messed up my screen resolution."
date: 2008-06-16
forum: General Help
---

### Post by Sico2 on 2008-06-16
I wanted to install Google Earth on my Acer5920G yesterday, but didn't succeed due to lack of X11 drivers or something. I tried to install them, but then I gave up. As I turned on my laptop today, it gave me a info (while booting -?-) that some screen resolution are missing and which one I want to choose. I've chosen max available, 800x600. But now I can't change it. My normal is 1280x800 @ 50Hz, but the max I can get is 800x600. It drives me nuts! I have a Nvidia graphic card, and also installed the restricted drivers for it. But still no changes. Everywhere max possible for me is 800x600. What else can I do please?

---

### Post by rune0077 on 2008-06-16
Try installing nvidia-settings (it's in Synaptic) and use that to change your resolution. If that doesn't work, try reinstalling the drivers.

---

### Post by mgmiller on 2008-06-16
Use this command to pop up the gui:
```
gksu displayconfig-gtk
```
then skip to instruction 5 below.

If you want to permanently add it to your menu system and then run it, do the following:


1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select "generic" at the top of the list and on the right find LCD of the correct resolution assuming it's an LCD, otherwise scroll down a bit and use Monitor of the correct resolution for CRT, or try Plug 'N Play.
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

---

### Post by Sico2 on 2008-06-17
mgmiller

Did as you stated, but:
1)I have the 1280x800 as I wanted, but it doesn't hold after reboot or log out. Need to go there every time and set it manually
2)The tests for my graphic card fail, for both nvidias driver I can shoose from on the list (it's a Nvidia 8600M GS or something).
The driver is on automatic now, and seems to be fine, but only until I shut down the laptop.

---

### Post by mgmiller on 2008-06-17
Have you tried as rune0077 suggested?  Try running:
```
nvidia-settings
```On the left side, go to the "X-server Display Configuration"

On the right side, in the Display tab, select your resolution and then click "Save to X configuration File".   Then click quit.

See if that persists across logins.

The other thing I am wonder about is if you are running nvidia-glx or nvidia-glx-new.  I suspect your card may require the "new" glx driver.  Take a look in synaptic and search on nvidia-glx and see which version you are running.

Edit:

After some more googling around, I am now pretty much convinced that you should be using nvidia-glx-new.  The version in our repositories is 169.12 and is the driver I am using for my geforce 7800 GT.  

Check in synaptic to see which version you are using.

---

### Post by Sico2 on 2008-06-18
I am using the -new drivers. 
I did the settings from nvidia x server settings (I even managed to turn off the creepy logo!) and all seems to be working fine now. Only when I launch Ubuntu loader, the resolution is still 640x480 and somewhat separated in the screen (the Ubuntu logo with the orange bar running from left to to right). Apparently it was in the xorg.conf file to fix this, but nothing is lower than 1280x800 so no idea where I could change this last bit :)
But is ok as it is now. Am happy so far.
Thanks! all

---

### Post by mgmiller on 2008-06-18
> Only when I launch Ubuntu loader, the resolution is still 640x480 and somewhat separated in the screen (the Ubuntu logo with the orange bar running from left to to right). Apparently it was in the xorg.conf file to fix this, but nothing is lower than 1280x800 so no idea where I could change this last bit :smile:Install the start up manager applet:
```
sudo apt-get install startupmanager
```After it's installed, run System > Administration > StartUp-Manager

The first tab is "Boot Options"
In the middle is "**Display**"

This area sets the resolution and color depth of the Ubuntu logo and bar when starting and shutting down.  It also affects the resolution of virtual terminals (ctrl-alt-F1, etc).

You can change this to what ever you like within the limits of your video card.  Be aware that this will be displayed using the VESA driver during boot and shut down and not all video cards can output 1280 x 1024 at 24 bits without creating an "out of range" error on the monitor.

Anyway, change it to what you want and  click close.  It will do a post configuration thing and then the changes will be there after a full shut down and reboot.

If you get an "out of range" error, don't worry, just give it a little time and as soon as it displays the normal login screen, your regular video driver will take over and you will be able to log in.  

Then just go back to startupmanger and try a different resolution/color depth.

---

### Post by Sico2 on 2008-06-19
The resolution of the logos is fine now(1280x1024), both launch and shut down. A small problem occurred though. This time right after the GRUB loader. It gives me a message:

Undefined video mode number 31b:
Press <ENTER> to see all modes available <SPACE> to continue or wait 30 sec.

After I press Enter it shows me 6 available modes (mostly font size in this loading mode, options 0-6). Each of them has a code. I took a code 0F03 for 80x28 pixels mode, but it works only as I enter it, and asks me again after another restart or shutdown. It doesn't remember the settings. 
How can I get rid of it?

---

### Post by mgmiller on 2008-06-19
I did find one other person with this problem:
[http://ubuntuforums.org/showthread.php?t=775261](http://ubuntuforums.org/showthread.php?t=775261)

They never got an answer.  Try hitting the space bar and see if it just continues to boot normally.

---

### Post by Sico2 on 2008-06-19
All works fine after enter or space, but why all of a sudden it appears in my loader? I want it wiped out somehow.

I tried with the nosplash command in /boot/grub/menu, editing boot from grub level etc. it doesn't work. Apparently no one found solution for this yet..?

If I only didn't touch the X11 folder! :|

---

### Post by mgmiller on 2008-06-20
Go back into startup manager and try slightly lower resolution like 1024 x 768 and also try different color depths.  I think you may be sending a type of signal that the frame buffer in your video card cant' support while using the VESA driver.

---

### Post by Sef on 2008-06-20
Moved to General Help.

---

### Post by Sico2 on 2008-06-20
I made it! :)

Whoever still has this problem, here's the solution:

make yourself a root or similar to edit system files (gksudo nautilus).

Go to /boot/grub/ and open the menu.lst file

Find the line that starts :
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=*****-****-****-****-**** ro quiet splash vga=795

and then instead of '795' on the end of the line take any of the modes you get while you boot from list 0 to 6 (0F03, 0F05, 0F07 etc.) each one has a different font size that you get while booting, 80x60, 80x25 and so on. So my line now looks like this:

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=*****-****-****-****-**** ro quiet splash vga=0F03

Save, and restart.
Done. 
\\:D/

---

