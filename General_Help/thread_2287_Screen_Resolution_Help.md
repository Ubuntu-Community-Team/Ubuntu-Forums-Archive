---
title: "Screen Resolution Help"
date: 2004-10-26
forum: General Help
---

### Post by Blue Storm on 2004-10-26
Hey all, how are ya?

First off, I am quite the Linux newbie, so I would appreciate it if we don't go too fast on this first date. I have used Mandrake before but I think Ubuntu is a whole new kettle of fish.

I have a 17" LCD with native resolution of 1280 x 1024 and that is what I was running it as. As soon as I got Ubuntu working it has stuck me with 1024 x 768 and what looks like some low colours. I cannot work out how to up the reseloution and change the colour depth. Can anyone help me out with a clear explination?

Cheers all.

---

### Post by SFN on 2004-10-27
You'll need some specs for your monitor. Usually it'll say something along the lines of "Optimal resolution 1280x1024 @ 85 Hz". Those numbers will vary.

Click "Computer"
Click "System Configuration"
Click "Screen Resolution"
Choose the resolution your monitor lists as optimal from the first drop-down list
Choose the accompanying refresh rate from the second drop-down list
Click Apply

You'll need to log out and log back in or, if you prefer, reboot.

---

### Post by princemackenzie on 2004-10-27
Also having this problem.  My monitor is capable of 1280x1024 and 75 Hz, but I'm incapable of inceasing it past 1024x768.  I also installed the nvidia drivers, but this didnt help.  Any suggestions?   8-[

---

### Post by Rancoras on 2004-10-27
Check your monitor settings in /etc/X11/XF86Config-4  (horizontal and vertical refresh, etc)

Make sure they match the specs in the manual for your monitor.

---

### Post by Alexari on 2004-10-27
[QUOTE=princemackenzie]Also having this problem.  My monitor is capable of 1280x1024 and 75 Hz, but I'm incapable of inceasing it past 1024x768.  I also installed the nvidia drivers, but this didnt help.  Any suggestions?   8-[[/QUOTE]

I found that if I didn't set it during the installation, I couldn't go above 1024x768.  Incidently, use SPACEBAR to select the available resolutions you want NOT the enter key.  I had to reinstall twice before I figured that out.  Now I can set all the resolutions I selected.

---

### Post by Beire on 2004-10-27
[QUOTE=Alexari]I found that if I didn't set it during the installation, I couldn't go above 1024x768.  Incidently, use SPACEBAR to select the available resolutions you want NOT the enter key.  I had to reinstall twice before I figured that out.  Now I can set all the resolutions I selected.[/QUOTE]
 is there any way to do this without reinstalling ? 

also i don't have a manual for my display so i dont know the vertical and horizontal rates !

---

### Post by taygan on 2004-10-27
you can reconfigure the xserver (for new monitor specs) by going to the terminal and typing *sudo dpkg-reconfigure xfree-xserver* 

It will not do the easy probe for the video card and montior but will walk you through a series of steps that will ask you all the nitty gritty details.  
My old Thinkpad 600 laptop wouldn't display correctly until I fixed the amount of RAM the video card had and lwer the color to 16  bits.  Now it's great!

---

### Post by beesee on 2004-10-27
[QUOTE=Beire]also i don't have a manual for my display so i dont know the vertical and horizontal rates ![/QUOTE]
You can probably find the specs for your monitor on the manufacturer's website (or google).

---

### Post by bstil on 2005-01-13
Does Warty use the auto-detection for /etc/X11/XF86Config-4 that Knoppix uses?

I just tried Warty live cd on my IBM Thinkpad T42 and when I changed the resolution above 1024x768, the screen display had problems.

In other words, should I try to boot first with Knoppix and save /etc/X11/XF86Config-4 and then use that in Warty?  Or since they are both Debian based distros, will I get the same autodetection with my Warty installer?

---

### Post by paul cooke on 2005-02-04
[QUOTE=taygan]you can reconfigure the xserver (for new monitor specs) by going to the terminal and typing *sudo dpkg-reconfigure xfree-xserver* [/QUOTE]

not quite... it's:

*sudo dpkg-reconfigure xserver-xfree86*

---

### Post by Ice-69 on 2005-02-04
sudo dpkg-reconfigure xserver-xfree86 didn't work for me, i'm still stuck at 640x480 @60hz.  I need 1024x768@85, I finally sorted out my driver problem(via vm400, now have vx support)

I tried manually editing the config file and took out all instances of 640x480 and left 1024x768 w/85 hertz everywhere,  gnome did not change at all.

other suggestions?

---

### Post by Wim Sturkenboom on 2005-02-07
[QUOTE=Ice-69]sudo dpkg-reconfigure xserver-xfree86 didn't work for me, i'm still stuck at 640x480 @60hz.  I need 1024x768@85, I finally sorted out my driver problem(via vm400, now have vx support)

I tried manually editing the config file and took out all instances of 640x480 and left 1024x768 w/85 hertz everywhere,  gnome did not change at all.

other suggestions?[/QUOTE]What are the settings for HorizSync and VertRefresh in the monitor sections of your XF86Config-4 file? Those should reflect the specifications of your monitor.

---

### Post by tom_ on 2005-02-07
I think the advice contained in this thread may be helpful ......

