---
title: "Help finding running process"
date: 2007-03-09
forum: General Help
---

### Post by gatliff on 2007-03-09
how do I find what running I try to use Adept Manager I get this

"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

---

### Post by Slojah on 2007-03-09
To find running applications in Linux use ps.  In your situation I might try:

Open a terminal window and try:
```
ps aux | grep apt
```

That will show you all of the processes containing the letters "apt".  I think you may be running synaptic package manager or your installing updates

---

### Post by gatliff on 2007-03-09
thanks all it show is "index-watcher watch --syslog" is this my bug?

---

### Post by Slojah on 2007-03-09
Well I would try this then:

```
sudo /etc/init.d/apt-index-watcher stop
```

---

