---
title: "How do I load a program before Nvidia driver loads?"
date: 2007-06-06
forum: General Help
---

### Post by timzak on 2007-06-06
I have a program that I want to autostart with Feisty, but it needs to load before the Nvidia driver is active, so it can't go into Sessions.  It is nvclock and it unlocks pipelines on my video card.  Here are the instructions given by the nvclock help:

> Pipeline modding can't be used while the Nvidia driver is active (exit X and unload the kernel module).
If you don't follow these instructions there's a big chance that your computer will freeze.

I am a newbie so I need step-by-step instructions.  Here is exactly what needs to be run:

```
nvclock -f -P 1111 -V 111111
```

I just need that to be executed prior to the Nvidia driver loading.

Can anyone tell me how to do this?

Thanks!

---

### Post by esavato on 2007-06-06
You can go into Session manager and add it there.  look under the startup programs tab.  If that does not work, you may have to look into editing your init.d

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by Adramelech on 2007-06-07
> Pipeline modding can't be used while the Nvidia driver is active (exit X and unload the kernel module).
If you don't follow these instructions there's a big chance that your computer will freeze.

I guess running it before nvidia drivers is not going to help, cause they will get active eventually.

I would

Exit X:  /etc/init.d/gdm stop

Unload module: modprobe -r nvidia_driver_here

---

### Post by timzak on 2007-06-07
esavato:

Sessions does not work.  It corrupts the screen because nvidia drivers are loaded already by the time it loads from Sessions.

I should qualify that:  Sessions works IF after the desktop loads, I immediately do a CTRL-ALT-backspace and reload X.  But rather than do that every time I turn on my computer, I'd like it to load automatically without me having to do that.

Adramelech:

Could you tell me how to do what you suggested?  I don't understand if you're saying to type that manually each startup?  Or is there a way to automate what you said?

---

### Post by seamuso on 2007-06-07
you have to modprobe with this option ..

[quote=from modprobe.conf man page]
**install** *modulename* *command...* This is the most powerful primitive in *modprobe.conf*: it tells **modprobe** to run your command instead of inserting the module in the kernel as normal. The command can be any shell command: this allows you to do any kind of complex processing you might wish. For example, if the module "fred" worked better with the module "barney" already installed (but it didn't depend on it, so **modprobe** won't automatically load it), you could say "install fred /sbin/modprobe barney; /sbin/modprobe --ignore-install fred", which would do what you wanted. Note the **--ignore-install**, which stops the second **modprobe** from re-running the same **install** command. See also **remove** below. You can also use **install** to make up modules which don't otherwise exist. For example: "install probe-ethernet /sbin/modprobe e100 || /sbin/modprobe eepro100", which will try first the e100 driver, then the eepro100 driver, when you do "modprobe probe-ethernet". 
If you use the string "$CMDLINE_OPTS" in the command, it will be replaced by any options specified on the modprobe command line. This can be useful because users expect "modprobe fred opt=1" to pass the "opt=1" arg to the module, even if there's an install command in the configuration file. So our above example becomes "install fred /sbin/modprobe barney; /sbin/modprobe --ignore-install fred $CMDLINE_OPTS"[/quote]


An example is the /etc/modprobe.d/lrm-video file ..
```

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

```which tells the system to run /sbin/lrm-video before it loads the nvidia module. It's been a long time since I've used the install option (several years and several distros back to get my sb live working correctly), so maybe someone else can fill in some more of the blanks too

---

### Post by timzak on 2007-06-07
Wow, that's way over my head.  At this point it is easier for me to reload X every time I boot into Feisty.  This is the alternative to doing what I'm trying to do.

Thanks, hopefully someone can chime in and help some more.

---

