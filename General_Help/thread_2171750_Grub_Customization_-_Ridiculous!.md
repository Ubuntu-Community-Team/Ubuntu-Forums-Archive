---
title: "Grub Customization - Ridiculous!"
date: 2013-09-01
forum: General Help
---

### Post by alligoodw-live on 2013-09-01
My level of frustration knows no bounds. 

The objective is simple. I want a navy blue background for grub - nothing more and nothing less. Using Ubuntu 13.4 with Grub Custimizer, I still have a solid black background instead of a simple navy blue I was hoping for. All I need is a simple image that is nothing more than Navy Blue - how hard can it be? Using Gimp, I've followed the instructions per the Grub manual for image creation and I yet experience failed results. I just can't for the life of me figure out what I'm doing wrong. A splash-image should not be this hard to install with GRUB.

---

### Post by Quackers on 2013-09-01
Depending on the exact version of Grub the instructions can vary. Are you following the correct method for your version of Grub?

---

### Post by oldfred on 2013-09-01
I manually create a grub.cfg on my flash drives to boot ISO.
I use these settings, not an image for a fixed color:

set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

Shows available colors
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by deadflowr on 2013-09-01
In GIMP, after you make the image, go to scale image and where the drop down lists says cubic change it to interpolation(or whatever the word is).
Then run the scale image "ok"(again I forget what it says).
Then export the file. I tend to save/export it as png rather the jpg, for some reason it works better.
Then copy the file into /boot/grub
```
sudo cp fullfilename /boot/grub
```
then run update grub
```
sudo update-grub
```
The first line after configuring grub...
should be background found and the image's name.
Then the grub lists will show up and finally say "done" at the end, as long as no errors show up.

---

### Post by alligoodw-live on 2013-09-01
This is my etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
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


export GRUB_COLOR_NORMAL="white/black"
export GRUB_COLOR_HIGHLIGHT="yellow/black"
export GRUB_MENU_PICTURE="/boot/grub/grubdesk.png"

Is there anything that should NOT be there or should be added?

---

### Post by oldfred on 2013-09-01
I do not think export goes into /default/grub, but have never tried it..
The manual suggests a configfile as the correct place.

       [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
14.3.14 export
&#8212; Command: export envvar

       Export the environment variable envvar. Exported variables are visible to subsidiary configuration files loaded using configfile. 

Then see this secton.

 5.4 Embedding a configuration file into GRUB

I use configfiles to just load other boot stanza for my ISO loopmounts, now instead of 40_custom. Then I can edit the configfile without having to rerun sudo update-grub.

---

### Post by buzzingrobot on 2013-09-01
No way around it, grub is a pain.  It's one of those things that developers, in their ignorance, create thinking mere users will never, ever, want to play with it.

---

### Post by VMC on 2013-09-01
There is a way around it. The key word is "around". oldfred gave you one way. I would suggest google for another method. Ubuntu forums tent to be conservative, mainly because of Windows users not knowing Linux that well.

There's always another way.

---

### Post by oldfred on 2013-09-02
I followed directions and they worked in 12.04. I did try putting them in 40_custom and they did not work.
 [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)


gksudo gedit  /lib/plymouth/themes/default.grub
sudo update-grub

# copied this inot default.grub
set menu_color_highlight=yellow/dark-gray
set menu_color_normal=black/light-gray
set color_normal=yellow/black

---

