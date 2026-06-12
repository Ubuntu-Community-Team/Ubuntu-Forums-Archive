---
title: "I need Major Video Help"
date: 2008-06-15
forum: General Help
---

### Post by alphadeltaviii on 2008-06-15
Ok, so i screwed up my display refresh rate, and somehow I locked it in so i have no monitor. I have access to webmin, and ssh. I for the life of me can't figure out how to reset the settings for my monitor.

here's what i have done:

through ssh, stopped gde using 
```

sudo /etc/init.d/gdm start

```

an then i tried to modify my xorg.conf file, and restart gde but it hasn't worked. 

Please HELP!

---

### Post by alphadeltaviii on 2008-06-15
a reboot seemed to fix the problem, crisis averted

---

### Post by lut4rp on 2008-06-15
Good job!

---

