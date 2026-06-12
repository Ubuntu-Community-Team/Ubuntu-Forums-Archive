---
title: "Unwanted Programs at Startup"
date: 2014-01-06
forum: General Help
---

### Post by de Bacon on 2014-01-06
I am experiencing something different, and unwanted.  I don't know why it started or how to correct this.  After boot, and login, two programs automatically start up,  Mozilla web browser and a Terminal Emulator.  

Where and how, do I change settings that will stop this from happening?

Thanks in advance.

---

### Post by btrix2 on 2014-01-07
click on settings button on upper right hand corner >> then in startup application >> a window should open check if mozilla is checked if yes uncheck it. done same with other programs. 

hope this helps.

---

### Post by de Bacon on 2014-01-07
I take it that what you are referring to is a part of unity, but I don't run unity and thus the menu doesn't offer what you refer to.  I have looked through the settings options in "Settings Manager" but there is nothing in there that will change anything on startup.  I have also found that changing the settings in some items only lasts as long as the session, then reverts back to its original settings at boot, ie screensaver.

thanks for the thought though.

---

### Post by ibjsb4 on 2014-01-07
Try this

Open a terminal and enter

```
gnome-session-properties
```

---

### Post by Bucky Ball on 2014-01-08
Well, might be an idea if you tell us exactly what you are running (presuming UStudio with xfce4 but please confirm). 

Anyway, could be as simple as this. When you click the shutdown icon a window pops up with 'Log out, reboot, shutdown' etc. There is a little tick box which asks if you want to 'save session for future logins' so it boots up exactly as you left it. Make sure that is unticked.

So, close all programs, go for a reboot, make sure the 'save session' is unticked, reboot.

---

### Post by vasa1 on 2014-01-08
> **de Bacon said:**
> I take it that what you are referring to is a part of unity, **but I don't run unity** and thus the menu doesn't offer what you refer to.  I have looked through the settings options in "Settings Manager" but there is nothing in there that will change anything on startup.  I have also found that changing the settings in some items only lasts as long as the session, then reverts back to its original settings at boot, ie screensaver.

thanks for the thought though.
So what do you run? Sharing that information may help people help you :)

---

### Post by xeonix on 2014-01-08
You can also check at *~/.confg/autostart *directory and delete all those applications with *rm* command.

---

### Post by de Bacon on 2014-01-08
Thanks for the responses!
=============================
ibjsb4,
I went ahead and looked into your suggestion.  In the Startup Applications Preferences box, there is a list of four items:
No name
NVIDIA X Server Settings
Power Manager
XFCE Volume Daemon

When using the edit button after selecting "No name"  the popup is empty of all content where there are available input spaces for, name, command, comment.

I would not know what to put in any of them or how to verify that their content is correct.
===============================

Bucky Ball,

I am running Ubuntu Studio 12.04 with xfce.

There is not a little tick box when I shut down.  It goes to a countdown warning, 30 seconds or confirm, is all that it shows.

=========================

xeonix,

I don't know what you mean.  The tilda (~) doesn't mean anything to me!
==========================

This thing is getting weirder now.  Both last night and this morning it happened.  I had shut down Firefox, then later wanting to look up something more, when trying to open Firefox, a message popped up, Firefox is already running....   I had to mechanically shut it off the only way I know how, through "System Monitor".  That resolves the problem at least for the duration of the session (I think).

I realize I didn't provide much assistance here, but I really don't know much more.

Thanks

---

