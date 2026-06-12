---
title: "Ubuntu 5.04 Live CD - huge screen resolution - tiny print - unusable"
date: 2005-05-19
forum: General Help
---

### Post by Three on 2005-05-19
- Ubuntu Live CD Screen Resolution Problem -

Hardware: Celeron 1 GHz, Radeon 7500 64 MB PCI card, Gigabyte motherboard with integrated video (overridden in the BIOS to use the Radeon 7500 PCI video card, instead), Samsung SyncMaster 957 19" CRT monitor (Horizontal: 30-96 kHz, Vertical: 50-160 Hz), 384 MB RAM.

I have been trying to deal with the problem of an excessive screen resolution with the Live Ubuntu 5.04 CD.  I would  guess that X is coming up as 1920X1440 at 85 MHz - the maximum that my video card is capable of producing.  Far too tiny to read the print.  None of the flickering that I would see at 65 Hz.

I am not given a choice on boot-up to set the screen resolution.  I see no option to set the screen resolution on the "expert" boot options on booting up the Live Ubuntu 5.04 CD.

The initial boot-up messages - white on black background as the OS is going through the boot routine - are all readable and fine.  Once X comes in, however, I get a large brown screen with tiny, unreadable letters. I am unable to troublshoot further - i.e., i cannot get into the X config files - because I cannot read whatever print  is on the screen, even wtih a 5 inch magnifying glass - the letters are then just a tiny blur.

Are there any Ubuntu boot codes that will solve this problem?

The Knoppix boot codes that I routinely use - << xmodule=radeon >> and << screen=1024X768 >> (or 1280X1024) - do not work with the Live Ubuntu 5.04 CD.

The Mepis boot code that I routinely use << xdrvr=radeon >> does not work with the Live Ubuntu 5.04 CD.

I have searched several Ubuntu fora and I have not found an answer to this problem.  Fixes posted for the installed version of Ubuntu such as << live dpkg-reconfig xserver-xorg >> do not have any effect when I type them on booting the Live Ubuntu 5.04 CD.

This computer works fine with Mepis 3.3 with the << xdrvr=radeon >> boot code - Live CD and Mepis 3.3 installed to the hard drive. 

This computer works fine with KNOPPIX 3.8.1  with the << xmodule=radeon >> boot code -  Live CD and  installed to the hard drive. 

This computer works fine with Red Hat 8, Red Hat 9 and Fedora Core 1 with no special boot code - installed to the hard drive. 

It is just the Live Ubuntu CD that doesn't work.

Any suggestions?


I write this to you from this computer with a Knoppix 3.8.1 hard drive install.

None of the Knoppix cheat codes I have tried work with the Live Ubuntu CD.


Thank you,

Three

---

### Post by fackamato on 2005-05-20
Have you tried changing the resolution with control+alt+minus/plus (on the numpad) ?

---

### Post by Three on 2005-05-21
[quote=]Have you tried changing the resolution with control+alt+minus/plus (on the numpad) ?[/quote]
fackamato,

Partial success!

Thank you!


Clicking control+alt+plus once magnfied the desktop a little bit - but the menu bar on the top of the screen completely disappeared.

Clicking control+alt+plus a second time magnified the desktop a little bit more - but the menu bar on the bottom of the screen completely disappeared, as well.

Clicking a total of seven times kept enlarging the "ubuntu" on the desktop, but with the top and bottom menu bars gone, ubuntu appeared to be unusable. Not way to access any programs. No scroll bars for navigaon.

Up and down arrows did no good for navigation.

Taking the mouse cursor and putting it at the top of the screen did allow me to navigate to the upper menu bar, however. There, using System > Preferences > Screen Resolution, I was able to bring the screen resolution down from the unreadable 1920X1440 at 60 Hz it was on to 1024X768 at 85 Hz, and I am now writing this from a standard, usable Ubuntu desktop in Firefox.

How do I alert the Ubuntu development people of this glitch?

glxgears runs at 337 - it normally runs at 377 on multiple other distributions.

glxinfo indicates that DRI is enabled.

