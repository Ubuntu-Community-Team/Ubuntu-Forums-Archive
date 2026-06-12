---
title: "nvidia x server settings - loading user configuration?"
date: 2019-02-07
forum: General Help
---

### Post by jfca283 on 2019-02-07
Hello, 
I have no problems with Nvidia X server settings.
I use two monitors as I wish.
The issue is that every time I turn on the PC I need to go to the nvidia app and set manually the configuration.
How can I save it and load it automatically when I start my session?
Thanks for your help, interest, and time.

---

### Post by TheFu on 2019-02-08
I'd like to know this too!   The nvidia-setup/settings app doesn't seem to be able to load previously save setting files.  nVidia says that running **/usr/bin/nvidia-settings --load-config-only** should work, if the default file is used, but it doesn't.  The default filename is ~/.nvidia-settings-rc

Some settings can be configured in the xorg.conf file. There is a manpage for that.  I put mine into /etc/X11/xorg.conf.d/20-nvidia.conf so it won't be touched by updates.  You don't need to specify a full config file, just enough to ensure nvidia driver is used and whatever settings need to be non-default.

In the last few weeks, I've had to manually create a complete config file to get an unknown monitor and a GT 1030 to send exactly the correct information to it.  I suspect what you seek is much easier.

---

### Post by jfca283 on 2019-02-08
I save a config file using the Nvidia app. Where do I need to put this config file in order to avoid using the nvidia settings?

---

### Post by CatKiller on 2019-02-08
> **jfca283 said:**
> The issue is that every time I turn on the PC I need to go to the nvidia app and set manually the configuration.
How can I save it and load it automatically when I start my session?

> **TheFu said:**
> I'd like to know this too!   The nvidia-setup/settings app doesn't seem to be able to load previously save setting files.  nVidia says that running **/usr/bin/nvidia-settings --load-config-only** should work, if the default file is used, but it doesn't.  The default filename is ~/.nvidia-settings-rc

It does work, but it isn't applied automatically, and you can't specify with that file all of the settings that are available in the GUI tool. If the settings you want to change *are* ones that can be specified in that file it is simple to add ```
nvidia-settings --load-config-only
``` to the startup applications list of whichever desktop environment you're using. That way they'll be applied every time you log in.

Otherwise, you can adjust other settings with the nvidia-settings command line tool. For example, with coolbits you can adjust clock speeds in the GUI tool, but you can't use .nvidia-settings-rc for that. So when I want to overclock my graphics card, I use this script: ```
#!/bin/sh

nvidia-settings -a [GPU:0]/GPUMemoryTransferRateOffset[4]=1000
nvidia-settings -a [GPU:0]/GPUGraphicsClockOffset[4]=100
exit 0
``` and when I want to set the speeds back to normal I use this script: ```
#!/bin/sh

nvidia-settings -a [GPU:0]/GPUMemoryTransferRateOffset[4]=0
nvidia-settings -a [GPU:0]/GPUGraphicsClockOffset[4]=0
exit 0
```

Some settings may be adjusted that aren't exposed through either the GUI tool or the command line tool, but require the use of the System Management Interface. For example, to adjust the power limit of my graphics card, I can use ```
nvidia-smi --power-limit=290
```

> **TheFu said:**
> In the last few weeks, I've had to manually create  a complete config file to get an unknown monitor and a GT 1030 to send  exactly the correct information to it.

When a monitor isn't providing enough information to allow its resolution to be automatically detected, xorg.conf *is* the appropriate place for those settings. You want the resolution to be correct for all users, and on the login screen.

---

### Post by TheFu on 2019-02-08
> **CatKiller said:**
> It does work, but it isn't applied automatically, and you can't specify with that file all of the settings that are available in the GUI tool. If the settings you want to change *are* ones that can be specified in that file it is simple to add ```
nvidia-settings --load-config-only
``` to the startup applications list of whichever desktop environment you're using. That way they'll be applied every time you log in. 
It didn't control the gamma values in my attempts.  Might have been user error, but ...   I didn't try the CLI interface.

> **CatKiller said:**
> 
When a monitor isn't providing enough information to allow its resolution to be automatically detected, xorg.conf *is* the appropriate place for those settings. You want the resolution to be correct for all users, and on the login screen. 

I left out a few details ... like the active DVI-D to VGA adaptor being used and that the adaptor wasn't providing correct EDID for the resolution  the monitor used natively. Also, the KVM switch being used wasn't mentioned...  

But didn't want to side-track this thread too much.

---

### Post by CatKiller on 2019-02-08
> **TheFu said:**
> like the active DVI-D to VGA adaptor being used and that the adaptor wasn't providing correct EDID for the resolution  the monitor used natively. Also, the KVM switch being used wasn't mentioned... 

Yep, figured it was something like that. EDID is magic when it works, but annoying when it doesn't or can't. The real stinker is when there *is* EDID, but it's full of lies. Such a pain.

My main point was that the solution you're using, far from being a workaround, is the best way to do that. FWIW, you *should* be able to specify gamma values in the rc file, per display. You can also specify them per Monitor in xorg.conf.

As you say, best not to wander too far off topic. The OP should be able to automatically apply whichever settings it is that they're interested in, either through the rc file, or through nvidia-settings, or via the driver itself in xorg.conf.

---

