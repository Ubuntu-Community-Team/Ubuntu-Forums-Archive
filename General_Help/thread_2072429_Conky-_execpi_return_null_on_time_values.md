---
title: "Conky- execpi return null on time values"
date: 2012-10-17
forum: General Help
---

### Post by FLCL on 2012-10-17
I'm running a conky script in order to return my external IP using the execpi command. However, if I set the execution time higher than a certain number it will change the return to (null), and as soon I lower it it shows the IP again in the conky display.

Example:
```
execi **3600** ~/.IPChecker.sh
``` will change the information on the display field to ```
(null)
```

Though if I set it to:
```
execi **1600** ~/.IPCheck.sh
``` It will immediately show the IP again on the display. 

After tinkering with the numbers it seems the highest value I can set before it returns (null) on the display is 1600, which seems pretty odd to me.

               Anyone have an idea? Thanks!

---

### Post by stinkeye on 2012-10-17
There is a bug in the Precise version of conky where execi/execpi commands don't run
until your uptime reaches your execpi interval.
ie Your system has been running for about **half an hour** so the **execi 1600** works.
When it's been running for **an hour** the **execi 3600** will work.

Upgrade Conky using this ppa.
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
sudo apt-get install conky-all

```

---

### Post by FLCL on 2012-10-23
Ah! Thank you, works like a charm

---

### Post by aalemann on 2013-01-23
> **stinkeye said:**
> There is a bug in the Precise version of conky where execi/execpi commands don't run
until your uptime reaches your execpi interval.


I just want to say thank you for mentioning this, because it had the same problem and was thinking that I was my fault, so: thanks! :D

---

### Post by Fuxy on 2013-03-25
Thx. That solved a related problem with the output of execpi not being rendered corectly by Conky.

I wish canonical (or whoever maintains this binary) would fix their ****. I always run into stuff like this.

---

### Post by RJ12 on 2013-03-25
> **Fuxy said:**
> Thx. That solved a related problem with the output of execpi not being rendered corectly by Conky.

I wish canonical (or whoever maintains this binary) would fix their ****. I always run into stuff like this.

Well, you know, bugs happen and can be very hard to track down ;)

---

