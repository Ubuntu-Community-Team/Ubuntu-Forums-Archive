---
title: "Frequency out of range problem v2"
date: 2006-10-28
forum: General Help
---

### Post by gcamilo on 2006-10-28
I just updated to Edgy, and I'm having the Frequency Out Of Range monitor problem. I followed the reconfigure xserver-xorg command, to no avail. My monitor is an LCD with a native resolution of 1280*1024, and according to [this page](http://support.gateway.com/s/MONITOR/7005425/7005425cp.shtml) I set my frequency to Horizontal 60-70 and Vertical 70-75.

I would like to note that when I first installed ubuntu, I tried with the Edgy release candidate, and this same thing happened, but when I put Dapper on, no problems. Could this be related to a kernel thing?

Thanks for your suggestions.

---

### Post by vibestriton on 2006-10-28
Just a thought... Have you tried adding a custom modeline to end of the Monitor section of your xorg.conf file? 

Does this work?

Modeline "1280x1024"   108   1280 1328 1440 1688   1024 1025 1028 1066  +hsync +vsync

---

### Post by gcamilo on 2006-10-30
I tried it and it didn't work. But now after a while it displays the ubuntu login menu. But when I login, it displays the booting menu with the autostart programs, and then it just stalls there with the beige screen, no Gnome panels or anything.

I tried to reinstall Ubuntu 6.10 completely by CD, but when I select the Start and Install Ubuntu from the menu, and after it loads completely, it displays Frequency Out of Range warning again, but this time without any change indefinitely. Any help?

---

### Post by gcamilo on 2006-10-30
When I load the Failsafe Gnome Session I get this errors:

```

"There was an error starting the GNOME Settings Daemon. Some things, such as themes, sounds or background settings may not work correctly. 

The Last error message was: 
Unable to launch the address of the message bus (try man dbus-launch or man dbus-daemon for help). Gnome will try to restart the Settings Daemon next time you login."
```

Also another screen next to it says:

```

"I've detected a panel already running, and will now exit."
```

What can I do to get my ubuntu working again? I rebuilt the modeline myself, to no effect. My [ xorg.conf is available here.](http://www.gcamilo.com/xorg.conf) Again, using [this page](http://support.gateway.com/s/MONITOR/7005425/7005425cp.shtml) as reference. Remember my monitor is a generic Gateway LCD.	

        HorizSync	30-80
	VertRefresh	60-75

---

### Post by CatKiller on 2006-10-30
You could keep running Dapper instead.

Or you could try taking the refresh ranges down a notch in xorg.conf, since you haven't been able to accurately identify what they should be for your model.

Or you could check /var/log/Xorg.0.log to see if that says why it's not using appropriate ranges for your monitor.

---

