---
title: "Kernel boot options - debug"
date: 2008-03-07
forum: General Help
---

### Post by electricchild on 2008-03-07
Can someone explain to me how the option "debug" is supposed to exactly work?

[http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html)

From the Linux BootPrompt  HOWTO

> The kernel communicates important (and not-so important) messages to the operator via the printk() function. If the message is considered important, the printk() function will put a copy on the present console as well as handing it off to the klogd() facility so that it gets logged to disk. The reason for printing important messages to the console as well as logging them to disk is because under unfortunate circumstances (e.g. a disk failure) the message won't make it to disk and will be lost.

The threshold for what is and what isn't considered important is set by the console_loglevel variable. The default is to log anything more important than DEBUG (level 7) to the console. (These levels are defined in the include file kernel.h) Specifying debug as a boot argument will set the console loglevel to 10, so that all kernel messages appear on the console.

The console loglevel can usually also be set at run time via an option to the klogd() program. Check the man page for the version installed on your system to see how to do this. 

So how exactly do I enter this option and view the log? Here is my situation: I have an emulator booting up a target (guest) OS of linux, with Ubuntu as my build OS. The boot up process in the emulator fails because something is wrong with the kernel configuration. I want to see the error logs for the boot up process of that kernel on the emulator. So in the command to launch the emulator I have -append "debug", where -append is an option of the emulator, and "debug" is a kernel boot option.

But I don't get anything in the emulator screen or back in my terminal window. There is no indication that I even got a log of the errors! Does anyone know how I use this debug option?

---

