---
title: "Bought a new monitor and it doesn't show the Ubuntu loading anymore.. What can I do?"
date: 2007-12-22
forum: General Help
---

### Post by mmilitia9 on 2007-12-22
Hey guys!

I recently purchased a new 20' monitor because my other monitor died out.  Anyway, everything works fine with Ubuntu.  It's labeled as "Plug and Play" because I couldn't find the Westinghouse brand in the menu.  Anyway, the only problem I have with the monitor is when Ubuntu is loading up.. I dont see ubuntu and the loading bar.. my monitor at that time says like.. "No signal" until it boots into logon screen.  What can i do to correct this?

Thanks

---

### Post by ijason on 2007-12-22
it doesn't show any of the BIOS loading or device pool loading or anything? just 'no signal' until you get to the log-on screen?

---

### Post by mmilitia9 on 2007-12-22
Everything is fine.  Grub displays.. everything displays.  I choose Ubuntu to load... and then when I'm supposed to be seeing Ubuntu(with loading screen) I don't... Monitor is blank with a "no output" sign.. and then it'll finally pop up to the login screen.

---

### Post by ijason on 2007-12-22
ah. so it's just once you actually start ubuntu booting that it loses signal. 

my original thought would be that it might be a setting in the xorg.conf (er... assuming gutsy still uses xorg? i'm more familiar with fiesty). but since you're getting a 'no signal' error it sounds like the video-card stops sending signal to the monitor... not that the monitor can't understand the signal it's receiving.

are you using the digial cable or the old VGA cable? maybe ubuntu has to load far enough along to pull up the proper digital drivers to run the signal? i'm really not sure. :confused:

---

### Post by mmilitia9 on 2007-12-22
Old VGA.  I don't know if it changed anything in my xorg.conf file.  Maybe I need to edit something out?  dunno..

---

### Post by ijason on 2007-12-22
the only thing that i think would change in the xorg.conf is needing to be sure that the new screen's resolutions are listed, but since it works fine once ubuntu is starting, clearly that's not the problem. 

i'm not sure what the problem is! you may be able to get some good advice in searching for other 'splash screen' type threads. good luck!

---

