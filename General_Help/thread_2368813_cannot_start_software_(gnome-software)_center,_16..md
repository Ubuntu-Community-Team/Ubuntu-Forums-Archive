---
title: "cannot start software (gnome-software) center, 16.04"
date: 2017-08-15
forum: General Help
---

### Post by gychang2 on 2017-08-15
I have 16.04 installed and runs well, today I noticed software center icon and command of gnome-software does not open the application.  Updating, rebooting even after "sudo apt-get update && sudo apt-get install --only-upgrade gnome-software" does not work.

Is there a fix for this?

---

### Post by Andreyshel on 2017-08-15
What output you get when you try to run gnome-software from command line?

---

### Post by gychang2 on 2017-08-16
> **Andreyshel said:**
> What output you get when you try to run gnome-software from command line?

cursor keeps blinking..., no launching, no error message...

---

### Post by Andreyshel on 2017-08-16
Have you tried reviews db recreation?

To do that you can run
 ```
killall gnome-software
 rm -r ~/.local/share/gnome-software
```

---

### Post by gychang2 on 2017-08-17
> **Andreyshel said:**
> Have you tried reviews db recreation?

To do that you can run
 ```
killall gnome-software
 rm -r ~/.local/share/gnome-software
```

I followed this and also in synaptic I reinstalled the gnome-software, now it is working fine.  thanks.

---

