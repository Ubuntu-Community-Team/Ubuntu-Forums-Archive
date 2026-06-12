---
title: "Ubuntu 13.04 log in screen error"
date: 2014-01-24
forum: General Help
---

### Post by Edgardo_Marrero on 2014-01-24
I am dual booting windows 7 and ubuntu 13.04 (windows installed first) and today i just upgraded from 12.10 to 13.04. I restarted my computer because ubuntu was acting funny and when i tried to boot up ubuntu the log in screen wasn't showing up, this was:

 [ATTACH=CONFIG]249710[/ATTACH]

---

### Post by ajgreeny on 2014-01-24
Looks like a graphic card glitch.

What card do you have and what driver?

---

### Post by Edgardo_Marrero on 2014-01-24
i have an NVIDIA GeForce 6150SE nForce 430

---

### Post by ajgreeny on 2014-01-25
And the driver; open source or proprietary, ie from additional drivers?

---

### Post by jeanjd63 on 2014-01-25
Hello

You can try this :
CTRL+ALT+F1 to open a console.
Then connect with yours user/password and do :
[B]sudo  apt-get  purge  "nvidia *"
sudo  apt-get  install  nvidia-current  nvidia-settings[/B]
and 
**sudo  reboot**

---

