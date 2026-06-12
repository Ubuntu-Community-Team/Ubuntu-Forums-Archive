---
title: "acpi-cpufreq.ko, Old precompiled Modules"
date: 2014-11-27
forum: General Help
---

### Post by jakfish on 2014-11-27
My HTC Shift X9500 has many hardware constraints and forces me to run Hardy 8.04.4 with the 2.6.24-19-generic kernel.  The Shift runs high temperatures and I would like to undervolt using this thread:

[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

The rub is, all the download links in the thread are dead.  Using Wayback archive, I've found [COLOR=#000000][FONT=Ubuntu Mono]linux-phc-optimize.bash and [/FONT][/COLOR]functions.bash from [http://www.s3pp.de/misc/linux-phc-optimize.bash](http://www.s3pp.de/misc/linux-phc-optimize.bash) and [http://www.s3pp.de/misc/functions.bash](http://www.s3pp.de/misc/functions.bash).  What I'm missing is the precompiled module acpi-cpufreq.ko from [http://www.s3pp.de/misc/19/acpi-cpufreq.ko](http://www.s3pp.de/misc/19/acpi-cpufreq.ko)

Did anybody ever undervolt Hardy and did they save these acpi-cpufreq.ko's, or know where I could find them?

I'd very much appreciate any help,
Jake

---

### Post by tgalati4 on 2014-11-27
You typically have to compile the kernel from scratch to get *pchtool* to work.  When you compile the kernel, you also compile all of the modules that go with it, including acpi-cpufreq.ko.  So unless someone has that module, you will have to spend some time creating a build environment and building it yourself.

Perhaps the high temperatues are caused by something like a stuck process or a bad heatsink or heat paste.

---

### Post by jakfish on 2014-11-27
Hi, thank you for your post on a holiday.  Compiling from scratch, given the fact that the kernel already has certain modules that are HTC-specific, it's above my pay grade.

The s3pp.de [COLOR=#000000]acpi-cpufreq.ko for the [/COLOR][COLOR=#000000]2.6.24-19-generic kernel will work, I just can't find it on the web.  Seems so strange that it could disappear so completely :).

At any rate, thank you again for your post,
Jake[/COLOR]

---

