---
title: "Teamviewer unable to control Ubuntu 15.04 remotely"
date: 2015-04-27
forum: General Help
---

### Post by D00mM4r1n3 on 2015-04-27
Hello, I recently did a clean install of Ubuntu 15.04. Installed all updates and the AMD proprietary driver (gfxlr-updates?). After that I only installed 2 programs: Teamviewer 10 and KVPM (partition manager used for managing LVM volumes). Teamviewer installed without error and I was able to open and log in to it. From my Windows 8.1 machine I installed Teamviewer 10 and logged in then tried to connect remotely to the Ubuntu machine. It connects and I can move the mouse around, but the screen never updates. In other words, if I click to launch a program on the Ubuntu machine, I never see the program launch over the remote connection. If I walk over to the Ubuntu machine I can see it did launch though, it just is not updating the screen remotely. I had no problems with Ubuntu 14.04 and Teamviewer 9, this only stopped working with Ubuntu 15.04 and Teamviewer 10.

So far the only thing I have tried is making sure I enabled remote access in the Ubuntu system settings.

Is anyone able to connect successfully to a machine running Ubuntu 15.04 from a Windows machine?

---

### Post by kristoffer3 on 2015-05-25
Hello

I have the same problem as you. Did you find any fix for it ?

---

### Post by ShinXero on 2015-06-10
I'm having the exact same problem.
I tried some alternatives, even tried resorting to X11 forwarding, but that doesn't seem to work well when connecting from a Windows client at work.
Also, when trying to use vnc or RDP-protocol, I get a grey screen with an "X" as a cursor which disconnects almost immediately.

At first I thought it was the Mir displayserver, but that apparently didn't make it into the 15.04 edition.

I've been distro-hopping for quite some time, thinking to switch back to fedora or debian for this particular reason.
I need to be able to log into a graphical session over the internet.

Is anyone else experiencing this??
Are there any known solutions for this?

Help?? :-)

---

### Post by Geoffrey_Arndt on 2015-06-11
See post #3

[http://ubuntuforums.org/showthread.php?t=2280649&p=13297563&highlight=Team+Viewer#post13297563](http://ubuntuforums.org/showthread.php?t=2280649&p=13297563&highlight=Team+Viewer#post13297563)

---

### Post by Carlos_Eduardo_Gel on 2015-06-24
Hi, 
I'm having the same issues with amd/ati proprietary driver, ubuntu 14.04 and teamviewer, the solution I found is no solution to this at all, that is, I had to choose between having graphics acceleration or teamviewer.

I remove the proprietary driver from amd/ati and teamviewer works flawlessly. Since I wouldn&#8217;t be doing much of a 3D work, I accept that. But now I need to do some tests with Blender and cloth simulation, and I'm afraid I will get performance issues.

Anyone, so far make the three work together? 

I'm guessing that I will have to get some nvidia card.

---

### Post by FarSight87 on 2015-11-01
> **D00mM4r1n3 said:**
> Hello, I recently did a clean install of Ubuntu 15.04. Installed all updates and the AMD proprietary driver (gfxlr-updates?). After that I only installed 2 programs: Teamviewer 10 and KVPM (partition manager used for managing LVM volumes). Teamviewer installed without error and I was able to open and log in to it. From my Windows 8.1 machine I installed Teamviewer 10 and logged in then tried to connect remotely to the Ubuntu machine. It connects and I can move the mouse around, but the screen never updates. In other words, if I click to launch a program on the Ubuntu machine, I never see the program launch over the remote connection. If I walk over to the Ubuntu machine I can see it did launch though, it just is not updating the screen remotely. I had no problems with Ubuntu 14.04 and Teamviewer 9, this only stopped working with Ubuntu 15.04 and Teamviewer 10.

So far the only thing I have tried is making sure I enabled remote access in the Ubuntu system settings.

Is anyone able to connect successfully to a machine running Ubuntu 15.04 from a Windows machine?

I am also having the same problem.

I am trying to remotely access a computer running Ubuntu 14.04 LTS with latest Teamviewer 10 installed (multiarch) + Radeon HD5450 with fglrx. I have tried accessing it from my Win 10 machine with latest TV10 + Radeon R9 270X, another Ubuntu 14.04 LTS TV10 (multiarch) machine + Radeon HD6850 with fglrx and also my android phone.
The connection works perfectly. The desktop is displayed as normal. The problem is, the desktop is not live updated to the the computer im using to remote login from. Anything i click on or move around actually works on the remote computer, but nothing is shown on my computer. It just looks like a frozen desktop but with a movable cursor. If I disconnect and then reconnect, I can see what I have done while blindly clicking around.

The two computers I am using to try and remote login to the first computer, are both able to login to each other and work perfectly, aswell as with my android phone. 

Driving me crazy.

---

### Post by EnterG on 2016-06-24
May sound weird but worked for me . 
Go to Teamviewer Extras>Options>Remote control>choose quality custom settings>custom settings>and tick improve application compatibility.

---

### Post by oldos2er on 2016-06-24
Old thread closed.

---

