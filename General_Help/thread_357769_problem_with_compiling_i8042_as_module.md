---
title: "problem with compiling i8042 as module"
date: 2007-02-10
forum: General Help
---

### Post by hovnatan on 2007-02-10
Hi

I8042 and SERIO are comiled directly Ubuntu kernel. I was trying to compile them as modules in ubuntu kernel. So i downloaded linux-source-2.6 package  from official repos and applied default kernel config and tried to change the values of I8042 and SERIO to as modules. But in make menuconfig I can't change them (the checkboxes are inactive). When I tried to change them directly in vim .config and compile the kernel, it compiled them directly to kernel image :(. I have tried the same thing with  vanilla kernel from kernel.org  and it works fine. Anybody knows how to correct this thing? It is important for my laptop (hp nx7400) in which keyboard and mouse don't work after resuming from suspend to ram if not compiled as modules.

Thanks,
Hovo

---

### Post by john_brown_jr on 2007-02-12
Hi hovnatan, 

I have the same laptop (nx7400) and had same problem (it hanged on resume from suspend). I have not yet managed to fix it, but I remember reading that upgrading to new (>2.6.19.rc5) kernel might help. (Well, I have 2.6.19rc5 right now, but now the laptop is not suspending at all. It simply resumes immediately after suspend. I had the same problem in SUSE, and s2ram utility helped there, so I'm going to try that with Ubuntu as well). I'll let you know if (when) I succeed.


Kind regards,
John

---

### Post by hovnatan on 2007-02-12
Hey John

I think I have solved the problem. So what I did. I compiled new kernel with I8042 as a module (the [config]("http://emisca.altervista.org/nx7400/config-i8042")  file you can find on very useful site [http://emisca.altervista.org/nx7400/]("http://emisca.altervista.org/nx7400/")). Then I made some changes in /etc/default/acpi-support file (it is attached to this post), basically the important thing was to uncomment SAVE_VIDEO_PCI_STATE=true and unload some modules with MODULES="..." (I'm not sure that all of modules are important to unload, maybe it'll work without unloading some of them). And that's all it is working!

Thanks,
Hovo

---

### Post by john_brown_jr on 2007-02-13
Hi,

How did you manage to compile i8042 as module? Right now I have the same problem that I can't disable it in xconfig and menuconfig.

Kind regards,
John

---

### Post by hovnatan on 2007-02-13
Use the config file from my previos post ([http://emisca.altervista.org/nx7400/](http://emisca.altervista.org/nx7400/) from here)
Hovo

---

### Post by john_brown_jr on 2007-02-14
Well, I tried to copy the .config file to /usr/src/linux, but whenever I call "make-mkpkg clean", Ubuntu seems to owerwrite the file. 

Anyway, I managed to fix it using xconfig. To get rid of i8042, one must also remove AT keyboard or something like that. After that, everything was just fine, and the laptop now suspends, and wakes up. YYYEEEEESSS!!!

Thank you!

John

---

