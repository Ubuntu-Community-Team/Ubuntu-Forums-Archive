---
title: "nvidia-settings issue"
date: 2007-04-24
forum: General Help
---

### Post by russianbandit on 2007-04-24
I've never been able to use nvidia-settings successfully, because the application can never save to to the Xconf file.

Everytime I play around in nvidia-settings and press "Save To X Configuration file"

I get this error:

ERROR: Unable to determine valid vertical refresh ranges for display device
       'Sharp' (GPU: GeForce Go 6800)!


ERROR: Failed to add display device 'Sharp' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!




What is wrong with nvidia-settings? Am I the only one with this problem?

---

### Post by ahaslam on 2007-04-24
> **sudo** nvidia-settings
;)

---

### Post by johnc4510 on 2007-04-24
In a terminal type this:

man nvidia-settings

This will give you options on loading your config file

I believe you might want the --no-conf   option, but can't remember for sure

you can load nvidia-settings and the option right into your start sessions list

---

### Post by Talon2 on 2007-04-24
> **russianbandit said:**
> I've never been able to use nvidia-settings successfully, because the application can never save to to the Xconf file.

Everytime I play around in nvidia-settings and press "Save To X Configuration file"

I get this error:

ERROR: Unable to determine valid vertical refresh ranges for display device
       'Sharp' (GPU: GeForce Go 6800)!


ERROR: Failed to add display device 'Sharp' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!




What is wrong with nvidia-settings? Am I the only one with this problem?

Maybe you are the lucky one.

I tried to set up my new 7600GS card a couple of days ago.  I installed the new card then loaded feisty clean.  Things went downhill from there.  I couldn't get a proper refresh rate so I tried nvidia-settings.  It was able to save a new xorg.conf here... only problem is that this new xorg.conf wouldn't allow X to start.  I could not figure out the problem so back in went the old ATI card (that is supported by the open source driver) and a reinstall has everything working.

Video support in this operating system is lacking.

There needs to be an overall examination of the situation.  I don't think I could have come up with a bigger furball for a video support subsystem if I have tried.

---

### Post by Dave54 on 2007-04-25
> I couldn't get a proper refresh rate...
There's a bug with nvidia cards + feisty that messes up all refresh rates.
Solution: [http://ubuntuforums.org/showthread.php?t=414287]("http://ubuntuforums.org/showthread.php?t=414287")

> only problem is that this new xorg.conf wouldn't allow X to start
I think nvidia saves the old xorg file. You could recover it with something like
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

