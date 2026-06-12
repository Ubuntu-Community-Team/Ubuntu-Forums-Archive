---
title: "[SOLVED] Control Computer Without Viewing On Local"
date: 2007-08-28
forum: General Help
---

### Post by prince_niceguy on 2007-08-28
Here is the scenario I am having.

I am having two laptops. One is running XP (Company Laptop) and another one Ubuntu (Personal Laptop). Ubuntu being my primary work laptop.

However the XP laptop is connected to a docking station and to a huge monitor. I am able to VNC from ubuntu to XP. It is running great no issues.

However, there is simply too much traffic between xp and ubuntu as I VNC displays the same thing which I am viewing on the huge monitor.

Is there  a way I connect to vnc server and not get back the screen refreshes. I will manage the same from the huge monitor.

I am out of my wits how to do the same.
Thanks in advance...

---

### Post by prince_niceguy on 2007-08-30
bump....

any one???

---

### Post by bmorency on 2007-08-30
> **prince_niceguy said:**
> 

However the XP laptop is connected to a docking station and to a huge monitor. I am able to VNC from ubuntu to XP. It is running great no issues.

However, there is simply too much traffic between xp and ubuntu as I VNC displays the same thing which I am viewing on the huge monitor.

Is there  a way I connect to vnc server and not get back the screen refreshes. I will manage the same from the huge monitor.

I am out of my wits how to do the same.
Thanks in advance...

I just need something to be a little clearer.  you are using vnc to connect to xp from ubuntu. you said it works great.  i am not sure exactly what you mean by do not want to get the screen refreshes back? also what do you mean to much traffic between the two systems? what kind of traffic?

---

### Post by prince_niceguy on 2007-08-30
computer A laptop with Dock and a big external monitor windoze on it.

computer B laptop with ubuntu.

Refer to the open office impress document attached.

I do not want to view the screen refreshes on computer B as I am already seeing them directly on computer A's external monitor.

Hope I am explaining properly. 

The traffic I am referring to is a VNC traffic from compA to compB which I can avoid as I want to use my compB as just as a dumb terminal with keyboard and mouse input.

---

### Post by prince_niceguy on 2007-09-04
bump...

any idea.. how this can be done???

---

### Post by cwaldbieser on 2007-09-05
> **prince_niceguy said:**
> bump...

any idea.. how this can be done???

If I am understanding what you want to do correctly, I think the simplest solution would be to just  get a wireless mouse and keyboard.  I don't think you can choose to "shut off" half of the network communication of VNC.

---

### Post by prince_niceguy on 2007-09-17
I solved it... I am using x2vnc...

I installed vnc on the computer with windows and i run x2vnc on my ubuntu... now i am able to use the key board and mouse of my laptop to control the windows computer...

---

