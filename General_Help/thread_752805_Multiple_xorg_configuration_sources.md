---
title: "Multiple xorg configuration sources?"
date: 2008-04-12
forum: General Help
---

### Post by undecidable on 2008-04-12
My (/etc/X11/) xorg.conf has the following 6 lines setting up 6 font paths:

Section "Files"
	# path to defoma fonts
    FontPath 	"/usr/share/fonts/X11/misc"
    FontPath 	"/usr/share/fonts/X11/100dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/75dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/Type1"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/usr/local/share/fonts"
EndSection


But in Xorg.0.log near the beginning I see those 6 font paths then 10 more! :

(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi:unscaled,
	/usr/share/fonts/X11/75dpi:unscaled,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/local/share/fonts,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,		
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,		
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType

and some of these don't exist, so near the end of xorg.0.log I see
three error messages re fonts from the additional 10:

Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

Where are the requests for these extra 10 fonts coming from?
Is there some other configuration file that X uses apart from my xorg.conf

I am using Feisty Fawn.

thanks for any clues.

---

### Post by warp99 on 2008-04-12
No those are just coded into xserver to look for those font paths during startup. If it doesn't find the directories then xserver does a  *removing from list!*

---

### Post by undecidable on 2008-04-12
warp99

Thanks.  In fact I have 7.04 Ub on one partition and 7.04 Kubuntu on another, using separate home directories (am testing Ub prior to migration).   I just checked that while the font paths specified in xorg.conf are slightly different, the extra 10 added are the same, and further, the 3 errors at bottom (ie paths removed from list) are the same.  So, you are clearly correct!

Do you happen to know where these extra 10 are specified?  It seems unlikely they would be hardcoded into code itself.

---

### Post by warp99 on 2008-04-12
According to the xorg wiki the error is because xorg is looking for a font server:

> Somewhere (pretty much at the beginning of the log) there is a message:

 Could not init font path element unix/:7100, removing from list!

This message tells that the Xserver is trying to contact a font server which appearantly isn't running. So you need to get your font server up and running before you start X. How this is done depends heavily on the OS and/or the distribution you use. Please contact your vendor support on how to do this!

[http://www.x.org/wiki/FAQErrorMessages](http://www.x.org/wiki/FAQErrorMessages)

So it appears that the Ubuntu developers have enabled by default that xorg look for a font server on startup. Since none is installed it returns the error message.

---

### Post by soxs on 2008-04-12
thx, helped me a lot debbuging my system :-P

---

### Post by undecidable on 2008-04-12
warp99
thanks for the link - very informative.

However I don't think this is related to my issue.  I have no such err msg, and none even remotely like it.  In fact no other X err msgs apart from DRI not enabled.   Also all my fonts work fine  (I have added LIberation fonts and Chinese fonts and can use them both from KDE and froml egacy X apps). 

mc

---

