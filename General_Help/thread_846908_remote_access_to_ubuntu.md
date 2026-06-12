---
title: "remote access to ubuntu"
date: 2008-07-02
forum: General Help
---

### Post by boblemur on 2008-07-02
hey sorry if this is in the wrong place, its a little bit of a few topics so i wasnt sure where to post...

my problem is im not home... and i really need to get to my computer using ubuntu, so far i have ssh access so i can run commands from the terminal and i have vnc enabled, however i cant login to it because its not loged in.

i was thinking i could setup auto login though ssh and then sudo reboot. but i wasnt sure how to do this... i know u can do it in gnome but i wasnt sure how to change the settings in terminal alone.

i have all the passwords to my computer, and i just need a way to make it login, so it can accept my vnc request... or find some why that i can enable vnc as a service so i dont have to login to ake it work, like windows rdc

thanks in advance :)

---

### Post by dcstar on 2008-07-02
> **boblemur said:**
> hey sorry if this is in the wrong place, its a little bit of a few topics so i wasnt sure where to post...

my problem is im not home... and i really need to get to my computer using ubuntu, so far i have ssh access so i can run commands from the terminal and i have vnc enabled, however i cant login to it because its not loged in.

i was thinking i could setup auto login though ssh and then sudo reboot. but i wasnt sure how to do this... i know u can do it in gnome but i wasnt sure how to change the settings in terminal alone.

i have all the passwords to my computer, and i just need a way to make it login, so it can accept my vnc request... or find some why that i can enable vnc as a service so i dont have to login to ake it work, like windows rdc

thanks in advance :)

Try System-Administration-Login Window and enable remote logins.

---

### Post by boblemur on 2008-07-02
yeh i can do that, but i dont have access to the desktop... only ssh access

---

### Post by sp0nge on 2008-07-02
I'm just getting into playing with SSH myself, but I believe you have to have it configured on your home machine in order to access it. If you haven't done that to this point, you're best bet will probably be attempting to connect via RDP or terminal services.

---

### Post by p_quarles on 2008-07-02
I can't really answer the question, since I've never used a VNC setup, but I wanted to make sure that you know you can use SSH to access the GUI on the remote system. This is known as X session forwarding, and is relatively easy to do, as well as having the security advantages of SSH.

---

### Post by boblemur on 2008-07-02
iv installed openssh-server which allows ssh access.... and i have that all setup and i can get to terminal on the other computer

my problem is i cant get to rdc or terminal client... because it requires someone to be loged in and then you can view their desktop

but i need a way to force it to login...

---

### Post by boblemur on 2008-07-02
yeh iv heard about this but how do i go about setting this up??

because im unsure of how where to start im still very new to ubuntu... sorry for posting b4 i didnt see ur reply

---

### Post by forger on 2008-07-02
Enable VNC?
Ubuntu hardy heron has built-in support for remote desktop:
System > Preferences > Remote Desktop

---

### Post by p_quarles on 2008-07-02
Make sure that X forwarding is enabled on the remote machine (in /etc/ssh/sshd.conf), and then run something like:
```
ssh -X server-location firefox
```
Or, if you wanted to forward an entire session, something like:
```
ssh -X server-location gnome-session
```
A link for further information (written for another distro, but everything except for installation is basically the same):
[http://gentoo-wiki.com/HOWTO_X-forwarding](http://gentoo-wiki.com/HOWTO_X-forwarding)

---

### Post by boblemur on 2008-07-02
alright sweet thanks :) ill give that a try, thank you for ur help

---

