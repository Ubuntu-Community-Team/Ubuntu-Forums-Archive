---
title: "Laptop lid-suspend ignoring - BEFORE a user logs in."
date: 2017-11-15
forum: General Help
---

### Post by Ajfleming on 2017-11-15
Hi - 

I've got a laptop running 16.04 LTS which is acting as an always on server.

I've managed to get the system to ignore lid open/close - as long as there's a user logged in. However - if there's no user logged in - say the system has just rebooted - I have to manually open the lid to get the network interfaces to come up. If I then shut the lid - the system suspends. If I log a user in and shut the lid - everything stays functional. 

Thanks, 

Adam.

---

### Post by Ajfleming on 2017-11-15
Solved by : [COLOR=#111111][FONT=Ubuntu]editing [/FONT][/COLOR]/etc/UPower/UPower.conf[COLOR=#111111][FONT=Ubuntu] and changing [/FONT][/COLOR]IgnoreLid=false[COLOR=#111111][FONT=Ubuntu] to [/FONT][/COLOR]IgnoreLid=true[COLOR=#111111][FONT=Ubuntu] at the end of the file
[/FONT][/COLOR]

---

### Post by Ajfleming on 2017-11-15
Bit overeager to call this solved - I made the change above, and still have the same problem.

---

