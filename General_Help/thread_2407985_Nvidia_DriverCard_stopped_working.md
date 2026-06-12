---
title: "Nvidia Driver/Card stopped working"
date: 2018-12-12
forum: General Help
---

### Post by olivar on 2018-12-12
Okay,

So I reinstalled Ubuntu, and everything was working fine at work the past 2 days.
I ran some updates as the system notified me that there were updates to be installed, and now my laptop monitor is no longer working when the external monitors are plugged in.

Doesn't matter what version of Nvidia Driver I install, the behavior is always the same.
When I purge all nvidia packages from the system, the monitors all work as expected, but run on the internal intel display.
I don't know what to do to fix this...

---

### Post by olivar on 2018-12-12
Found a work-around for now:

* sudo apt purge nvidia*
* sudo rm /etc/X11/xorg.conf
* sudo apt autoremove
* sudo ubuntu-drivers devices
* sudo ubuntu-drivers autoinstall
* sudo reboot

Now I'm running with the Nvidia drivers installed, and no X11 configuration file and this works.
I'm scared of saving the X11 settings with the nvidia-settings application, because as soon as I unplug the monitors I fear it's going to break again.

---

### Post by CatKiller on 2018-12-12
Don't use nvidia-settings to create the xorg.conf file, then :) 

You don't generally need one at all, and less-so a machine-generated one.

If you do have an xorg.conf, and it's not flexible enough to handle your change in configuration, you can just edit the file rather than rushing to purge all your drivers.

---

### Post by olivar on 2018-12-12
well, if I don't need one then I'm not going to generate one :D
Still a complete newbie when it comes to Linux, but it works at the moment, so I'm not touching anything and letting Ubuntu run/work without the config file.

---

### Post by CatKiller on 2018-12-12
Sounds like a plan :)

The auto-configuration has got pretty good these days. I'm also a fan of the way you can separate out the different sections now in xorg.conf.d. It used to be the case that you had to specify *everything* in a single xorg.conf file, and if you didn't specify it it wouldn't work.

The auto-configuration is much more flexible for things like changing the configuration when you plug/unplug a monitor.

---

