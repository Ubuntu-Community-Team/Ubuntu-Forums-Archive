---
title: "ThinkPad X120e. Ubuntu 12.04 hibernate leads to flickering power button and failing"
date: 2013-03-26
forum: General Help
---

### Post by gazazello on 2013-03-26
Hello,

Please help me to resolve this issue with hibernate for ubuntu 12.04 on lenovo thinkpad X120E.
Shortly after I start hibernating the screen goes dark and Power button starts flickering going infinitely. So eventually hibernate is failing.
I created swap partition twice the size of RAM. Swap is enabled.
Hibernation is enabled. This is not my first Precise Pangolin installation on various devices.
Nothing interesting in /var/logs/syslog nothing erroneous found, but I can post that if you'd like to see.
I tried to install TuxOnIce. Result is the same.
I tried to reinstall uswsusp.
I created file named "[COLOR=#333333][FONT=monospace]/etc/pm/config.d/[/FONT][/COLOR]module" containing [COLOR=#333333][FONT=UbuntuMono]HIBERNATE_MODE="shutdown"
[/FONT][/COLOR]I even checked all partition including swap for bad blocks, but nothing was found.

Everything above didn't change anything with dark screen and flickering power button.

---

### Post by gazazello on 2013-03-28
Seems like nobody ever stumbled on this :)

---

### Post by gazazello on 2013-04-01
really nobody?!

---

### Post by Eric.brackenbury on 2013-05-16
> **gazazello said:**
> really nobody?!

I have the same issue with hibernate and 12.04 on my X120e
Hope some one come up wit a solution!
I was beginning to think it might be my solid state HD not being campatible.
Eric B

---

