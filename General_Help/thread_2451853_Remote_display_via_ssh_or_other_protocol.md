---
title: "Remote display via ssh or other protocol"
date: 2020-10-12
forum: General Help
---

### Post by yasha312 on 2020-10-12
to start i am not looking for vnc, also not looking for x11 forwarding as i have been able to set up. 

simple question:
i want my local shell to display any xserver requests on remote display

long question:
     setup:
          raspberry pi physically attached to a physical display, no keyboard, no mouse
          local machine with all, display, mouse, keyboard, nuke warhead, all the good stuffs

     request:
           i would like to have local shell's x requests display on remote display. NOT on both "x11 forwarding" i can look "over 
           there" to see it. 

     extra credit:
          i would like to be able to capture local xinput and send to remote xserver with keyboard interrupt to 
          return to local xserver

    if im asking this the wrong way pls inform

---

### Post by EuclideanCoffee on 2020-10-12
Have you tried x2go? It has its own server and client. You'd install the server on the Raspberry Pi and the local machine you use with a client.

---

### Post by ActionParsnip on 2020-10-12
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)
Works for me

---

### Post by Holger_Gehrke on 2020-10-12
Could [barrier]("https://github.com/debauchee/barrier") be what you're looking for ? It's basically a keyboard and mouse switch in software. The mouse pointer can be moved from one display to the other, the keyboard input goes to whatever display the mouse pointer is in ... I'm using this between my Raspberry Pi 4 and my XUbuntu machine and it works quite nicely.

Holger

---

