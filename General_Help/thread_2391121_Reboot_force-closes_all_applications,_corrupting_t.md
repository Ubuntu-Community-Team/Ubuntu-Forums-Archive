---
title: "Reboot force-closes all applications, corrupting them!"
date: 2018-05-06
forum: General Help
---

### Post by feijoa-boa on 2018-05-06
Hi there,

Every time I reboot, using the reboot button in the GUI, it seems to force-close everything. eg Firefox and Chrome will tell me they were improperly shut down and won't reload my tabs from last time, and any hard drives I had mounted with Veracrypt now have corruption if writes were in progress. This doesn't happen on Windows or Mac (same applications, same usage).

Is there a way to make reboot happen softly like I'm used to? It's really annoying to have to manually close all applications before rebooting!

Bonus question: I've tried everything to get nvidia-settings to save my screen layout, but it gets blown away each reboot. I know there's a LOT written about this online already. I've tried running it as sudo and saving to /etc/X11/xorg.conf, I've tried saving the config to /etc/X11/xorg.conf.d/20-nvidia.conf (and other numbers too), I've tried fiddling with the ~/.nvidia-settings-rc file (""remove any trace of your hostname then set it read only!""). I'm on latest ubuntu, so this isn't Wayland funny business.

Any help: much appreciated! Thank you!

~~~

Ubuntu 18.04 installed in BIOS mode (because NOTHING I could do would make it work in EFI mode). 

lshw output not attached because "The following errors occurred: Your file of 27.8 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."

Monitor config attached
[ATTACH=CONFIG]279594[/ATTACH]

---

### Post by TheFu on 2018-05-06
If those programs don't close themselves cleanly when told to close with the SIGTERM or SIGQUIT signals, that is a bug in them, not Linux.

**sudo shutdown --reboot ** should do it cleanly.   If you **--force** it, things won't be cleanly shutdown following the init rules.  init rules work for the core OS which will ask user programs to shutdown nicely.

Linux isn't Windows or OSX. It does what you tell it.  Unix has a philosophy that users know what they want. It can't tell whether the command is pure genius or total stupidity.   

Sorry, I have no idea how to use the GUI, not something I do.  Mainly server-guy.

From the shutdown manpage:```

       --reboot
           Reboot the machine, regardless of which one of the three commands
           is invoked.

       -f, --force
           Force immediate halt, power-off, reboot. Do not contact the init
           system.
```

How veracrypt integrates into Ubuntu/Linux is unknown.  I know that dm-crypt/LUKS do fully integrate.

---

