---
title: "Disabling x server for nvidia install"
date: 2007-04-22
forum: General Help
---

### Post by Charkel on 2007-04-22
Well I'm going to install drivers for my gForce but it tells me to disable the x server.
I've done this before but i don't remember how i did.

I've looked around and found some way but that didn't work quite as i hoped, it took me to a command prompt.

So does anyone know a simple way of disabling the x server temporarily?

---

### Post by DoktorSeven on 2007-04-22
Disabling the X server *will* take you to a command prompt.  X is the thing that runs the the graphical desktop interface part of Linux.

**sudo /etc/init.d/gdm stop**
then if you don't get a text login prompt hit CTRL+ALT+F2.  You can then login and do whatever is necessary.

To start X back up after you're done:
**sudo /etc/init.d/gdm start**

(Note: for kubuntu, it's kdm stop / kdm start.)

---

### Post by Charkel on 2007-04-22
> **DoktorSeven said:**
> Disabling the X server *will* take you to a command prompt.  X is the thing that runs the the graphical desktop interface part of Linux.

**sudo /etc/init.d/gdm stop**
then if you don't get a text login prompt hit CTRL+ALT+F2.  You can then login and do whatever is necessary.

To start X back up after you're done:
**sudo /etc/init.d/gdm start**

(Note: for kubuntu, it's kdm stop / kdm start.)

Well thank you, I used this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)

You think you also can tell me how to check which version I have?

---

### Post by dcstar on 2007-04-22
> **Charkel said:**
> Well thank you, I used this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)

You think you also can tell me how to check which version I have?

Gnome is the "standard" desktop that you get with Ubuntu, the other one is what Kubuntu installs.

You can run both commands, it will do no harm.

---

### Post by Charkel on 2007-04-23
> **dcstar said:**
> Gnome is the "standard" desktop that you get with Ubuntu, the other one is what Kubuntu installs.

You can run both commands, it will do no harm.

Hehe :p I know that already. I'm talking about graphic card driver version

---

### Post by Mad_Max_1412 on 2007-10-09
Guys,

I've just followed this post to get out of X so I can install the Nvidia drivers.  Thanks for your tips on getting to the prompt.

Anyway, I've now got a problem when I run the install.

It firstly says that there's no precompiled kernel interface to match your kernel. Would you like the installer to attempt to download one from the nvidia FTP site.

I choose "Yes" but it comes back saying it couldn't find one.  It then says the installer will need to compile a kernel interface for your kernel.  I click ok, which is the only option.

It then says:

You do not appear to have the libc header files installed on your system. Please install your distributions' libc development package.

This then takes me back to the command prompt.

Any suggestions?

Thanks

---

