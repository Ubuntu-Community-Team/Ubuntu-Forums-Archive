---
title: "How do I control dial up?"
date: 2007-11-18
forum: General Help
---

### Post by Poppyelvin on 2007-11-18
With the help of the forum I was finally able to get on line in ubuntu last night. But; now when I turn the computer on it dials up before I even log in. And I don't know how to tell it to hang up. I'm only used to IE which has a pop up when I open or close the browser. I'm using Mozilla Firefox now.

Poppyelvin

---

### Post by geraldm on 2007-11-19
You omitted important details.  OS ? 
You had to fill in information boxes for ISP information, number to dial, etc.  It was probably setup to dial upon boot, so it is being called from your bootscripts.  Dial up is usually in
directory /etc/ppp/   Perhaps you might remember from looking at information on the 
Desktop  System->Administration->Network.  Otherwise use the command runlevel, and 
see what number it returns.  Then look in /etc/rcX.d (X is the number runlevel returned)
That contains links that point to the scripts that are run.  The dialup ought to be found in
one of them.
Some users use scripts to dial out, and disconnect.  /usr/bin/pon to dial, and /usr/bin/poff to disconnect.

Gerald

---

### Post by Poppyelvin on 2007-11-19
Thank You gerald for your response to my cry for help. My OS is Ubuntu 7.04. I am new to the linux world. Most of your advice is over my head right now. I do hope to learn all about linux, but maybe the forum is not the best place to start. Maybe someone could suggest a good source. Thank You again.

Poppyelvin

---

### Post by Shazaam on 2007-11-20
Lol I have been there. First thing to do is open a terminal and run 
```
sudo apt-get update
```
This will update your package list. Enter your user password (cursor wont move, don't worry your password is there) and hit enter.
Since you have a working modem, open System>Administration>Synaptic Package Manager.
If you are using Ubuntu look for gnome-ppp. Check the box, go to the top and click Apply. Click apply again and it will download and install (maybe with other programs called dependencies) for you.
If you are using Kubuntu, go to the same place in Synaptic and look for kppp and install it.
Once it is installed, go to Networking, highlight your connection and click "Deactivate". Then go to Applications>Internet>GNOME-PPP, right-click, choose "Add this launcher to desktop". Click the icon, then go to configure and set up your ISP user info and such. Next time you boot (with the modem connection deactivated) it won't autodial. When you want to connect just click the desktop icon then connect. To disconnect click the network icon in your panel and choose Disconnect. Easy as pie.

---

### Post by Poppyelvin on 2007-11-21
Thank You Very much Shazaam!!! I just went through your instructions and everything is working great!!! just like you said. Thanks to you, we have one more success story.

Poppyelvin

---

