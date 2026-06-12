---
title: "Slim down background apps in Xubuntu or Ubuntu"
date: 2007-01-27
forum: General Help
---

### Post by mike_m on 2007-01-27
I installed Ubuntu 6.10 on a Dell cpx 650mz laptop with 512 ram,
It runs good but the USB mouse is sometimes lagging so I used Synaptic to get Xubuntu thinking it would run less things in the background, but the mouse still lags sometimes. so I uninstalled all the bluetooth stuff & OpenOffice & email programs, stoped the cups & hp printers, activity logs, actions schedulers, power mangment (only run from AC - Battery is dead)

 - what else runs in the background that I can uninstall or stop? 

The mouse lag isn't that bad, but would like to speed it up.

PS I must run Gkrellm for the Dell fan, but turned off all other options on it.

Thanks

---

### Post by kerry_s on 2007-01-27
Just open synaptic, click on status(left bottom corner), then on installed and just slowly work your way down the list and uninstall what you don't need. I'll usually go for the obvious stuff, say like all the fonts in languages i'll never use, all the xorg-drivers except vesa(i use nvidia,vesa is backup), extra kernels, themes i'll never use, etc....
Make sure in synaptic>settings, check the box under apperance so you can see the description of the item and the common tab will tell you the priority(optional,extra,common,standard,required,important) if your not sure look it up on the web, google is your friend. :D

---

### Post by Insomniac20k on 2007-01-27
Perhaps there's a better driver for the mouse?

---

### Post by mike_m on 2007-01-27
Thanks those are good ideas, the mouse came with a cd but I'm sure it's only for windows so I can't use it right? 

I was going to look for a faster window manager but the posts I read say that Xfce is the fastest
Funney of all the linux's I've tried Ubuntu is the only one that my SMC wifi card will work with "out of the box" and all the others I couldn't config it to run at all, but I'm a n00b.

Thats ok, I like Ubuntu!

---

### Post by mike_m on 2007-01-28
Solved it, I reinstalled Ubuntu & manualy set the swap to 1 gig, the first install had the swap set to 256 megs

Thanks for all the help :)

---

