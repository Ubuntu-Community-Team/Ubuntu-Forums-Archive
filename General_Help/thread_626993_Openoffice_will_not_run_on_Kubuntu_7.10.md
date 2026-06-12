---
title: "Openoffice will not run on Kubuntu 7.10"
date: 2007-11-29
forum: General Help
---

### Post by kle on 2007-11-29
Acoording to the Kubuntu developers, cf. site 
[https://wiki.ubuntu.com/GutsyGibbon/Tribe5/Kubuntu#head-29f59dd33bcff20a2089978206587ea863d2a764](https://wiki.ubuntu.com/GutsyGibbon/Tribe5/Kubuntu#head-29f59dd33bcff20a2089978206587ea863d2a764), 
we cannot expect OpenOffice to open on Kubuntu 7.10. 
The promgram stalls on the spalsh screen and has to be killed. 

What Kubuntu users are recomended to do is to use the Openoffice.org-gnome version. 
Using apt-get, I have not been able to install the gnome version. The apt-get insists on iinstalling from the CD alternate from which I installed Kubuntu. 

I have disabled compiz, and that seems to solve my other crash problems (using an HP Pavillion laptop and recognise some of the problems described elsewhere on these pages). 

How to install the OO for Gnome?
And does OO for Gnome behave properly in Kubuntu?fi

Grateful for any help.

---

### Post by ptn107 on 2007-11-29
Try commenting out the line in your */etc/apt/sources.list* file that refers to your Kubuntu CD (should be at the top of the file).  Then do a quick:
```
sudo apt-get update && sudo apt-get install openoffice.org-gnome -y
```

---

### Post by kle on 2007-11-30
Thank you - it seemed a very good idea, but all I got was:

Reading package lists... Done
Building dependency tree
Reading state information... Done
openoffice.org-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And I don't have any trace of OO in my files. How odd!

---

