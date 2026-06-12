---
title: "Broken package error... Need help"
date: 2012-11-26
forum: General Help
---

### Post by linuxuser12345 on 2012-11-26
I have a broken package in my system and it will absolutely NOT allow my system to continue with any updates, etc. until this broken package is fixed :(

I tried repairing it via Synaptic, but the same problem occurs over and over. Synaptic even tells me I cannot fix the package... How can I fix this problem??

```
E: burg-theme-lightness: package burg-theme-lightness is not ready for configuration  cannot configure (current status `half-installed')
```

---

### Post by oldfred on 2012-11-26
Do you have a ppa for burg?

I thought burg was not supported anymore so you may not have an updated ppa. I would uncheck ppa in synaptic or comment it out in entry in sources:

       sudo cp /etc/apt/sources.list ~/sources.list.backup
gksudo gedit /etc/apt/sources.list

---

### Post by linuxuser12345 on 2012-11-27
I removed the PPA

---

### Post by linuxuser12345 on 2012-11-28
I removed the PPA and I'm still getting the same errors :(

---

### Post by oldfred on 2012-11-28
You are still getting a burg error without burg?

---

### Post by ibjsb4 on 2012-11-28
gksudo nautilus

And search filesystem:  

burg-theme-lightness

And remove the leftovers

---

### Post by linuxuser12345 on 2012-11-28
Where would I probably find the leftovers?

---

### Post by linuxuser12345 on 2012-11-29
> **oldfred said:**
> You are still getting a burg error without burg?

Yes, I am still getting errors, even without Burg :(

---

### Post by oldfred on 2012-11-29
Can you post exact errors. Are you sure you comment out or deleted all the ppas in sources list?

Double check direct in sources.
       cp /etc/apt/sources.list ~/sources.list.backup
gksu gedit /etc/apt/sources.list

---

