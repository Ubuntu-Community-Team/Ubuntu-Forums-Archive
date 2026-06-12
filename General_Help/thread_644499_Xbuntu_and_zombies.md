---
title: "Xbuntu and zombies"
date: 2007-12-18
forum: General Help
---

### Post by j_latteier on 2007-12-18
I just migrated from Ubuntu 7.10 to Xbuntu 7.10 and find that many processes like Mousepad and Xfce Teminal leave zombies, Otherwise it is great! Is this normal for Xbuntu? I can't find information on the web.

---

### Post by kerry_s on 2007-12-19
> **j_latteier said:**
> I just migrated from Ubuntu 7.10 to Xbuntu 7.10 and find that many processes like Mousepad and Xfce Teminal leave zombies, Otherwise it is great! Is this normal for Xbuntu? I can't find information on the web.

it was normal for me when i had xubuntu installed. i used a script to chase them down.
here's the script, just make a file paste it in there and make it executable, then just click on it when ever you see the zombies.

```


#!/bin/sh
kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'`


```

---

### Post by j_latteier on 2007-12-19
Kerry- Thanks for the script. That takes care of the zombies, but it also kills the xfdesktop. There is a menu option turn off xfce desktop management. It can be managed in a rc file. Maybe that's what I should do.

---

### Post by kerry_s on 2007-12-19
> **j_latteier said:**
> Kerry- Thanks for the script. That takes care of the zombies, but it also kills the xfdesktop. There is a menu option turn off xfce desktop management. It can be managed in a rc file. Maybe that's what I should do.

hmmm, it must have been xfdesktop that caused the zombie. what the script does is open the parent of the zombie process, then kills it properly, it only kills the parent that caused the zombie. i've never found another way to kill zombies other than a reboot, since i didn't reboot often, i would just let the zombies build up till about 20 then killl them, sometimes the system will kick in and they will die off them selves. they don't take no resources so you can just leave them if you don't mind them there, it's not really a big.

---

