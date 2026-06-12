---
title: "Can't Shutdown and Power Off (always restarts) 14.04"
date: 2014-07-25
forum: General Help
---

### Post by shag00 on 2014-07-25
I am unable to shutdown and power off my machine, I don't know when this occurred as it is normally running 24/7 and it's some time since I wanted to power off. I have attempted shutdown through the standard GUI and through the terminal (sudo shutdown -h now). In either case the machine always reboots without user input. It is similar to pressing the reset button on the PC as the PC actually turns off (fan lights go off). 

I have tried to edit 
/etc/default/grub [COLOR=#0000ff]from [/COLOR]GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; [COLOR=#0000ff]to[/COLOR] GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash acpi=force&#8221;

with no solution.

Any help is appreciated.

---

### Post by qwerkus on 2014-07-25
Did you try to run "sudo poweroff" in a console ?

---

### Post by shag00 on 2014-07-27
Unsurprisingly sudo poweroff yields the same results as the other commands.

---

### Post by shag00 on 2014-08-02
By changing the BIOS setting Wake on LAN to disabled the machine will now power off properly.

---

### Post by fomember on 2014-09-13
I just updated my home server from 12.04.1 LTS to 14.04.1 LTS and I do get the same problem.
If I issue a "poweroff" command the server just reboots.

Disabling Wake On LAN is no option for me.

With 12.04 I had no problem with  poweroff   and I used to use  Wake On LAN to wake up my server whenever a client needs it.
I also used Wake On Alarm to get the server to do regular maintenance tasks.

Any clues why the server now behaves differently?

P.S. My Mobo is an MSI P9D-X with a  Xeon CPU E3-1230L v3

---

