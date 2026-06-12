---
title: "Video card or software problem?"
date: 2013-09-08
forum: General Help
---

### Post by markus79 on 2013-09-08
I'm not sure if I have a hardware problem with my NVIDA video card or if its a software-related issue.

I boot my Ubuntu, I see the graphical motherboard display, and then I see all the plain text just fine. When it tries to go into graphical mode, and would normally show me the Ubuntu login screen, the image just goes black. Everything is still running fine, my monitor shows it still has a signal, it's just a black screen.

Someone told me it was probably my video card and I should reseat it, which I just did.

I have all my latest updates, I know nvidia doesn't always play nice with Ubuntu, but this just all of a sudden happened to me today with Ubuntu 13.04

Any suggestions would be much appreciated!!

Thanks
Markus

---

### Post by deadflowr on 2013-09-08
Probably driver issues.
Seeing as your seeing something on the screen when you turn the computer on, right?

What driver are you using, the out of the box nouveau driver or the additional driver nvidia?
If nvidia, which version, or which version ubuntu do you have installed?

You can also try adding nomodeset to the grub, if you can load grub(press the shift key right after the startup screen(BIOS) disapears)
In grub press E key and then add nomdeset at the end of the line quiet splash.
then exit on see if it loads.

But it's probably more important to know what  graphics card, version of Ubuntu and what drivers you have.

Edit: nevermind the Ubuntu version, I somehow missed 13.04.

---

### Post by markus79 on 2013-09-08
Thanks. I tried nomodeset but that did not help.

I'm pretty sure I am using the restricted nvidia driver in 13.04 but not sure how to find out what version it is using terminal.

Card is NVIDIA GF 104 [GeForce GTX460]

---

### Post by djyoshabyd2 on 2013-09-08
open a terminal, and do 

> lsmod | grep nvidia

If that responds, you are using the proprietary nvidia drivers.

---

### Post by djyoshabyd2 on 2013-09-08
Also, you need to see which driver version you are using, if you do have it. search in your programs for :

nvidia-settings

if you open that (if its even there), then it will tell you the driver version. Older drivers dont work with the 3.8 kernel and the X version that Raring uses. You may  have to install the Nvidia drivers by hand from the a terminal. 

If you do, download the nvidia driver. THen:

Make a copy of these notes, as you will not be able to see them while installing. 

press:
> ctrl+alt+F2

log in with your username and password at the terminal

navigate to your download folder (or wherever you donwloaded it)

eg:

> cd ~/Downloads

then

> chmod +x NVIDIA-nameofdriver

sudo service lightdm stop

sudo ./NVIDIA-nameofdriver

follow all install instructions

reboot when its done.

---

### Post by markus79 on 2013-09-08
Thanks, Yep "nvidia 11313877"

---

### Post by markus79 on 2013-09-08
And yes, I do get a display when it powers on, I get the bios startup graphic and then the text as it boots, but when it would go to a graphical-mode (when i should get login screen) it goes black -- then when I press the power button to power it down,  I get the text again as it shuts down.

---

### Post by djyoshabyd2 on 2013-09-08
ok, so when you get it booted up and its running, and the screen is blank, press:

> ctrl+alt+F2

Does it take you to a terminal and ask for a username?

---

### Post by djyoshabyd2 on 2013-09-08
If it was the video card, it wouldnt show anything at all. No buils screen, nothing. At least I have never seen one do that.

---

### Post by djyoshabyd2 on 2013-09-08
If you can get to that, then log in with your username and password, then :

Remove current xorg.conf,

> sudo rm /etc/X11/xorg.conf

Then rebuild with:

> sudo nvidia-xconfig


reboot, and see if that will let you in. 

Check your BIOS for any video card settings, too. 

You said it didt boot from the CD either? Thats odd. It should for sure, but it could still be a BIOS setting wrong or something like that. I dont know how a video card would display anything at all if it was bad.

One more thing to look at: Is the backlight on your screen staying on? Or is the monitor getting NO signal at all, and no backlight? My last screen that burned out had a bad inverter, and it would show the bios screen, but as soon as it tried to get beyond GRUB, the screen would turn black, but if I held the screen to the light or a flashlight at just the right angle, I could see the ubuntu desktop, but there was no backlight. Just another thing to check.

---

### Post by markus79 on 2013-09-08
No, I cannot get to a terminal w/ ctrl+alt+f2 when it is running and blank screen.

nvidia-settings says "ERR :The control display is undefined"

---

### Post by markus79 on 2013-09-08
I will try getting a new x11 conf... and yes, the monitor shows a green signal all the time, so it doesn't look like it's the video card otherwise the monitor would probably complain about no signal and turn off

---

### Post by djyoshabyd2 on 2013-09-08
> [COLOR=#000000]then when I press the power button to power it down, I get the text again as it shuts down.[/COLOR]

Sorry. Just re-read that. lol. Check that stuff above and see if it works. I think rebuilding your xorg.conf as described above may help or reinstalling your nvidia drivers may help. You would need to remove the nvidia drivers first with:

> sudo apt-get purge nvidia-*

restart

Then, reinstall the driver as stated in my instructions in the above post to get the most recent driver installed correctly. I have always had bad luck with Jockey (Additional Hardware tool in Ubuntu).

---

### Post by djyoshabyd2 on 2013-09-08
> [COLOR=#000000]I will try getting a new x11 conf... and yes, the monitor shows a green signal all the time, so it doesn't look like it's the video card otherwise the monitor would probably complain about no signal and turn off[/COLOR]

Do you have multiple monitors hooked up? or just one? You could also boot into recovery mode in GRUB. If you look in the GRUB boot menu right after the BIOS screen, you will have options. Use your arrow keys to go down to Advanced or Recovery Mode or something. Its usually right below the first choice. It will give you the option to run every kernel that is installed. Chose recovery mode for the first one. It will take you to a small CLI window, and you can choose Root Login (something like that).

From there, it will drop you to a command prompt as root, and you can run:

> rm /etc/X11/xorg.conf


Then try running

> nvidia-xconfig


NOTE: BE VERY CAREFUL DOING ANYTHING AS ROOT

---

