---
title: "Question about running windows software"
date: 2007-09-04
forum: General Help
---

### Post by FullAuto on 2007-09-04
I am a Windows user converting to Ubuntu. The reason I decided to transfer over was because of issues I was having in relation to a particular software application that I was running on my laptop (crashing, freezing, etc.). I realized that there was a Linux version of this software and decided to give that a try.

Where I ran into the next issue was when installing it. To install/run the application, you need to have a "license server" installed and running. There are two ways to use the license server, locally and remote:

Local: You can install the license server on the same machine that you want to run the application. The license server runs in the background.

Remote: The license server can be installed on another machine and you can utilize it from another computer to run the application by inputing the address of the "host" machine.


I could connect my laptop to my windows desktop via network connection. Then, I could run the license server on the desktop machine and use it to run the software on my laptop via hostname of the desktop computer with the server license running. The thing is, there would be no point as if I was that close to my desktop I would just run the software on there.

So now I am trying to figure out how to run the license server exclusively on my laptop. I am aware of "VMWare" and have been looking into it although I have not found the answers to all my questions during my research. If I could maybe run Windows within my Ubuntu environment, maybe I could run the license server that way. There are three things I am wondering about now:

1. Is it possible for me to install and run the license server using some kind virtual environment?
2. If my only option was to run Windows within Ubuntu, could my Ubuntu applications communicate with my Windows applications as if they were on separate machines communicating over a network?
3. Is the performance of my Ubuntu applications going to suffer severely because of the added strain from running Windows simultaneously?

If anyone has any insight they'd like to share, I would like to hear it.

Thanks.

PS: if it matters, the software I want to run is Softimage|XSI.

---

### Post by gavinjb on 2007-09-04
Hi,

You might want to investigate VirtualBox ([www.virtualbox.org](www.virtualbox.org)), I don't know if you can get ubuntu to see the apps/services working on VirtualBox, but it might be worth looking at, as for memory I only use virtualbox to run a few apps (mainly VB.net, ASP.net, and Photoshop CS3) but I have 2GB of ram and have 800mb allocated to VirtualBox and find that Ubuntu stills runs at an exceptable speed (better than XP did with on the machine)

Alternativly you could look at VMWare, or if you can run the Windows services through WINE (unlikly)

Gavin,

---

