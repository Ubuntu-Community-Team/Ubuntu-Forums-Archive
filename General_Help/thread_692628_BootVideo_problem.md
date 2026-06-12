---
title: "Boot/Video problem"
date: 2008-02-09
forum: General Help
---

### Post by Walruss on 2008-02-09
Hi all,

Just recently upgraded my system to a AMD AM2 4800+, with a Gigabyte mainboard and a 256 mgbyte Radeon HD 2400 Pro video card. I try booting up, and it gives me a video error; here's the full report

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
build Operating system: Linux Ubuntu
current Operating system: Linux Al 2.6.20-16-generic #2 SMP Tue Dec 18
 

actualy that stuff isn't really relevent, it goes on to talk about what markers mean, then just gives me this:

Fatal server error:
no screens found                           f''


then an ok option. i hit that


and it asks me if I want to view the detailed x server output as well. 
that has an error

(WW) The directory ''/usr/share/fonts/x11/cyrillic'' does not exist.
Entry from deleted font path and then it goes off and finds it,

Finishing the page with a new error 

(EE) No devices detected

Fatal server error:
no screens found


I hit ok there, it comes with 
"The X server is now disabled. Restard GDM when it is configured properly."

I then get a command-line operating system, and considering i don't know how to use it, I'm a little stuck. How do I configure the X server to work with my new PCI-E graphics card??
Can Ubuntu see PCI-E slots???

---

### Post by taurus on 2008-02-10
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Walruss on 2008-02-10
k, I'm in the xserver reconfig... thanks guys.

---

### Post by Walruss on 2008-02-10
ok, need a step-by-step guide to reconfiguring the damn thing please. I don't understand all of it.

---

### Post by taurus on 2008-02-10
If you are not sure about a question, just take the default.  Pick **vesa** driver for your graphic card for now until you get X up and running again.  Then, install a driver for your graphic card.

---

### Post by Walruss on 2008-02-10
it, err, still fails to boot properly...

---

### Post by taurus on 2008-02-10
What is the error message this time?

---

