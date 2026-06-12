---
title: "How do I change terminal to 80x24"
date: 2013-03-08
forum: General Help
---

### Post by JRV on 2013-03-08
When I press <CTRL>-<ALT>-<F1> to go to a full screen terminal the text is very small and hard to read.
How do I change it to 80x24 with large type?

---

### Post by sudodus on 2013-03-08
> **JRV said:**
> When I press <CTRL>-<ALT>-<F1> to go to a full screen terminal the text is very small and hard to read.
How do I change it to 80x24 with large type?

One way is explained in this link

[[COLOR=#ff0000]https://help.ubuntu.com/community/Grub2/Displays#Setting_Menu_Font_Colors[/COLOR]]("https://help.ubuntu.com/community/Grub2/Displays#Setting_Menu_Font_Colors")

> **Changing Menu Resolutions**

 If the user wishes to change the resolution of the GRUB 2 screen for image enhancement or general font size changes: 

[LIST=1]
[*]Set the desired resolution in */etc/default/grub*
[LIST]
[*]Change the value of **GRUB_GFXMODE=**  (Example: GRUB_GFXMODE=800x600) 
[*]If unsure of what resolutions are available to GRUB 2 they can be displayed by typing vbeinfo in the GRUB 2 command line. The command line is accessed by typing "c" when the main GRUB 2 menu screen is displayed. 
[/LIST]
  
[*]Select an image of the same proportions.
[LIST]
[*]GRUB 1.99 - Place the image in the *grub* folder or add a *GRUB_BACKGROUND* entry in */etc/default/grub* 
[*]GRUB 1.98 - Change the value of *WALLPAPER* in */etc/grub.d/05_debian_theme* 
[*]GRUB 1.99 - Place the image in the *grub* folder or add a *GRUB_BACKGROUND=* entry in */etc/default/grub* 
[/LIST]

[LIST]
[*]If an image of the correct size is not used, the menu will not be positioned correctly. 
[*]Use the image editor of your choice to create/resize an image to the correct size. 
[*]The user may be able to view the image size via *Properties* in a file browser (check the Properties *Image* tab in Nautilus). 
[/LIST]
  
[*]Run update-grub to update GRUB 2 
[/LIST]
 
**Creating User Splash Images**

 GRUB 2's splash image management makes it easy to use a wide variety of splash images. 
 
**Resolution Settings**

 The images in the *grub2-splashimages* package are primarily 640x480 images. 
GRUB 2 looks for a resolution setting in */etc/default/grub*. ***If uncommented***, the resolution is determined by this line: 


[LIST]
[*][TABLE]
[TR]
[TD="bgcolor: #fffbdb"]GRUB_GFXMODE=640x480[/TD]
[/TR]
[/TABLE] 
[/LIST]
 
To make the change in */etc/default/grub* work, you need to finish with the command
```
sudo update-grub
``` and it will work after the next reboot.

---

### Post by JRV on 2013-03-09
Grub is set the way I want it. 
I want to change the full screen terminal I get when I press <CTRL>-<ALT>-<F1>.

---

### Post by steeldriver on 2013-03-09
> **JRV said:**
> Grub is set the way I want it. 
I want to change the full screen terminal I get when I press <CTRL>-<ALT>-<F1>.

The virtual terminals get their mode from grub though - e.g. to get the desired (high) resolution VTs for my laptop (which is a 16:10 display) I have

```

GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD=keep

```

For low res you would probably want something like 800x600 - but technically you should drop to the grub prompt at boot time and run 'vbeinfo' to see the supported modes, especially if you have a nonstandard aspect ratio like mine

---

### Post by sudodus on 2013-03-09
> **steeldriver said:**
> The virtual terminals get their mode from grub though - e.g. to get the desired (high) resolution VTs for my laptop (which is a 16:10 display) I have

```

GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD=keep

```

For low res you would probably want something like 800x600 - but technically you should drop to the grub prompt at boot time and run 'vbeinfo' to see the supported modes, especially if you have a nonstandard aspect ratio like mine
+1
Try it, and you will see that it works :-)

The text screen mode uses the graphics mode set by grub. There might be advanced methods to add other fonts and font sizes keeping the grub graphics mode, that I don't know, but other people might show for us.

I have used
GRUB_GFXMODE=800x600x32
and now I'm using
GRUB_GFXMODE=1024x768x16
in a computer connected to a 1920x1080 screen,
and this lets me see more and longer lines,  when running in text mode compared to the default 80x25 lines that you get with
GRUB_GFXMODE=640x480

---

### Post by sudodus on 2013-03-09
> **sudodus said:**
> There might be advanced methods to add other fonts and font sizes keeping the grub graphics mode, that I don't know, but other people might show for us.

I found setfont at [[COLOR=#ff0000]http://askubuntu.com/questions/29328/how-do-i-increase-the-text-size-of-the-text-on-a-console[/COLOR]]("http://askubuntu.com/questions/29328/how-do-i-increase-the-text-size-of-the-text-on-a-console")

and suggest that you change font size according to these examples, which gives you a certain flexibility within the grub graphics mode between 13 (smallest) and 18 (largest) font size.
```
examples:

setfont Uni2-Terminus16
setfont Uni2-Fixed18
setfont Uni2-Fixed13

ls -l  /usr/share/consolefonts|grep Uni|grep Fixed
-rw-r--r-- 1 root root  4515 apr 19  2012 Uni1-Fixed15.psf.gz
-rw-r--r-- 1 root root  4364 apr 19  2012 Uni1-Fixed16.psf.gz
-rw-r--r-- 1 root root  3985 apr 19  2012 Uni2-Fixed13.psf.gz
-rw-r--r-- 1 root root  4216 apr 19  2012 Uni2-Fixed14.psf.gz
-rw-r--r-- 1 root root  4168 apr 19  2012 Uni2-Fixed15.psf.gz
-rw-r--r-- 1 root root  4112 apr 19  2012 Uni2-Fixed16.psf.gz
-rw-r--r-- 1 root root  4198 apr 19  2012 Uni2-Fixed18.psf.gz
-rw-r--r-- 1 root root  3982 apr 19  2012 Uni3-Fixed13.psf.gz
-rw-r--r-- 1 root root  4224 apr 19  2012 Uni3-Fixed14.psf.gz
-rw-r--r-- 1 root root  4146 apr 19  2012 Uni3-Fixed15.psf.gz
-rw-r--r-- 1 root root  4076 apr 19  2012 Uni3-Fixed16.psf.gz
-rw-r--r-- 1 root root  4204 apr 19  2012 Uni3-Fixed18.psf.gz

```

---

### Post by schragge on 2013-03-09
If you don't need the full character repertoire of Fixed fonts, try Terminus. It's a very good legible console font and is available in sizes up to 32x16. It contains glyphs for most Latin scripts, as well as Greek and Cyrillic. See comments in */etc/default/console-setup*

---

### Post by JRV on 2013-03-09
Thank you, but that didn't do it.
Ubuntu 12.10 64 bit 1280x1024 monitor.
Here is my /etc/default/grub file:
```

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
GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

export GRUB_COLOR_NORMAL="yellow/black"
export GRUB_COLOR_HIGHLIGHT="light-cyan/black"
export GRUB_MENU_PICTURE="/home/jack/Pictures/Wallpaper/Fire.jpg"

```

---

### Post by sudodus on 2013-03-09
Did you remember to run ```
sudo update-grub
``` and ```
sudo reboot
```

---

### Post by JRV on 2013-03-09
> **sudodus said:**
> Did you remember to run ```
sudo update-grub
``` and ```
sudo reboot
```

Yes

---

### Post by sudodus on 2013-03-09
This does not work like on my computers. What resolution do you get (at the grub menu) and at the text screen (pixelwise and textwise)?

---

### Post by sudodus on 2013-03-09
Have you got a multi-boot environment, so that the changes in this system's /etc/default/grub is not effective, and you need to reboot into another of the installed linux versions to really affect grub?

---

### Post by JRV on 2013-03-09
1 - When I play the robots game in the bsdgames package it fills the upper left 1/4 of the screen.

2 - It is a single boot system.

---

### Post by sudodus on 2013-03-09
So you still have the high resolution, probably the 1280x1024 resolution of your monitor.

Try [COLOR=#0000ff]at the grub menu to click the**  *c***  key[/COLOR] to get the command line prompt ```
grub> _
```

Then enter the command ```
[COLOR=#0000ff]vbeinfo[/COLOR]
```

Maybe you need to specify exactly the whole name of one of the displayed modes. I get several 640x480 modes
```
640x480x8
640x480x15
640x480x16
640x480x24
640x480x32
```
Select one of those that are displayed in [COLOR=#0000ff]***your***[/COLOR] computer (for example **[FONT=courier new]640x480x24[/FONT]**)
and use that in **[FONT=courier new]/etc/default/grub[/FONT]**

---

### Post by schragge on 2013-03-09
I guess
```
sudo dpkg-reconfigure console-setup
``` and selecting a larger console font size from there (IIRC, it's the 4rd question) would be an easier option for the OP.

---

### Post by sudodus on 2013-03-09
By the way, could it be that the picture

**[FONT=courier new]export GRUB_MENU_PICTURE="/home/jack/Pictures/Wallpaper/Fire.jpg"[/FONT]**

has higher resolution, and forces its resolution to grub? What if you try  to reduce its resolution and try again?

---

### Post by sudodus on 2013-03-09
> **schragge said:**
> I guess
```
sudo dpkg-reconfigure console-setup
``` and selecting a larger console font size from there (IIRC, it's the 3rd question) would be an easier option for the OP.
+1
This method is definitely worth trying :-)

[COLOR=#808080]or maybe also the method with [FONT=courier new]**setfont**[/FONT] from an earlier post.[/COLOR]

---

### Post by JRV on 2013-03-09
I ran vbeinfo, selected 640x480x16, put it in my /etc/default/grub file.
Then I ran update-grub, rebooted, ran vbeinfo again, now there is an astrisk beside 640x480x16.

I ran sudo dpkg-reconfigure console-setup and changed the font size from 16 to 18, and rebooted.

I changed the Grub menu picture to 640x480, ran update-grub, and rebooted.

Still no luck.

---

### Post by sudodus on 2013-03-09
Maybe some link along the line (graphics chip or monitor) can't run with the resolution 640x480 

1. Check with ***[COLOR=#0000ff]vbeinfo [/COLOR]***again and try with one of the available modes of size 800x600, for example
```
GRUB_GFXMODE=800x600x32
```
And change the corresponding background picture size to 800x600.

2. Will you see any difference, when logged in to a graphics screen you run each of these commands
```
setfont Uni2-Fixed18
``` ```
setfont Uni2-Fixed13
```

---

### Post by schragge on 2013-03-09
Wait, there's an error in your */etc/default/grub*. This ```
GRUB_GFXPAYLOAD=keep
``` should be ```
GRUB_GFXPAYLOAD[COLOR=#ff0000]_LINUX[/COLOR]=keep
``` You also can set it independent of Grub menu screen resolution:
```

GRUB_GFXMODE=1024x768x16
GRUB_GFXPAYLOAD_LINUX=640x480x16

```

---

### Post by JRV on 2013-03-09
> **schragge said:**
> Wait, there's an error in your */etc/default/grub*. This ```
GRUB_GFXPAYLOAD=keep
``` should be ```
GRUB_GFXPAYLOAD[COLOR=#ff0000]_LINUX[/COLOR]=keep
``` You also can set it independent of Grub menu screen resolution:
```

GRUB_GFXMODE=1024x768x16
GRUB_GFXPAYLOAD_LINUX=640x480x16

```

Now the text is still real small and it says:

* starting                                                                                                [ OK ]
mountall: Disconnected from Plymouth
mount: unknown file system type 'smbfs'
mountall: mount /mnt/mp3 [1317] terminated with status 32
mount: unknown file system type 'smbfs'
mountall: mount /mnt/mp3 [1611] terminated with status 32
mount: unknown file system type 'smbfs'
mountall: mount /mnt/mp3 [1804] terminated with status 32
mount: unknown file system type 'smbfs'

I commented out the line GRUB_GFXPAYLOAD_LINUX=640x480x16 and no longer get the error messages.

---

### Post by sudodus on 2013-03-09
Are you running a desktop or server version of Ubuntu? If desktop, since this text screen mode is so stubborn, would it be an alternative to run a terminal window with coarse font, for example

```
xterm -fa default -fs 20
```

or something similar (but via the settings menu) in your standard terminal window?

---

### Post by JRV on 2013-03-09
Thats a big improvment, thank you.

I'm leaving the thread open for a few days to see if somone knows how to do it.

---

### Post by sudodus on 2013-03-09
And if you specify your computer and monitor, it will make it easier for new people to help. Because the things we suggest (at least what I suggest) work at our computers. Someone may recognize your hardware and know how to manage it.

- computer brand and model
- motherboard
- cpu
- ram
- graphics card or chip
- monitor brand and model
- version of Ubuntu (12.04 LTS, 12.10, ...)
- flavour of Ubuntu (standard 'vanilla' Ubuntu, Lubuntu, Xubuntu, Kubuntu, ...)

If you don't know or remember, use lshw and hardinfo
```
sudo lshw>lshw.txt
``` and attach the file [FONT=courier new]**lshw.txt**[/FONT] to a reply
and
```
hardinfo
``` (you may need to install it)
```
sudo apt-get install hardinfo
```

---

