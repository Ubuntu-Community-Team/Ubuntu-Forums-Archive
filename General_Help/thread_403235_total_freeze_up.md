---
title: "total freeze up"
date: 2007-04-06
forum: General Help
---

### Post by leveliv on 2007-04-06
hi I am running 6.06  and I have the Nvidia drivers installed for my 6200TC card...and whenever I boot up its all good till I am 5 mins into doing something...so on start up I open firefox...get to a website...read something thats interesting then it freezes :|

---

### Post by leveliv on 2007-04-06
I did a little test and...I uninstalled my nvidia drivers...and rebooted..it worked fine with no flaws...then I installed them again and it froze...right on the GDM welcome screen :| how do I fix this?

---

### Post by llamakc on 2007-04-06
Determine which version of the NVidia drivers you're using, and let us know how you installed them.

---

### Post by Kedma on 2007-04-06
I have somthing like this.. I get to the login screen, and enter info.. then it freezes..  Fresh install of 6.10 from alternate cd.. couldnt get either 32 or 64 lives to work..  its the 32bit alternate cd.

---

### Post by xphelanx on 2007-04-06
I am having a similar problem, however mine takes a little longer than that unless I go into a graphics intensive program such as Nexuiz or OpenArena in which case, I get a good 2-3 minutes of playtime out of it before I'll just lock up. Can't restart X, nothing. Just have to hit reset. I have tracked possibly pertinent information at this link:
[http://www.nvnews.net/vbulletin/showthread.php?t=58498]("http://www.nvnews.net/vbulletin/showthread.php?t=58498")
I believe this applies to me as I am running a Core2Duo (referring to the booting with the idle=poll kernel parameter) I have not tried this as of yet because I'm not sure where to plug this little dandy into a config file or what in order to get it to work. Maybe this also applies to your issue?

Note: I seem to be running with the default 'nv' driver just fine right now. I just changed it from 'nvidia' in my xorg.conf file.

---

### Post by leveliv on 2007-04-07
I installed them using Automatix2 so I am guessing they are the newest ones out there. thanks for your replies :) I was down to think that no one knew what to do but I can't really get into ubuntu to see what version of drivers I have cuz of the freezing, I am going to try in Recovery Mode

---

### Post by FuturePilot on 2007-04-07
If you have```
Option "RenderAccel" "true"
``` in your xorg.conf either comment it out or remove it all together. Then restart x. I was having freezing problems with the Nvidia driver and once I removed that line, it hasn't frozen up since. The onces from Automatix are the same ones in the Ubuntu repos and the ones for Dapper are pretty old.

---

### Post by leveliv on 2007-04-07
I can't even get into ubuntu it freezes at the welcome screen :| is there a way I can start the X server with VESA not Nvidia..
I was using > sudo cp /etc/X11/xorg.conf_backup200704061344 /etc/X11/xorg.conf
but it doesnt work anymore cuz I reinstalled the drivers since then so the numbers on the end are different but I dunno what they are...

---

### Post by leveliv on 2007-04-07
here I am, re installing :| I have never had this problem with Ubuntu before (I just started using ATI and Nvidia Drivers) I never used to use them. so now I will re install then probably not install them, seeing that they don't wanna work for me =)

---

### Post by FuturePilot on 2007-04-07
If you have the problem again just <Ctrl><Alt>F2 to get to the command line when the login screen appears, sign in then do ```
sudo nano -w /etc/X11/xorg.conf
``` then comment out the RenderAccel line <Ctrl>X to exit, Y to save then hit Enter. Then type exit to sign out then <Ctrl><Alt>F7 to get back to the login. Then restart X by <Ctrl><Alt><Backspace>. Now you can sign in normally and it shouldn't freeze.

---

### Post by leveliv on 2007-04-08
thanks I will try that...

---

