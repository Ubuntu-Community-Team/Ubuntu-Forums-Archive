---
title: "Increase Resolution"
date: 2006-10-30
forum: General Help
---

### Post by Aquiva on 2006-10-30
I tried to increase the resolution, but the max setting was "1280 x 1024". I'm currently running on a 20" LCD moniter and have been running on 1400 x 1050 (max res I can get on Windows. Although It would be nice to get higher than even that.)

So, how can I allow ubuntu to give me at least 1400 x 1050 res?
Do I need to install a driver or something?

Thanks!

 ~ Mark

---

### Post by CatKiller on 2006-10-30
You might find it advantageous to install a different driver for your video card.

You may find that **sudo dpkg-reconfigure -phigh xserver-xorg** is enough configuration to get the resolutions you want. You might also find it useful to have researched the refresh rate ranges of your monitor.

---

### Post by Aquiva on 2006-10-31
I'm sorry to be newby - but where do I find the "sudo dpkg reconfig" or the "phigh xserver-xorg" and what do I edit with them to increase resolution?

 ~ Mark

---

### Post by Aquiva on 2006-10-31
Okay well I found the xorg file and I used the HowTo to edit it the monitor section to 1400 x 1050 at 90HZ

But then it said that I don't have permission to save that file!?
(Is this cause I"m running it live?)

 ~ Mark

---

### Post by roger99 on 2006-10-31
Hi,

The previous advice is not a program it is the command you need to enter into a terminal to reconfigure the xserver.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Try it, it may be all you need to get the resolution you need for your monitor.  If not try editing the xorg.conf file to force gnome to display the resolution you require.  In the same terminal window enter

```
sudo gedit /etc/X11/xorg.conf
```

Under the section screen you should see something like this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LS902U"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
```

Repeated for all the various colour depths.  Enter your resolution in these sections and gnome should use the highest as default.  For example

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LS902U"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
```

I hope this solves your problem.

---

### Post by CatKiller on 2006-10-31
> **Aquiva said:**
> But then it said that I don't have permission to save that file!?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

> (Is this cause I"m running it live?)

Running off the live cd you'll have to do this every time (obviously). I'd suggest that you don't bother until you've installed it - then you can make a permanent change, if it is still required.

Otherwise, log out and then do a **Ctrl-Alt-Backspace** to restart your X server once you've made the changes you want.

---

### Post by Aquiva on 2006-11-01
**HELP!!** I pressed CTRL + ALT + BACKSPACE and it made my GUI dissapear and now only have command line!
(I rebooted and am on Windows now)

What do I type to reactivate my GUI!? Help!

Once I do... the sudo xorg commands weren't working in changing my resolution, it was asking for like my hardware - gave a list of random applications like: voodoo, ati, vga, tga, vmplayer ?
:/


 ~ Mark

---

### Post by CatKiller on 2006-11-02
If you made a backup (I think dpkg-reconfigure will have done this automatically) you can copy that file over the new one to get your X configuration back as it was (sudo cp /etc/X11/xorg.conf.whateverthebackupiscalled /etc/X11/xorg.conf). Or if you want to correct the steps that led to your X server not restarting, you could find out some things about your hardware and then run the dpkg-reconfigure command again. You can look at the Device Manager in Windows to find out some stuff, since you're there already.

The "list of random applications" it asked you about is the list of drivers that you could use. "vesa" would be a fairly safe bet if you have to go that route to get a GUI back, like the generic VGA driver in Windows.

I guess you didn't look up the specs of your monitor, either? :)

Good luck.

EDIT: Are you still on the live cd? Because if you are, then none of what you did will be saved. Just reboot and have another go.

---

### Post by Aquiva on 2006-11-02
I know it has made several backups, but I have no clue what they would be called.

So I have no GUI, all I have is a black and white command center.
So I need to type in the backup, but if I don't have a GUI to know the extension to the backup... how do I get it?

Is there an CTRL ALT BACKSPACE undo combo? :P
There isn't some button that will auto-redo the xorg, just like CTRL ALT BACKSPACE makes it go to command line?

And no, I installed it now :/.

 ~ Mark

---

### Post by stylishpants on 2006-11-02
The backups would be in the same directory as your xorg.conf.  Try these commands. 

```

    cd /etc/X11
    ls

```

This should show you the xorg.conf and several other files.  The backup files will have names like this:

```

  xorg.conf.20061028212758
  xorg.conf.20061028213131
  xorg.conf.20061028213327

```


You can use the "cp" (copy) command to copy one of the backups over top of your broken xorg.conf.

```

  sudo cp xorg.conf.20061028212758 xorg.conf

```


Alternatively, you can try generating a new one, with 

```

    sudo dpkg-reconfigure xserver-xorg

```

Normally I would tell you to restart your X server after that with one of these commands:

```

    sudo /etc/init.d/xserver-common start
    sudo /etc/init.d/gdm start

```

However, this doesn't seem to work in edgy, at least not for me.  So, you might have to just reboot to try out a different xorg configuration.

Good luck!

---

### Post by nyinge on 2006-11-02
> **Aquiva said:**
> **HELP!!** I pressed CTRL + ALT + BACKSPACE and it made my GUI dissapear and now only have command line!
(I rebooted and am on Windows now)

What do I type to reactivate my GUI!? Help!


I suppose typing the following code in the terminal (black & white screen) should get you back into GUI:
```

startx

```

From your above posts, I believe you're trying Ubuntu live CD.  If so, all settings you've changed will be reverted back to original once you reboot your machine.

---

### Post by Aquiva on 2006-11-02
I've tried all of the commands and they aren't working. 

This is what happens: I turn on my computer, GRUB loads, ubuntu auto-loads and then a screen shows up that has a mostly blue background with weird characters to border a table - inside it it says:
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes> <No>

If I hit No then it just goes to the black screen where I can type stuff in, but nothing works.

If I hit Yes, it continues:
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 1686
Current Operating System: Linux Aquiva 2.6.17-10-generic #2 SMP Fri Oct 13: 18:45:35 UTC 2006 1686
Build Date: 07 July 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 2:08:20:22 2006 (==) Using config file: "/etc/X11/xorg.conf"

Fatal server error:
no screens found

<ok>

Then it asks if I want to view the detailed output. But this is /extremely/ long and I won't type it all up.


The X server is now disabled. Restart GDM when it is configured correctly.

<ok>



I hit ok, then it takes me to the black screen where I can type things

?? Thanks.

 ~ Mark

---

### Post by Aquiva on 2006-11-02
And now Windows won't boot. It gives me "sorry for the inconveniences. But Windows did not start successfully. A recent hardware or software change might have caused this.
If your computer stopped responding, restarted unexpectedly, or was automatically shut down to protect your files and folders, choose Last Known Good COnfiguration to revert to the Most recent settings that worked.
If a previous startup attempt was interrupted due to a power failure or because the Power or Reset button was pressed, or if you aren't sure what caused the problem, choose Start Windows Normally.

Safe Mode
Safe Mode with Networking
Safe Mode with Command Prompt

Last known Good Configuration (your most recent setting that worked)

Start WIndows Normally



Whichever I choose, it just shows the loading screen, and then restarts the computer - and I get stuck in an endless repetition.

And Ubuntu isn't working (see my above post). Giaaah!](*,) 

 ~ Mark

---

### Post by CatKiller on 2006-11-02
> **Aquiva said:**
> I've tried all of the commands and they aren't working. 

I hit ok, then it takes me to the black screen where I can type things

So what happens when you type them?

"No screens found" suggests that your xorg.conf is broken.

I'd assumed earlier that you'd misconfigured your X server before you hit Ctrl-Alt-Backspace, and that's what had messed you up, but since Windows won't load either it sounds like a hardware problem to me. It's unlikely that anything you've done has affected your Windows install - there are things that could affect it, but you'd probably have noticed doing them even if you didn't mention it here - which leaves hardware as the common factor between your broken Ubuntu and your broken Windows.

If you haven't messed around in the BIOS, I'd suggest that you open up the case and start checking connections. Make sure everything is seated properly and all the fans are OK, and the like.

---

### Post by Aquiva on 2006-11-02
"So what happens when you type them?"
Nothing, I type in the sudo commands, or anything and hit enter and nothing will happen. It just goes to the next line. -So I guess it isn't the commandline.

"I'd assumed earlier that you'd misconfigured your X server before you hit Ctrl-Alt-Backspace, and that's what had messed you up"

Yes.

I have not messed with the BIOS, besides originally to change it to "boot from disk" (but I don't need the disk anymore, should I switch it back? - it didn't seem to matter earlier)

I haven't messed with the inside of the computer, so I know its not anything in there.

I just need to know ... how do I reset the xserver?
(can I reinstall linux *again* without messing things up?)

Thanks,
 ~ Mark

---

### Post by CatKiller on 2006-11-02
> **Aquiva said:**
> "So what happens when you type them?"
Nothing, I type in the sudo commands, or anything and hit enter and nothing will happen. It just goes to the next line. -So I guess it isn't the commandline.

Sound like you're right - that's **not** the command line.

Ctrl-Alt-F2 should take you to a screen where you can log in and try the commands that people have given you. Alt-F7 should take you back again.

I guess it's just coincidence that Windows has chosen now to break.

---

### Post by Aquiva on 2006-11-02
Alright, things are starting to work.
I'm going through the all it's questions (when I do the sudo dpkg-reconfigure xserver-xorg command).

Gone through the video card... monitor... resolutions... keyboard... all that
But now I get to the color bit setting - naturally I want the 32-bit (which is the 24 bit) so I select it.

Then down below the command line pops up and wants me to insert something. It says: xserver xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.reconf.20061102153859
and then it wants me to insert something.

I assume the xserver process wants to save the file now that I've told it to be 24 bit. However... it then realizes it is going to overwrite a file... so then the commandline interrupts.

what do I type (I assume to make that backup) so the xserver xorg thing will continue?

 ~ Mark

---

### Post by CatKiller on 2006-11-02
I think that's it. It's done all the configuration, sees there's a file there, makes a backup, saves the file and quits, telling you what it's done.

---

### Post by Aquiva on 2006-11-02
Thank you all! I am finally back on track and alive. :) And I have pretty 1600 x 1200 resolution. (the refresh rate is only 61 though :()

Alright, so I have finally a final question:
I selected the options for it to have 1600 x 1200, 1400 x 1050 (my previous default), 1280 x 1024 and 800 x 600.

...I like 1600 x 1200, but the refresh rate might become irritating (like when I scroll down a page, or move things it is jumpy)
...However, despite the xorg.conf file states it, the system->preferences->resolution still won't recognize 1400 x 1050 (and I assume it has a higher refresh rate than 61hz).

So then...
How do I either:
1. Increase the refresh rate on 1600 x 1200.
But will will high resolution/high refresh rate burn out my LCD?

or

2. Make it recognize my 1400 x 1050? (On windows, this was originally my highest setting).

Thanks! :) (I'll test to see if Windows OS works later :P)

 ~ Mark

---

### Post by CatKiller on 2006-11-02
You're a glutton for punishment aren't you?

You **could** find out the HorizSync and VertRefresh values for your monitor and edit your xorg.conf appropriately. That **may** give you the option of your missing resolution.

---

### Post by nyinge on 2006-11-03
Aquiva,

I believe the refresh rate of 60 is normal on LCDs at your resolutions.  The jumpy thing you mention could be due to lack of proper video drivers.

---

### Post by Aquiva on 2006-11-03
Okay, I have all the details on my moniter, and I re-did my xserver xorg with specific settings. - I even then rebooted.
But it absolutely refuses to give me the setting of "1400 x 1050 60Hz" (which is the optimum and maximum resolution, as stated, on my product details.)

It comes with a driver, but no Linux install. But I don't think I need the driver to get 1400 x 1050 60 hz view.

How come Linux doesn't want to do 1400 x 1050 but it is happy to comply with 1600 x 1200 61hz ?

 ~ Mark

---

### Post by CatKiller on 2006-11-03
> **Aquiva said:**
> How come Linux doesn't want to do 1400 x 1050 but it is happy to comply with 1600 x 1200 61hz ?

That is peculiar. What does your xorg.conf look like now?

Does your /var/log/Xorg.0.log tell you why it's not using that resolution?

---

### Post by Aquiva on 2006-11-03
> Section "Monitor"
	Identifier	"SyncMaster 203B"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel 900"
	Monitor		"SyncMaster 203B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "800x600"
	EndSubSection
EndSection

And um, I can't see any apparent or logical reason in the xorg.0.log
(Note, I have modified the xorg since I inputted in the specifics. At one point it didn't work properly so I reverted back to the closer general settings)

Still no 1400 x 1050 option. :/

 ~ Mark

---

### Post by CatKiller on 2006-11-03
> **Aquiva said:**
> And um, I can't see any apparent or logical reason in the xorg.0.log

It is rather scary-looking. Still, there might have been something.

> (Note, I have modified the xorg since I inputted in the specifics. At one point it didn't work properly so I reverted back to the closer general settings)

Now you're getting the hang of it.

[This page]("http://www.superwarehouse.com/Samsung_SyncMaster_203B_Black_20_LCD_Monitor/203B-BLACK/ps/1487288") suggests that you could have 30-81 as your HorizSync. You could give that a go.

---

### Post by Aquiva on 2006-11-04
Still not working. :/
Anyway that I can just override it all and make the xorg.conf settings be 1400 x 1050 with 60hz?
(note: I'm running my screen on Analog, not digital. Does this cause problems?)

It is a really long file, and I have absolutely no clue what to look for. So just in case your curious here is the first section (till it gets to the hexs)
```
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  3 23:40:31 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster 203B"
(**) |   |-->Device "Intel 900"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
```

Thanks.

 ~ Mark

---

### Post by CatKiller on 2006-11-04
> **Aquiva said:**
> Still not working. :/
Anyway that I can just override it all and make the xorg.conf settings be 1400 x 1050 with 60hz?
(note: I'm running my screen on Analog, not digital. Does this cause problems?)

It doesn't cause problems as far as I know - it just means that you get to put in 30-93 according to that page. I think there are ways to completely override settings, but I don't really know what they are. You can use the IgnoreEDID option in the Device section to  ignore what the monitor is telling the video card, and you can use modelines somewhere. I don't know how that bit works.

It was these kinds of messages that I used when I was having similar resolution problems in the past: > (WW) (1600x1200,Hansol 730E) mode clock 189MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)


---

### Post by Aquiva on 2006-11-04
Some things I found:

```
(II) VESA(0): Not using mode "1400x1050" (no mode of this name)

(II) VESA(0): h_active: 1400  h_sync: 1488  h_sync_end 1632 h_blank_end 1864 h_border: 0
(II) VESA(0): v_active: 1050  v_sync: 1053  v_sync_end 1057 v_blanking: 1089 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 160 MHz

*(WW) (1600x1200,SyncMaster 203B) mode clock 162MHz exceeds DDC maximum 160MHz
```

(Note: I'm trying to obtain 1400x1050 60hz with no lag. 1600x1200 would be nice, however I assume it is bad to use since my monitor doesn't suggest it. [Is it okay to use 1600x1200 even if it isn't suggested?])

Question: Right now I"m on 1280 x 1024 with 76hz. In FireFox when I scroll I get a laggy-refresh feel - so if I scroll a bunch and then stop, it'll still be scrolling. (this is what I'm trying to avoid)
In Word, scrolling down is generally smooth, but scrolling up is laggy.
If I move the position of a window quickly then it'll be laggy. However, if I adjust its size, it is smooth.

What really is my problem?
Is it my refresh rate and resolution?
Is it because I don't have the driver installed? (Note: I e-mailed Samsung and they said they don't give out Linux drivers. How can I possibly get a driver then?)
Or is it simply the applications aren't smooth?

:/

 ~ Mark

---

### Post by CatKiller on 2006-11-04
Are you still using the vesa driver? There are workarounds for Intel integrated graphics, but it's apparently a bit of a pain, and I don't really know anything about them.

LCD monitors look crappy at anything other than their native resolution. It's not really a function of resolution as much as of cell size. Despite the page I linked to claiming differently, Samsung appear to be claiming that 1400x1050 is the native resolution.

I'd try to find out more about my graphics card if I were you, and use the appropriate driver for that. That should sort out your performance issues, and we can look at the reolution afterwards if it is still a problem.

---

### Post by Aquiva on 2006-11-14
Sorry for the long delay, I got busy with school stuff.

Alright, I contacted Samsung and they said they don't offer drivers for Linux. So question, how in the world do I get one?
Yes, I am still using vesa - but I believe I should be using Nividia?
Where do I get drivers for Linux that will make my monitor function correctly?

Thanks.
 ~ Mark

---

### Post by CatKiller on 2006-11-14
> **Aquiva said:**
> Alright, I contacted Samsung and they said they don't offer drivers for Linux. So question, how in the world do I get one?

You don't need one. Ideally, anyway. Windows "monitor drivers" are just registry settings for the information that you are due to put in your xorg.conf file.

> Yes, I am still using vesa - but I believe I should be using Nividia?
Where do I get drivers for Linux that will make my monitor function correctly?

The snippet of your xorg.conf that you posted before says that your graphics device is at least identified in there as "Intel 900". If you are using some kind of integrated Intel thing then you really wouldn't want to use the nVidia driver.

> **CatKiller said:**
> I'd try to find out more about my graphics card if I were you, and use the appropriate driver for that. That should sort out your performance issues, and we can look at the reolution afterwards if it is still a problem.

---

### Post by Aquiva on 2006-11-16
Okay, alright...
Well, it is a Intel Graphics Media Accelerator 900. I really honestly have no clue what type of things I'm looking for. [http://www.intel.com/products/chipsets/gma900/index.htm](http://www.intel.com/products/chipsets/gma900/index.htm) 

And in Intel's download center, I couldn't find any downloads for the gma900? 
Perhaps should I contact Intel's support, rather than you guys? And ask Intel for a gma900 Linux driver?

 ~ Mark

---

