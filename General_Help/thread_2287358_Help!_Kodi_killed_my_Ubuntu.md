---
title: "Help! Kodi killed my Ubuntu"
date: 2015-07-18
forum: General Help
---

### Post by ray_silva on 2015-07-18
I made the mistake of creating the autostart script in the Kodi Wiki. It got saved to /etc/init/kodi.conf
The essential part is:

env USER=kodi
 
start on (filesystem and stopped udevtrigger)
stop on runlevel [016]
 
script
  exec su -c "xinit /usr/bin/kodi-standalone -- -nocursor :0" $USER
end script


The problem is that now I cannot get back to Ubuntu even on my regular login. My Ubuntu computer has been turned into a Kodi ONLY box.
How can I reverse this? I desperately tried booting to terminal and from there logged in to my account and deleted the kodi.conf file, but it still keeps booting Kodi only in standalone mode.

---

### Post by papibe on 2015-07-18
Hi ray_silva.

Did you also modify the file /etc/X11/Xwrapper.config ?

If so remember to set it back as it was (last line):
```
allowed_users=console
```
Let us know how that goes.
Regards.

---

### Post by ray_silva on 2015-07-18
That did it...Wow, thanks!

What a relief....

---

