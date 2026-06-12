---
title: "Touchpad weird behaviour"
date: 2013-10-14
forum: General Help
---

### Post by m4wdfNy on 2013-10-14
Hello all, I'm new here and I registered my username this evening. So I take this chance to hail you all and to thank you for every help you could give me. I hope to become good enough to give help by my hand, in future ;)

Anyway, my touchpad seems weird. I use Lubuntu 13.04 on an Asus eeePc 1001PX. The touchpad works fine, but suddendly it stops behaving normally. The left and right hardware mouse button work fine, but using the touchpad himself scrolls the page instead of moving the mouse arrow, while tapping doens't work. A USB mouse connected works fine, while touchpad remains locked. 

The problem appears suddendly, after some hours of utilization, and rebooting Lubuntu fix the problem. 
Any idea?

---

### Post by varunendra on 2013-10-14
> **m4wdfNy said:**
> The touchpad works fine, but suddendly it stops behaving normally. The left and right hardware mouse button work fine, but using the touchpad himself scrolls the page instead of moving the mouse arrow, while tapping doens't work.
In almost two years of usage, I faced exactly the same problem for a few minutes on my Asus X54C laptop. I don't remember which of the two fixed it but it did.

**1)** Try removing and reloading its driver. Open a terminal (Ctrl-Alt-T) and run -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

**2)** If this doesn't change the behaviour, run this command -
```
xinput
```
..and see your touchpad is listed by exactly which name. For me, it is "ETPS/2 Elantech Touchpad" and its ID is 13 (keeps changing between 12 and 13 across reboots) and the "Virtual core pointer" it is attached to has ID 2 (never changes). So if the driver reloading fails, I would try this -
```
xinput float 13
xinput reattach 13 2
```

Note that you can also use the exact name within double quotes (e.g. "ETPS/2 Elantech Touchpad") if confused with IDs.

Of course this is not a fix but better than reboot while we can possibly find an actual 'fix' for the problem.

**PS:** Oh, and welcome to the forums ! :)

---

### Post by Scottie303 on 2013-10-14
Touch-pads are designed to work with a specific PSU. If you use an inferior laptop power cable (The block on there is the PSU)  your mouse pointer can start to do weird things and you can be clicking on the touch-pad when you don't intend to. It's something to do with 'capacitance ground effect' or something like that. I used to have an article on that but it has disappeared. Buy yourself a genuine cable for this particular Asus laptop and your touch-pad will work normally again.

---

### Post by YannosB on 2013-10-15
Would those commands also be akin to a tablet? ie: graphics tablet (non wacom)

---

### Post by Scottie303 on 2013-10-15
> **YannosB said:**
> Would those commands also be akin to a tablet? ie: graphics tablet (non wacom)

I thought that would be quite likely, so I did a quick search.

Here Someone writes about ['your touchscreen won't work when it's plugged into a cheap charger']("http://www.laptopgpsworld.com/4995-some-chargers-tested#post44648")

However, it might not **only** be a case of an inferior PSU. It might also be a problem of an inferior power supply from the wall.
Here: [Someone has poor supply from their solar panels]("http://www.laptopgpsworld.com/5022-touchpads-go-wonky-when-laptops-connected-mains-power-supply") Causing problems with "touchpads are very slow or difficult to move at all"

---

### Post by varunendra on 2013-10-15
> **YannosB said:**
> Would those commands also be akin to a tablet? ie: graphics tablet (non wacom)

Never used a tablet, so can't say. But one thing I can say confidently is that if they didn't work, they won't harm either (they may return errors if not applicable, but won't change anything).

---

### Post by m4wdfNy on 2013-10-20
Hi men, 
thanks to all for the help. I'm waiting for the trouble to appear. I'll keep you updated. 
Anyway, my PSU cable is the Asus original one!

---

### Post by m4wdfNy on 2013-10-22
> **varunendra said:**
> 

**1)** Try removing and reloading its driver. Open a terminal (Ctrl-Alt-T) and run -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```



This actually solved the problem! Thank you all, guys!

---

### Post by varunendra on 2013-10-22
Awesome! Hope you don't need it frequently though. :P

---

