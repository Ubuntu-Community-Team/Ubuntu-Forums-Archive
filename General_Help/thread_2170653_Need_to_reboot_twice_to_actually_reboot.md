---
title: "Need to reboot twice to actually reboot"
date: 2013-08-27
forum: General Help
---

### Post by Yorthegreat on 2013-08-27
My XBMC box refuses to reboot when I enter "sudo reboot" or "sudo shutdown -r now". It basically does nothing, no output in syslog nothing happening on the prompt.

When I enter "sudo reboot" at the same prompt again, the machine reboots correctly. The following will also work "sudo reboot && sudo reboot".

The machine is used as a keyboard less XBMC station. All connections are through SSH. I am running ubuntu 13.04, although the problem has been with the previous version as well.

Any ideas on how to analyze or fix this one?

---

### Post by ryan-hoboabode on 2013-12-06
I'm having the same issue.

---

### Post by hwkns on 2014-03-12
I'm seeing the exact same behavior in Ubuntu 12.04.  I do have XBMC installed, but I also use the machine normally as a desktop computer.

---

### Post by matt_symes on 2014-03-13
Hi

I assume commands like 

```
shutdown -r now
reboot
```

are not working for you, from the terminal ?

If so, try using a different ```
*reboot=*
``` grub kernel parameter.

Start off with

```
reboot=bios
```

or

```
reboot=acpi
```

You will need to edit the grub command line, but these issues should be fixable.

If you need advice on how to do that, post back. Someone will help.

Kind regards

---

