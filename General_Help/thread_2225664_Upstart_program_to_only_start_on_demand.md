---
title: "Upstart program to only start on demand"
date: 2014-05-22
forum: General Help
---

### Post by hojjat on 2014-05-22
I have created an upstrat script for a program that I need to execute at times. It pretty much looks like this:

```

...
start on runlevel [2345]
stop on runlevel [!2345]

respawn

setuid blah
setgid blah

exec /foo/bar -param -param -param

```

I want to modify it such that it would NOT start on boot. Instead, I would still have the option to go to terminal and run *sudo start blah* to start it when I really want to.

How can I modify the upstrat script to achieve that result?

---

### Post by Gyokuro on 2014-05-22
Hi

You should check the Upstart Cookbook but what you are requesting is explained at: [http://upstart.ubuntu.com/cookbook/#starting-a-job](http://upstart.ubuntu.com/cookbook/#starting-a-job)

- HTH

---

### Post by steeldriver on 2014-05-22
*I think* that if it's your own service (i.e. there's no danger of the upstart script getting replaced by a subsequent system update), then you can just remove the 'start on' line from your script

OTOH if you want to prevent a system service from starting automatically, you can create a *servicename*.override file containing the word 'manual' in the /etc/init directory

---

