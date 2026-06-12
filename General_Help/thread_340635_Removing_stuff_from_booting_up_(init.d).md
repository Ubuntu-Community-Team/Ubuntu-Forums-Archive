---
title: "Removing stuff from booting up (init.d)"
date: 2007-01-17
forum: General Help
---

### Post by commodore on 2007-01-17
I have some stuff starting up by default when I boot my computer. I'd like to turn them off.

---

### Post by gwpritch on 2007-01-17
The easiest way is with a little app called sysv-rc-conf.
You can down load it from the repos
 
```
sudo apt-get install sysv-rc-conf
```

then:

```
sudo sysv-rc-conf
```

You will be presented with a list of services and which run levels they are active on.

Just uncheck what ever you want to turn off.

---

### Post by Rui Pais on 2007-01-17
and [here]("http://ubuntuforums.org/showthread.php?t=89491") (for the sake of completeness) are same detailed explanation and extra tips...

---

### Post by commodore on 2007-01-24
Wasn't there a command line script installed by default for this?

---

### Post by Rui Pais on 2007-01-24
> **commodore said:**
> Wasn't there a command line script installed by default for this?

the app that gwpritch or my link refers is a command line app, but as far as i remember it was never installed by default. Now there is some GUIs to do that (BUM and some other gnome app) but they are all very limited, allowing only the minimum changes... 

What i noted is that ubuntu from version to version as been reducing the number of extra stuff enabled and requiring less tweaking. With edgy i only turn off laptop related things (this is not a laptop) and some cron like thing - cron, atd, anacron, seems too much things on the same... not that one gains much more now days. 
It was important to turn off evwm and alike when those come out of the box and one don't have use to it. It was a nice trick to make boot fast... old days :)

---

