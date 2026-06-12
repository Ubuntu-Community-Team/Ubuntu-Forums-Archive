---
title: "XGL / Compiz when on battery"
date: 2007-07-19
forum: General Help
---

### Post by Yoeri on 2007-07-19
Is there a posiibility to change the GNome session depending on the state of the laptop when booting?
When I boot on battery, I want it to start up without XGL/Compiz loaded. XGL/Compiz can be loaded when on net power.

---

### Post by overdrank on 2007-07-19
> **Yoeri said:**
> Is there a posiibility to change the GNome session depending on the state of the laptop when booting?
When I boot on battery, I want it to start up without XGL/Compiz loaded. XGL/Compiz can be loaded when on net power.

Hi when you login  when on battery then don't choose xgl. Then once your are logged in you can disable comp-fusion. Just a thought.

---

### Post by maino82 on 2007-07-27
i'm curious about this too.... is there a way to do this automatically instead of having to manually make sure you don't boot into xgl and then manually disable compiz? i also like using awn in compiz and the gnome taskbar in a regular gnome session, so swapping out between those two automatically would be cool too, although not necessary. 

the power manager can detect if the power is plugged in or not, so it seems like you should be able to use that to trigger turning on and off compiz/beryl/compiz fusion automatically. does anyone know how that might be setup? i'm by no means a programming guru and am not really much of a power user, so i don't know where to start, but any sort of tidbits of information you might be able to help would be appreciated!

---

### Post by zanglang on 2007-07-27
Hmm, maybe you could use DBUS to hook into Power Manager. It should generate some sort of event when it changes from battery to charging state.

Edit: Alright, DBus script tested and done. When the AC power status changes Power Manager sends out an OnAcChanged DBus signal, which is easy to subscribe to and read. Now, I'm not a long-time Compiz Fusion user, so what is usually the best way to stop or restart XGL/Compiz safely and elegantly? Or do I just kill the process?

---

