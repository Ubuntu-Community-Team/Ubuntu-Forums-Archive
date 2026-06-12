---
title: "Directory for startup apps?"
date: 2013-01-15
forum: General Help
---

### Post by Kopkins on 2013-01-15
This should be fairly straight forward I believe. I just need to know the file or the directory in which the commands from startup apps are run. Going to the top right, click the gear, click Startup Applications. I just need to know where the backend for that is. I have very many apps and scripts that start that way and now I can not log on without my computer becoming unresponsive. I just want to take out a few apps. I can't seem to find it. It's in my /home right?

Thank you,

Kopkins

---

### Post by sisco311 on 2013-01-15
~/.config/autostart/
and
/etc/xdg/autostart/

You can read the full specification here:
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

---

### Post by Kopkins on 2013-01-15
> **sisco311 said:**
> ~/.config/autostart/
and
/etc/xdg/autostart/

You can read the full specification here:
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)


Thank you so much, that fixed my issue. It was a script that was messing everything up. Still not sure exactly what went wrong with it. Thank you.

Kopkins

---

