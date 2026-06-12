---
title: "Boots to command prompt only, and how to get Gnome back? plus more..."
date: 2007-03-27
forum: General Help
---

### Post by omega13lives on 2007-03-27
So I am still quite new to Linux and trying to see if I can replace Windows.  I was doing some testing and experimenting as is common in new users, and have run across a few problems and an awful lot of frustration.

I successfully installed Ubuntu as a dual-boot on my Windows XP system which was working fine until I decided to install Kubuntu with the KDE desktop.  That in itself, was not a problem, but I could not find any way to change the screen resolution and decided to uninstall it and then it prompted me to uninstall the kdm and dropped me to a command prompt.  At this point, I wasn't sure what to do so I restarted the computer.  I ended up back at the Kubuntu login screen, which I didn't want, and when I logged in I got the Ubuntu desktop but the Kubuntu log out options.  I would like to keep the KDE desktop as an option, but would prefer to have the Ubuntu started the shutdown screens.  I followed a to edit the startup option and selected gdm instead of kdm.  Now when I startup all I get is the command prompt.  I would like to start with Ubuntu and have the choice of desktops.

Why does it seem virtually impossible to change the screen resolution on my Kubuntu KDE desktop?  And using the control alt + or - simply makes the screen bigger or smaller but does not change the resolution.  I can't find the krandr utility either.

Another problem is, my investment web site creates a (.xls) spreadsheet for download based on a tabular display which normally opens in Excel.  However, when I try to download the link in Linux using Firefox the open office program says it will open it in the spreadsheet application but then opens it in the write application as a document, not a spreadsheet.

Oh yes, I saw the instructions for installing drivers for my Wacom tablet, and it looks daunting to say the least.

There are a number of other daily tasks or programs that I have not yet attempted to duplicate in Linux, and even though I know that many other people use this program, and as much as I hate the Microsoft monopoly, I am beginning to wonder about the cost of "free".  If I charge $80-$100 per hour as many consultants do, my Linux experience costs considerably more than buying a Windows license.  (And even the inflated costs of the new Windows Vista.)

Any help would be appreciated to make my journey less painful.  Note: when I searched the forums for a series of words, I get many results that do not seem to apply at all to my search and would like to be able to restrict the results.  tx

---

### Post by rajan on 2007-03-27
great to see that you're taking the time to learn linux. if you have enough time right away, you'll really start to enjoy it. if you don't, then you'll just see it as a nuisance. 

so in response to a few of  your problems, upon opening something on mozilla, you will usually have the choice of either opening that file with the recommended program that mozilla will show, or you can choose the program that you want to open it with. you probably know this already, but you probably don't know how to figure out which program to use. I would suggest open office calc. you can find out how to access that program by typing in a terminal 

```

which oocalc
```

the output for that line for me is 
```
rajan@paravati:~$ which oocalc
/usr/bin/oocalc
```

using that output, i know that the program open office calc is in the bin subfolder of the /usr directory. you just need to browse for that program now, and since you know where it is, you should be able to find it easily. 



your screen resolution problem sounds like something went wrong during the installation. you can fix this by editing (carefully) your /etc/X11/xorg.conf file (or whatever your system calls it). it will have a bunch of lines like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"CPD-E200"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

and those lines tell your computer what your monitor is capable of. I would strongly suggest you look into this independently, partially because i don't know enough to give you specific advice. 

anyways, good luck and i hope those things help,

rajan

---

### Post by omega13lives on 2007-03-27
Thank you for offering a reply, however, the information you gave doesn't seem to offer any solutions or actions to take except to look at something.  I already found the file listing the screen resolutions, but I have not found the display settings in the KDE desktop where I can change the resolution.  Secondly, I don't understand why you are telling me to look for the calculator, when I am already being prompted to open the Internet file with the spreadsheet program, which is what I want, but then it opens up in the write program instead.  I also need to figure out how to get the desktop launched again from the command line, and then determined why GDM did not launched at all.

---

### Post by omega13lives on 2007-03-28
I got the Ubuntu usplash screens back and the gdm.  I am trying to fix the pre-usplash boot screen now which says Kubuntu.  Also trying to change usplash screen resolution.

any ideas on the .xls spreadsheet problem?  or how to change KDE resolution in Ubuntu?  tx

---

### Post by rajan on 2007-03-28
oocalc : MS excel :: ubuntu : MS office

i hope you like SAT analogies.


i dont' have kubuntu, but in my regular ubuntu i go to the system tab, then to screen resolution, where you will find the options in the drop-down menu that are in the /etc file that you now know how to find. if need be, you need to edit this file by opening it with root access. since i use emacs, i would type 

```

gksudo emacs /etc/X11/xorg.conf
```

but you can replace emacs with your favorite text editor (you might want to try "gedit"). the "gksudo" gives you root priveledges (after entering your passwd).

the reason that I don't want to tell you how to edit your xorg.conf file is that if you edit it incorrectly, you can damage your monitor. this is a problem that you have to solve yourself by googling because it's unlikely that someone else has the same exact system as you do.



as far as you being unable to boot into a xterm session, i am not sure how that happens. have you tried hitting <control> + <alt> + <f7>? this should toggle you to a different login terminal that linux has by default several of. you may need to find the correct one by replacing <f7> above with the other f-keys. otherwise it seems that your grub is working fine (as evidenced by the splash) but your kernel isn't taking the handoff correctly.

---

### Post by omega13lives on 2007-03-28
I appreciate your desire to assist, but as you say, you don't use kde or kubuntu so you can't tell me how to change the resolution.  You also suggest I might edit the xorg.conf file (which I have seen) but don't say why or how.  You also say you don't know how I am unable to boot into xterm.  How does any of this help me?

---

### Post by AndyCooll on 2007-03-28
> **omega13lives said:**
> I appreciate your desire to assist, but as you say, you don't use kde or kubuntu so you can't tell me how to change the resolution.  You also suggest I might edit the xorg.conf file (which I have seen) but don't say why or how.  You also say you don't know how I am unable to boot into xterm.  How does any of this help me?

With regard to your screen resolution issue, it is likely that on setup all the possible settings for your graphics card and monitor weren't properly detected, so you are going to have to manually edit the relevent file and add the required resolutions. Resolution settings are kept in xorg.conf. So type the following into a terminal:
```
sudo kate /etc/X11/xorg.conf 
```

About two thirds of the way down that file is the section "Screen". Now manually add additional screen resolutions so that it looks like the one posted by rajan. Save the file and reboot. The additional resolutions you typed in to xorg.conf should now be available.

:cool:

---

