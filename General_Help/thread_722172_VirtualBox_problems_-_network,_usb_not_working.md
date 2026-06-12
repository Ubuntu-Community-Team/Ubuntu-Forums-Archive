---
title: "VirtualBox problems - network, usb not working"
date: 2008-03-12
forum: General Help
---

### Post by kiwited on 2008-03-12
In the last couple of weeks I have experienced difficulties with VirtualBox and Limewire.

VirtualBox no longer sees the network, and the USB devices are no longer available.

Additionally, Limewire no longer starts, and running in a terminal indicates a java problem.

I have been through all the fixits I have been able to find for the USB problem, which seems well documented. Trouble is, they don't work for me.

I have also downloaded and installed Java but this has not overcome the problem with Limewire.

All these things were working well until recently.

My system:-
AMD 6400+
Radeon HD 2600 XT video
SATA 350g HD

Thanks

---

### Post by {BzF}~JOKesTER on 2008-03-13
Ok So Lets Get Started:

To Try And Attempt To Fix The Java Problem.

Open A Terminal And Type:

apt-get remove limewire-basic --purge


Now Hit  Y And Then Enter.

Now Type:

apt-get autoremove

Now Hit Y And Enter.

Now Type:

apt-get autoclean

And Hit Enter.

Re-install Limewire!!!

You Can Do This By Typing:

apt-get install limewire-basic 

Hope This Helps!!!!:):)

---

