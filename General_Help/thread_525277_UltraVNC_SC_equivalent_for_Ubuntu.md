---
title: "UltraVNC SC equivalent for Ubuntu"
date: 2007-08-14
forum: General Help
---

### Post by amorangi on 2007-08-14
I use UltraVNC SC (Single click) to remotely support Windoze machines - it's great because the sever initiates the connection and there's no router configuration (ie port forwarding) required on behalf of the user at the other end. 
Does anybody know of an equivalent process for Ubuntu that the end user can initiate the connection to my machine with very little knowledge required? I'm setting up some of my more adventurous friends (read: windows keeps failing for them over and over again), but they need occasional help, and it hurts my brain to talk them through port forwarding on their router and the various settings on Ubuntu.   
I do use a dyndns address for the UltraVNC program for it to locate me, so I'd even appreciate a solution that was as straightforward as getting them to type in a command along the lines of getsupport myaddress.dyndns.org in terminal.

---

### Post by john8791 on 2007-08-24
> **amorangi said:**
> I use UltraVNC SC (Single click) to remotely support Windoze machines - it's great because the sever initiates the connection and there's no router configuration (ie port forwarding) required on behalf of the user at the other end. 
Does anybody know of an equivalent process for Ubuntu that the end user can initiate the connection to my machine with very little knowledge required? I'm setting up some of my more adventurous friends (read: windows keeps failing for them over and over again), but they need occasional help, and it hurts my brain to talk them through port forwarding on their router and the various settings on Ubuntu.   
I do use a dyndns address for the UltraVNC program for it to locate me, so I'd even appreciate a solution that was as straightforward as getting them to type in a command along the lines of getsupport myaddress.dyndns.org in terminal.

Remote Desktop access is setup in Ubuntu at System->Preferences->Remote Desktop.  I use Hamachi and it's front end GHamachi to set up a VPN.  Works even through most routers with no problems.  I can access my Ubuntu desktop remotely with a Windows machine using TightVNC client and vice versa using xvncviewer.  I installed Hamachi with Automatix, and got gHamachi from  [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/).  Had to use the beta version to get it to works.  Here is Hamachi's main site: [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/)

---

### Post by amorangi on 2007-08-26
Thanks, I'll give it a try.

---

### Post by john8791 on 2007-08-26
Oops.  Just realized I duplicated the URL to the gHamachi page.  The main Hamachi page is:
[http://logmein.com/products/hamachi/vpn.asp?lang=en](http://logmein.com/products/hamachi/vpn.asp?lang=en)

I'm sure you figured it out but just wanted to correct myself.

---

### Post by belda on 2008-03-01
you can use the reverse vnc

on the it support machine run 
```
vncviewer -listen
```

and on the machine, that needs help just type
```
x11vnc -connect ip
```

it would  be nice, to implement this in the dialog box, or create something like, remote support...

---

