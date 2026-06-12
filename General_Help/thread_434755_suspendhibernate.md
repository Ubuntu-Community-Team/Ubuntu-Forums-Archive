---
title: "suspend/hibernate"
date: 2007-05-06
forum: General Help
---

### Post by spx3 on 2007-05-06
hello
i wonder if i can use suspend/hibernate on my laptop
i have ubuntu 6.10 edgy with xfce4 running
i also do have to mention that for my mouse to work i modified
menu.lst for grub and added this "noapic irqpoll pci=routeirq",does
this have to do with suspend/hibernate not working at all ?
how can i make them work ?
thank you

---

### Post by Snowcat on 2007-05-06
You didn't say what model laptop you have.

Check here:[ https://wiki.ubuntu.com/LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam") for your model.
Maybe someone got it to work.

Hope that helps!

---

### Post by spx3 on 2007-05-06
this is as close as it gets to the laptop im workin
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProL10](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProL10)
to quote it
" Hibernates? Yes, next reboot gives me back my Gnome session Yes
 Sleep Yes, suspends to RAM Yes "
ok great so i probably have functionality
how do i get it to sleep/hibernate/suspend ?
from the console preferably
but from xfce its also ok

---

### Post by mdwuznik on 2007-05-06
The easiest way for me was to use gnome-power-manager. AFAIK you may use it under xfce too. 
I configured my laptop to go to sleep after pressing the power button. Of course there are more sophisticated ways to do that, that was the easiest for me.

Cheers
Michal

---

