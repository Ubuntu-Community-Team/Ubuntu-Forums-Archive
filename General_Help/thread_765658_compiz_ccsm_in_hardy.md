---
title: "compiz ccsm in hardy?"
date: 2008-04-24
forum: General Help
---

### Post by doctorgreg on 2008-04-24
I just put hardy on my laptop using wubi and compiz works right away without any screwing around but i notice that there is no ccsm to manage the compiz plugins.

---

### Post by grannyw on 2008-04-24
you need to enable repositories for ccsm
system>administration>software sources

---

### Post by doctorgreg on 2008-04-24
i tried to update everything this morning but i was getting a bunch of errors and i could not update nothing

---

### Post by overdrank on 2008-04-24
> **doctorgreg said:**
> i tried to update everything this morning but i was getting a bunch of errors and i could not update nothing

Ok could you post the errors. Also have you tried to update via the terminal?

---

### Post by doctorgreg on 2008-04-24
i am at work right now so I will be home in about 2 hours and i will try a few things again and then get back to you....Thanks

---

### Post by andrewsomething on 2008-04-24
CCSM doesn't come with Ubuntu by default. Install compizconfig-settings-manager in you package manager (ie Synaptic) or type this in the terminal:

     ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by doctorgreg on 2008-04-25
ya i got it now. Jus got it from synaptics after I did all my updating first.

---

### Post by dyr on 2008-04-25
I used

```
sudo apt-get install simple-ccsm
```

but I dont know if this is very different.

---

