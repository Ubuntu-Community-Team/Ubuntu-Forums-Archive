---
title: "Restart synaptics"
date: 2008-05-17
forum: General Help
---

### Post by minus198 on 2008-05-17
Hi,

Some random times, the scrolling part of my laptops touchpad, all of a sudden stops working. The only think that works to solve this, is to restart X.

But I don't want to be forced to do that a couple of times a day. So my question is: Is there a way to restart Synaptics without restarting X?

---

### Post by ibuclaw on 2008-05-17
If you can, Hit "**Alt+F2**" and the Gnome Run Application Applet will popup.

Type into the textbox:
```
killall synaptic
```
Then press "Enter" to execute that command.

Test it to see if that fixes it.

[EDIT]
If that fails...
```
gksu killall synaptic
```

Regards
Iain

---

### Post by minus198 on 2008-05-17
> **tinivole said:**
> If you can, Hit "**Alt+F2**" and the Gnome Run Application Applet will popup.

Type into the textbox:
```
killall synaptic
```
Then press "Enter" to execute that command.

Test it to see if that fixes it.

[EDIT]
If that fails...
```
gksu killall synaptic
```

Regards
Iain

You are thinking of "Synaptic package manager". I'm thinking of Synaptics. The program that controls the touchpad on laptops.

---

### Post by ibuclaw on 2008-05-17
](*,)#-o:roll:

Oops...

Sorry, I seem to have misplaced my synapse.

Erm...
Open a terminal and type in:
```
ps -e | grep synaptics
```
Then killall the name of that app instead.

It's hardware, right?
If you can find out which module is controlling the device. Then a simple:
```

sudo rmmod <device>
sudo insmod <device>

```
Should do the trick too...

Again, sorry.
Regards
Iain

---

### Post by stldirty on 2008-05-31
none of this has worked for me.  any other solutions?

---

