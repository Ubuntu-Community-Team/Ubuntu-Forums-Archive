---
title: "Free Games: Help with ATI driver X800pro"
date: 2007-10-24
forum: General Help
---

### Post by Ubuntoob on 2007-10-24
Hi all. I'm loving Ubuntu 7.10. (I've switched from the latest Suse)
I have an x800pro ATi graphics card and having trouble installing the driver.
Many references online but many differ. Aware of a bug logged and not officially fixed for some of these issues.

I'd love to get the driver installed properly so I can run custom effects with compiz fusion etc. Then tidy it all up as opposed to waiting for reinstall after reinstall to cleanly attempt the driver install again.

If anyone can point me to a reference from experience that works for the X800 pro cards - I can send some old games on official original cds to wherever you are.

Games include: UT2003, Soldier of Fortune 2 Double Helix, Comanche 4, Half Life counter Strike (the original one) and Rainbow Six Three Raven shield.

Needless to say I don't play these games and I'm loving Ubuntu. I'm off to work but if you have the time -  I have the decency to mail the games.

Cheers all. Grant.

---

### Post by Ubuntoob on 2007-10-26
Bump.

I know there is no official fix yet so I'll just wait.

In the meantime - Christmas is coming for all those who care.

If you want the said games - pm me with an address and I'll mail them. (1st come 1st served)

They are original cd's with original serials etc. But no CD cases as I use a CD folder.

All the Best Ubuntu peeps.

Grant. :guitar:

---

### Post by Can+~ on 2007-10-26
I have a X800 GTO2 running with compiz fusion with XGL, after a lot of work.

I did the following:
-Installed XGL
> sudo apt-get install xserver-xgl

-Installed FGLRX with the restricted driver manager.

-I rebooted as asked, but xorg was dead, so I jumped to the terminal (Ctrl+Alt+F1 (or any to F6))
> sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

-And rebooted again
> sudo shutdown -r

-The monitor didn't respond, so I jumped again to the terminal, and opened xorg.conf
> sudo nano /etc/X11/xorg.conf

-And added my resolution to the file, Section "screen" > SubSection "Display":
> 		Modes		"1280x1024@60" "1024x768@60" "800x600@60"
(I'm using an LCD screen)

-Added the fglrx to the white list of the compiz-fusion manager:
> gksudo gedit /etc/xdg/compiz/compiz-manager &

Then paste this inside:
> WHITELIST="nvidia intel ati radeon i810 fglrx"


-This time xorg started without 3d effects. So I had to enable them, I opened xorg.conf with terminal:
> gksudo gedit /etc/X11/xorg.conf &

-Added the following to the end:
> 
Section "ServerFlags"
        Option "AIGLX" "off"
EndSection
Section "DRI"
	Mode 0666
EndSection

-And set the "OpenGL overlay on", and the other one off:
> 	Option "VideoOverlay" "off"
	Option "OpenGLOverlay" "on"

-And if this is disabled, enable it!:
> Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

I rebooted again, and it worked. Dunno if it's gonna help you; the last FGLRX supports AIGLX, but XGL is good enough for me. Here are some other posts if this doesn't work:
[http://ubuntuforums.org/search.php?searchid=29907175](http://ubuntuforums.org/search.php?searchid=29907175)

By the way, I'm not interested on the "free games". So, keep'em to yourself. Besides, I live in Chile ;P

---

### Post by Ubuntoob on 2007-10-27
Cheers dude!

I'm just going to wait for an official fix or update cos I don't want to reinstall now after trying to get this system as I want it.

Thanks for posting all that stuff.

Chile would be no problem. I don't care where I send the cd's or how far.

Giving can be much more rewarding than counting the pennies.

Just say the word if you did or do want them. Or anyone else etc. (PM)

Cheers, Grant.

---

