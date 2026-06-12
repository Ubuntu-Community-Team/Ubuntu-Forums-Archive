---
title: "Noisy fans"
date: 2008-03-27
forum: General Help
---

### Post by bekmand on 2008-03-27
Hello

I'm having a "noisy" problem, my ASUS F5V is running with Ubuntu 7.10 and i notice that the fans are going crazy when i work on it, i thought that it was normal, but when i shutdown anything that should use my CPU, the fans are still working 100% is there a way to manipulate the fans or is there another trick that you can do?

Please help me and thanks in advance

-Bekmand

---

### Post by Ub1476 on 2008-03-27
The fans start running when your computer becomes warm/hot. Certain laptops (quite many actually) just is very warm whatever you do, even though cleaning dust from computers might help. If you have an Intel processor, you can install **powertop** and run it in terminal:

```
sudo powertop
```

This program collect info from your computer/OS and suggest changes to be made to get better battery life and such, sort of connected to warm computers..

The fans should also have free access to air, so if it's on a pillow, or sometimes even on a table, it can become very warm (if it's on a pillow it will likely overheat).

---

### Post by bekmand on 2008-03-27
Hey Ub1476

Thank you for the reply, but it dont now what i can do with that data

i'm getting

Wakeups-from-idle per second : 648,3 interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups

48,1% (259,3) <interrupt> : wifi0, fglrx
and somemore

but that is the one that is using the most CPU (i think)
but again, what can i do with these datas, can i shut'em down or can i reduce their usage or something

Thanks in advance

-Bekmand

---

### Post by Ub1476 on 2008-03-27
Wifi is necessary I suppose, and fglrx is the graphic driver. Powertop should give some suggestion for other thing to disable/change though?

---

### Post by bekmand on 2008-03-27
hmm, didn'y see that one ^^ but thanks mate think its working now, but there is something that i'm concerned about and that is "PS/2 keyboard/mouse/touchpad" sometimes it takes 30%! but after sometime it goes down to 1,2% is this okay, or should i do something about that?

Thanks again mate

---

### Post by Ub1476 on 2008-03-27
Well, I have sort of the same:

```
 39.6% (497.7)      <kernel IPI> : Rescheduling interrupts 
  38.6% (485.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   5.8% ( 73.6)       <interrupt> : extra timer interrupt 
   4.2% ( 53.0)       <interrupt> : HDA Intel 
   2.1% ( 26.6)              Xorg : schedule_timeout (process_timeout) 
   1.6% ( 20.1)       <interrupt> : iwl3945, uhci_hcd:usb3, firewire_ohci
```

I suppose there's not much to do about it. In other words, it's kinda normal.

---

### Post by fragos on 2008-03-27
Cheap fans are frequently noisy.  The sound comes from the bearings and not so much from the movement of air.  A quality low noise fan isn't very expensive.  You might also find the sound will be cut down if the computer sits on a soft material that doesn't transfer vibrations.

---

