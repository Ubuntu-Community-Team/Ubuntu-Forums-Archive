---
title: "hal/dbus error"
date: 2008-04-15
forum: General Help
---

### Post by pbne on 2008-04-15
Hey!
when I login I get this error:  HAL: Failed to initialize..after searching for this on various forums, I realized that a lot of people have had this problem, however they were able to fix it with some rather quick and easy fixes..I am not...
Here's what I tried:

 - Enabling timed login (30 sec) as a work around for race conditions
 - Changing the order of the symbolic links in /etc/rc2.d as a second work around for race conditions
 - Reinstalling dbus
 - Reinstalling hal
 - Adding an empty line to /etc/fstab
 - Disabling ACPI in bios

I proberbly forgot to mention something, cause I've really tried alot of proposals to fix this issue.

Here's the relevant contents of /var/log/daemon.log
[http://pastebin.com/m51f156e9](http://pastebin.com/m51f156e9)

Hope someone can help me.

Regards pbne

---

