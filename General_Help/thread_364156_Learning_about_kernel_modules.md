---
title: "Learning about kernel modules"
date: 2007-02-17
forum: General Help
---

### Post by duns0014 on 2007-02-17
I've read some stuff and I have the basic ideas, but I still have some questions.
1. I've read that the driver for the filesystem type you have installed as your root filesystem has to be compiled into the kernel, it can't be a module.  So why does ext3 appear when I do lsmod?
2. How does the kernel know what to load when my computer starts up?  And why's it load a bunch of stuff I don't need, like joydev?
3. How can I find out which modules my computer needs and doesn't need so I can somehow stop what I don't need from loading?

And does anyone have any good links that would explain questions like this?  I've looked through tldp and others.

---

### Post by az on 2007-02-18
> **duns0014 said:**
> I've read some stuff and I have the basic ideas, but I still have some questions.
1. I've read that the driver for the filesystem type you have installed as your root filesystem has to be compiled into the kernel, it can't be a module.  So why does ext3 appear when I do lsmod?
2. How does the kernel know what to load when my computer starts up?  And why's it load a bunch of stuff I don't need, like joydev?
3. How can I find out which modules my computer needs and doesn't need so I can somehow stop what I don't need from loading?

And does anyone have any good links that would explain questions like this?  I've looked through tldp and others.

1.  I think the cramfs filesystem is the relevant one.  The boot process used to be that the kernel image was loaded into ram and them it was run.  Nowadays, an initrd (init ram disk) is loaded along with the kernel image.  The system is run from there and other essential modules are loaded and then the root filesystem shifts (pivot_root) to your disk (or other device).  The filesystem of the initrd is cramfs or squashfs, depending on the version of Ubuntu.

2.  Udev detects whatever hardware you have and leads to modules appropriately.  This formerly used to be hotplug, and before that it used to be discover.  Other distros used other hardware detection techniques (kudzu, for example).  Some modules are loaded if you have the hardware to support them, regardless of whether thay are being used.  I think the joystick module is there because you have a gameport?  You may have nothing plugged into it, but it is there.  I may be wrong.  Anyway, even if you took all those modules and counted the kbs of memory they took up, it would be irrelevant.

3.  You can blacklist modules, but unless you are running a system with less the 8 megs of ram, you needn't worry about the waste.  It is less than trivial.  You will not gain any performance from preventing a few modules from being loaded.

---

### Post by duns0014 on 2007-02-18
Thanks a lot, that helps.  But as for udev loading modules, I still have ones loading that don't seem relevant, like sony_acpi loads by default even though I have a toshiba laptop.  I've heard people talking about tweaking the kernel and making a custom one to improve performance,  Since I knew the modules didn't take up that much ram, I kind of assumed that the modules would use up resources some other way, like by using up cpu cycles constantly, for some reason or another.  So that's not true?  Again, have any good links that explains how ubuntu or linux in general deals with modules?

---

### Post by az on 2007-02-18
> **duns0014 said:**
>  I've heard people talking about tweaking the kernel and making a custom one to improve performance,  

Years ago, when you installed a new distro, you had to use the stock kernel that shipped with the distro that had to have as many options turned on as possible, so that 90 percent of the people who wanted to install it could actually do so.  Since all these options were running (they were not even modules you could unload) the kernel would usually be slower.

You would then unpack the kernel source, compile the kernel with only the options you need and run your system.. Every time you needed to use a new peice of hardware, you needed to recompiel your kernel.  

Then the kernel became more modular, and you started to be able to detect and load modules as you need them.

You haven't needed to recompile your kernel for those reasons since, say, 2001.

---

### Post by duns0014 on 2007-02-18
Tell that to the gentoo people!

Thanks again.  But about sony_acpi and other things like that, how do they get loaded?  Is udev doing that?  Or what other things can make a module load?

---

### Post by duns0014 on 2007-03-21
I still kind of looking for answers here.  I don't think it's udev that's loading modules for me.  Not only does sony_acpi load automatically, but I checked and I have a toshiba_acpi module that doesn't load automatically, even though I have a toshiba and not a sony computer.  How's that work?  I thought there was some part of the kernel that autodetected which modules you need, it used to be kerneld and now it's called something else.  Any ideas?  Know anyone who'd know for sure?

---

