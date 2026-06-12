---
title: "x2go remote sessions freeze"
date: 2020-11-24
forum: General Help
---

### Post by bloodyskullz on 2020-11-24
Hey,

New to linux and hoping someone can assist me. I have an intel nuc running a 6th gen CPU, 256GB SSD (i think nvme) and 4GB of ram. I install xubuntu and its updated to the latest version, zero tier so I can remote in from a computer on the same service and x2go.

When i do a remote session with x2go, at times it just freezes after I connect and I can't click anything or open anything. I am connecting using the only account on the box but the main machine is at the login screen. I thought it would fix it but didn't do the trick.

Inspite of all these issues, I can still do a session over SSH and navigate the CLI (very weak skills).

Any ideas in resolving this?

Thanks

EDIT: Can mods move this to general help? Thanks

---

### Post by TheFu on 2020-11-24
If you are new to Linux, then you should be running an LTS release like 20.04, not the latest development version which is basically for developers only at this point.  Sometime in March, testing of the next release by normal people will be appreciated.

Or did you post this thread in the wrong forum?

What is "zero tier?"
x2go uses virtual sessions and virtual desktops. Don't expect those to be displayed on the real hardware.
As for locking up, I've seen slowdowns with non-lite DEs like gnome3 and Mate.  My solution was to change to using fvwm which is crazy fast bcase t is very light.  May want to try openbox first if you are really new to linux.

BTW, saying you have the latest often doesn't mean the same to different people. **lsb_release -a** will say exactly which release so we don't have to hope or guess.

---

### Post by deadflowr on 2020-11-24
*Thread moved to **General Help***

---

### Post by ActionParsnip on 2020-11-24
If SSH works then you can use this guide to use VNC through an SSH tunnel. Works well
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

Question: what are you doing on the system that needs the full desktop? What do you do when you remote onto the server?

---

### Post by TheFu on 2020-11-24
> **ActionParsnip said:**
> If SSH works then you can use this guide to use VNC through an SSH tunnel. Works well
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

Question: what are you doing on the system that needs the full desktop? What do you do when you remote onto the server?

x2go is 2-3x faster than VNC and can be easily tuned for lower bandwidth connections.
If you have lots of bandwidth, use SPICE and qxl video drivers.

---

### Post by bloodyskullz on 2020-11-25
> **TheFu said:**
> If you are new to Linux, then you should be running an LTS release like 20.04, not the latest development version which is basically for developers only at this point.  Sometime in March, testing of the next release by normal people will be appreciated.

Or did you post this thread in the wrong forum?

What is "zero tier?"
x2go uses virtual sessions and virtual desktops. Don't expect those to be displayed on the real hardware.
As for locking up, I've seen slowdowns with non-lite DEs like gnome3 and Mate.  My solution was to change to using fvwm which is crazy fast bcase t is very light.  May want to try openbox first if you are really new to linux.

BTW, saying you have the latest often doesn't mean the same to different people. **lsb_release -a** will say exactly which release so we don't have to hope or guess.

I am using the LTS release of ubuntu and when I say updated, I mean all the latest patches are installed. Exact output of the command you stated:


"No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal"

zerotier: [https://www.zerotier.com/](https://www.zerotier.com/)

Handy service for being able to connect to a machine you own from anywhere so as long as both devices using the session are on the same zerotier network (free).

Now I noticed that if I close the session and go back in, it will not allow me to initiate anything at all (open a browser etc..). However if I log out and then go back in, everything works fine. I am trying to have it where if I just close an x2go session, I can resume at any point and proceed where i left off.

@[COLOR=#000000]ActionParsnip: I am using this if I need to see something on my home network. I can't use a service like teamviewer since they think it's commercial usage for some weird reason. Connecting to my linux box over zerotier through SSH allows me to bypass everything.[/COLOR]

---

### Post by ActionParsnip on 2020-11-25
OK...what do you do on the remote system once you are connected? There may be a sleeker solution to what you are doing / wanting to achieve

---

### Post by TheFu on 2020-11-25
So, you aren't directly connecting to your remote system with x2go?
Can you directly connect to your remote system using X11-forwarding?

```
ssh -X username@server xterm -sb &
```
Give it upto 2 minutes for the xterm to be displayed on your local Linux workstation.
If that doesn't work and the xterm program exists, we need to look at other issues.

I am seeing that a password is required sing x2go even when I have ssh-key based authentication setup between the client and server (20.04) that works well.  This is unacceptable to me.  x2go works correctly/as expected with ssh-keys to other systems, just not 20.04.

---

### Post by bloodyskullz on 2020-11-25
> **ActionParsnip said:**
> OK...what do you do on the remote system once you are connected? There may be a sleeker solution to what you are doing / wanting to achieve

Normally I use teamviewer to assist my family at home while on the road/work with their issues if I have some time available. Since teamviewer tightened up their services, my work around was to connect to a linux box via zerotier and x2go, then use teamviewer to the problematic systems and see what is happening.

At the same time, i would be using my own machine when on TV to see my home network, make sure things are running from time to time. I had to find an alternative that was free and this was the best I could do.

I like setup I did for it all but if there is a better way to manage everything then I will try it out. In the end im still trying to figure out why this issue is happening.

---

### Post by bloodyskullz on 2020-11-28
Anyone?

---

### Post by TheFu on 2020-11-28
> **bloodyskullz said:**
> Anyone?

Still waiting for answers to my prior questions.

---

### Post by bloodyskullz on 2020-11-29
> **TheFu said:**
> Still waiting for answers to my prior questions.

Wow, I overlooked it. Just to be clear, am I running this from another machine:

"[COLOR=#000000][FONT=&quot]ssh -X username@server xterm -sb &"

I don't have another linux box.[/FONT][/COLOR][COLOR=#000000][/COLOR]

---

### Post by bloodyskullz on 2020-12-05
> **TheFu said:**
> Can you directly connect to your remote system using X11-forwarding?

```
ssh -X username@server xterm -sb &
```
Give it upto 2 minutes for the xterm to be displayed on your local Linux workstation.
If that doesn't work and the xterm program exists, we need to look at other issues.

This post is a little confusing to me. Am I just starting a new session on Windows with the mobaxterm and typing in that command you mentioned? Or are there additional steps involved?

Thanks

---

### Post by TheFu on 2020-12-05
The local machine must run a local X/server and support ssh w/ x11-forwarding. 

Any Linux/Unix workstation with X does. You can run a tiny Linux (16MB) distro for this (booted or inside a VM), if you don't have it on Windows. 20+ yrs ago, this was possible on Windows using a commercial X/Server.  I found it more hassle than just running a small VM with tinycore linux, which provided a better overall experience and better X/Server for free.

Anyway, solve it however you like.  If ssh -vvv works well, then ssh -X should too. If not, there probably are some missing configs that x2go needs too.

---

### Post by bloodyskullz on 2020-12-05
So I ran the command from a centOS VM that I forgot about and I got the result attached.

Am I missing something?

EDIT: Ran the command via moba and nothing happened.

---

### Post by bloodyskullz on 2020-12-09
Anyone else have ideas on where to look for a fix?

---

### Post by sinigal on 2021-01-26
I had a similar problem. After a short downtime, the session freezes.
I solved this problem by disabling the screensaver and turning off the screen in the power settings and removing the xfce4-screensaver package (sudo apt remove xfce4-screensaver and reboot).

---

