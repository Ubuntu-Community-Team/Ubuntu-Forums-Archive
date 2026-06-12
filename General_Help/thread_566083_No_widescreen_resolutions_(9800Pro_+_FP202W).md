---
title: "No widescreen resolutions (9800Pro + FP202W)"
date: 2007-10-03
forum: General Help
---

### Post by mjw21a on 2007-10-03
I've recently taken the plunge and installed UBuntu Linux 7.04 (32 bit, tried 64 and found it buggy - 32 was faster).

I've just got one rather annoying issue. After installing it was showing ghosting, I figured this was a driver issue (which it was) and UBuntu happily updated to the listed "restricted" driver for my 9800Pro.

Thing is, the only screen resolutions the system lists are 800x600, 1024x768 and 1280x1024. Problem is my monitor is a widescreen. Is there any way I can get this to run in a widescreen mode.

Please keep in mind that I'm a Linux noob so the simpler the answer the better.

Thansk in advance guys. :)

---

### Post by superyounan1 on 2007-10-03
you ought to be able to add a custom screen resolution right into your xorg.conf file, but fiddling with that file can kill your display. If that happens, ubuntu will have you reconfigure x, or if you just get a shell with no display, run this to invoke reconfiguring yoru display:
```
dpkg-reconfigure xserver-xorg
``` 

so basically you want to edit your xorg.conf file
```
sudo gedit /etc/X11/xorg.conf
```

find the "Screen" section, should look like this:
```

Section "Screen"
...
...
...
EndSection

```

inside you'll see a bunch of subsections, one for each bit-depth. heres what one of these looks like in my xorg.conf:
```
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
```

add in your screen's native resolution into the mix, so if yoru screen is 1440x900, change it from what is above to :
```

	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

```

and do the same for all the bit depth subsections, you'll probably have 6 of them, (1,4,8,15,16,24), you might have 32, but i don't, and i'm running a 9800 AiW pro.

Anyway, make the changes, save, and restart X
```
CTRL+ALT+BACKSPACE
``` 

or log out, or restart the computer.

then log back in and see if you have the right resolution now, if not, go to System > Preferences > Screen Resolution and see if the new resolution is available.


I'm sure this is a heavily discussed topic, If my advice doesn't help, try digging through the forums, you're definitely not the first person with that issue.

---

### Post by superyounan1 on 2007-10-03
or wait a couple weeks and upgrade to Gutsy, its going to have a GUI for editing xorg.conf

---

### Post by dcstar on 2007-10-03
> **superyounan1 said:**
> 
.........
I'm sure this is a heavily discussed topic, If my advice doesn't help, try digging through the forums, you're definitely not the first person with that issue.

Yep, some older video cards need "tweaking" of the xorg.conf file, and there are numerous posts in the forum about how to do it all.

---