[http://www.ubuntuforums.org/showthread.php?t=5608&page=1](http://www.ubuntuforums.org/showthread.php?t=5608&page=1)

The live cd's monitor detection routines (cribbed from morphix/knoppix) have consistantly been better than the hardware detection routines in ubuntu and other distros X installation. In the case of Ubuntu, I found that it left you with X working, but at a refresh rate that was so low it gave me headaches. So, I copied the monitor definition lines (modelines) from the livecd's XF86Config-4 to a floppy and then cut and pasted the relevant modelines into my hard drive install. Once the modelines were properly in my XF86Config-4, I could get my resolution up to 75mhz, or whatever it was my monitor supported (wasn't my machine where this came up, so I don't remember offhand)

The warning came from a foolish attempt to wholesale replace the file. Apparently, the layout of the XF86Config-4 is somewhat different. While the modelines work, everything else won't and you are left with X in a non-working state if you simply copy the file instead of just selecting the relevant portions.

While there are tools for making the modelines out there within your installation, I've yet to have found any that were easy to use.
__________________
--dare2dreamer 

How to fix monitor refresh rates in XFree86

01) Boot computer off Ubuntu Live CD
02) Copy /etc/X11/XF86Config-4 to a floppy
03) Reboot into Ubuntu Installation on HD
04) Copy modelines from floppy file into monitor section of /etc/X11XF86Config-4

05) Restart X and reset refresh rate to something higher than 60hz

***WARNING: Only copy modelines sections. If you use live CD's XF86Config-4 as is you will break your X installation.

__________________
--dare2dreamer

---

### Post by Erwin Marti on 2006-02-08
Hello ubuntu friends,

I'm new in ubuntu, as well as in debian, but for the last 10 years my OS was linux in different distributions as RedHat and Suse among anothers, now I am looking for a stable and robust OS, and I like the ubuntu philosophy. I'm trying ubuntu 5.10 in the following system:
Vendor: GenuineIntel
Speed: 928.453 MHz
Model: Pentium III (Coppermine) 	
Memory: 516 MB
Sony Multiscan E200 17" + RIVA TNT2 Model 64/Model
64 Pro
 

The installation ran out without problems: the network card, printer, KB, mouse, cd, cd/dvd burner etc were correctly detected and configured.... but the graphical enviroment isn't.

The resolution after installation is 640X480 @ 60Hz, and no possibilities for change   are available in the preferences-resolution  .

Now I red many entries at ubuntu forums, and what I did up to now:
 sudo dpkg-reconfigure -phigh xserver-xorg
 sudo gedit /etc/X11/XF86Config-4, but this file "XF86Config-4" is not installed.
I also configured  manually:
 sudo gedit /etc/xorg.conf
but no succes. Files like XF86Config-4, xfree-xserver or xserver-xfree, do not exist on my OS 
In the xorg.conf, the videocard and display parameters are correctly as well as in the ubuntu hardware database.

Ok, guys can someone tell me what I have to do? are in ubuntu some configuration scripts like yast or sax2 in suse or setup in redhat?

---

### Post by Beire on 2006-02-08
you should look at the horizontal sync and Vertical Refreshrate in your Xorg.conf file.

I had to alter them to get my monitor at the wanted resolution.
You should lok them up for your monitor.
Here are mine for my 17" monitor. 
```
HorizSync	30-70
VertRefresh	50-160
```

---

### Post by perchu14 on 2007-09-23
> **Beire said:**
> is there any way to do this without reinstalling ? 

also i don't have a manual for my display so i dont know the vertical and horizontal rates !

This worked for me. (UBUNTU 7.04 Feisty Fawn)

1st stage:
Somebody wrote "Check the xorg.conf file"
I found this file on: /etc/X11 folder.

1-So now open a terminal "Applications>Accesories>terminal"
2-Type more /etc/X11/xorg.conf

You will see in the first lines the following info:

#If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

3- type: sudo dpkg-reconfigure -phigh xserver-xorg
It will let you to check or change your video controller and settings (resolution or monitor rates) for xserver.
As you says you don't know your monitor rates, I suggest you to choose for a low resolution one like 640x480 or 800x600 and after the reboot you cna choose the best for your monitor.
You need to reboot the system after changes.

2nd Stage
About your monitor rates:

As another guy wrote you can check it on the web or simply try a different configurations from   "System>Preferences>Screen Resolution"

The system will ask you "If you don't see it I will get back to the previous settings"

Good Luck

---

### Post by onionsauce on 2007-10-05
Thanks perchu14, your post helped,
I just got my wide LCD 1440x900 to go and it is a joy to see an LCD at native resolution.
It took a few tries, but Running
 >sudo dpkg-reconfigure -phigh xserver-xorg 
and a reboot allowed me to select the new resolution from 
System>Preferences>Screen Resolution.

Some notes about dpkg-reconfigure:
it first asks for a Video Card Driver and it came set to 'vesa', but for me I had no success until I smartened up and realized that 'nv' was nVidia (if you don't know your Card's manufacturer, look in System>Preferences>Hardware information).
After you hit [enter] to select the correct driver, it asks for you to select resolutions and this is done with the [space bar] to mark (with a star) your selections, then hit [enter].

---