Looking at /etc/x11/xorg.conf, I see that the "ati" driver is being used. It is my experience on all other distributions that I have encountered that the "radeon" driver is preferred for my card. I have tried to change this to the "radeon" driver in /etc/x11/xorg.conf, but I cannot seem to do so on the basis that I do not have the appropriate permissions to change the file.

To gain permission for such changes, I usually work as root in the gui. I do not see how to do this in Ubuntu, and am not used to accessing files from the command line. How can I gain permission to change the driver file from "ati" to "radeon" in /etc/x11/xorg.conf with the Ubuntu Live CD?


Thanks again,

Three

---

### Post by SSTwinrova on 2005-05-21
Have you looked to see if there is something that will let you open/edit a file as root in the context menu (right-click) for the file?

If there isn't, you can use: "sudo (insert favorite editor) /etc/x11/xorg.conf" (sans quotes) at the command line.

---

### Post by Three on 2005-05-21
> Have you looked to see if there is something that will let you open/edit a file as root in the context menu (right-click) for the file? 
I just tried doing so as per your suggestion.

No joy.

> If there isn't, you can use: "sudo (insert favorite editor) /etc/x11/xorg.conf" (sans quotes) at the command line. 
This worked!

Thank you, SSTwinrova!


Summing up my first experience with a Live Ubuntu CD:

The Ubuntu Live CD looks like it could use some more work. The programmers might want to consider looking at what other live CDs do right - e.g., Knoppix and Mepis - in areas where things seem to be much more difficult with the Live Ubuntu CD.

Now that the Live Ubuntu CD is accessible, it looks like an interesting distribution which will, after a bit of a struggle, work on this machine.  

I plan to install Ubuntu - not because of the quality of the Live Ubuntu CD, which has its flaws - but because of the quality of the community help that I have encountered here.

In the process of learning how to access the Live Ubuntu CD I have learned how to change magnifications on Debian-derivative distributions by a simple keyboard shortcut, I have learned how to edit Linux files from the command line, I have learned a bit about using "sudo" instead of using "root," and I have learned how helpful the online Ubuntu community can be.

This effort has turned out very well.


Thank you, All,

Three

---

### Post by britbrian on 2005-05-22
Three

I'm not sure if the last post solved your problem but it seems familiar. My monitor does'nt report its resolution to the X-server so  KDE's KControl->Info->X-Server was reporting my 19" monitor as 22.5" and set my font res to 75dpi. Curiously I only had the problem in KDE while Gnome was correct regardless of distribution but I don't know if that detail applies to others.

This post   [http://www.ubuntuforums.org/showthread.php?t=20976&highlight=pixel](http://www.ubuntuforums.org/showthread.php?t=20976&highlight=pixel) suggested adding this at the end of Section "Monitor" in xorg.conf and then to uncomment the desired line:-

#	DisplaySize     270  203  # 1024x768   96dpi
#	DisplaySize     304  228  # 1152x864   96dpi
	 DisplaySize     338   270  # 1280x1024  96dpi
#	DisplaySize     370   277  # 1400x1050  96dpi
#	DisplaySize	423   370  # 1600x1400  96dpi

For me Kcontrol->Info->X-Sserver now reports 370x277 and dpi as 96 so now 10pt fonts look great.
You could also search for either DisplaySize or xdpyinfo and find you more posts.
Good luck

---

### Post by xmastree on 2005-05-29
> 
Clicking control+alt+plus once magnfied the desktop a little bit - but the menu bar on the top of the screen completely disappeared.

Clicking control+alt+plus a second time magnified the desktop a little bit more - but the menu bar on the bottom of the screen completely disappeared, as well.

Clicking a total of seven times kept enlarging the "ubuntu" on the desktop, but with the top and bottom menu bars gone, ubuntu appeared to be unusable. Not way to access any programs. No scroll bars for navigaon.I'm surprised no-one commented on this...

When you magnify the desktop like that, it's all still there, menu bars and everything, but your screen shows only part of it.

If you push the cursor past the edges of the screen, you can scroll around the whole thing.

---

