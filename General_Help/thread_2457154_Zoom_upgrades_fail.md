---
title: "Zoom upgrades fail"
date: 2021-01-26
forum: General Help
---

### Post by CowDoctor on 2021-01-26
Dear Friends,   Please bear with this less than tech savvy person.  I need to use Zoom a lot and now every time I try to upgrade I get a message from the software installer that says "failed to install file:not supported"  This is frustrating.  Earlier I got a tech from Zoom to show me how to do it from the terminal after he sent me the installation file, but it's a pain.  Anyone know how to fix this so I just download it normally???  20.04.1 LTS

---

### Post by wildmanne39 on 2021-01-26
*Thread moved to **General Help for a more appropriate fit**.*

Here is a link that details how to install zoom on 20.04.

[https://linuxize.com/post/how-to-install-zoom-on-ubuntu-20-04/](https://linuxize.com/post/how-to-install-zoom-on-ubuntu-20-04/)

If you already have it installed uninstall the old version first, it is very unlikely that an installation file from zoom support will install on Ubuntu, most non-linux tech support know nothing about what is required to install a program on linux or how to go about it.

Why do you need to upgrade zoom is it not performing well? I hope the version here is a newer version then the one you have installed you did not give enough information for us to be of much help.

---

### Post by &amp;KyT$0P# on 2021-01-26
> **jjsnyder@uci.net said:**
> Earlier I got a tech from Zoom to show me how to do it from the terminal after he sent me the installation file, but it's a pain.  Anyone know how to fix this so I just download it normally??? 

Using the Terminal **is** the normal way.  I don't think that "software installer" handles this type of software.

---

### Post by QIII on 2021-01-27
Zoom isn't included in Canonical's repos so far as I know, so you can't just install it from the Software installer or Synaptic.  I install it from the .deb via the terminal (I'd rather not, but hey, the clients want to Zoom).  You might be able to install gdebi or something like that if you want a GUI-ish way.

---

### Post by cmcanulty on 2021-01-27
This method worked for me in 20.04, very easy

[https://linuxize.com/post/how-to-install-zoom-on-ubuntu-20-04/]("https://linuxize.com/post/how-to-install-zoom-on-ubuntu-20-04/")

---

### Post by grahammechanical on 2021-01-27
The Software app in Ubuntu 20.04 does have zoom-client in it. A snap version of Zoom-client will install. Every time we run Software Updater Snap applications get updated if there is an update to the snap. Right now, on my 20.04 the snap version of zoom-client is at 5.4.5. This compares to what the zoom web site is offering to Ubuntu users. It is version 5.4.9. And it is a deb version. 

These are the Zoom instructions for installing zoom-client.

[https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux](https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux)

There is no mention of how to upgrade. The install is not from a repository but from a downloaded file. Therefore, as stated above, the way to upgrade would be to uninstall the existing version and download the newer version and then install that.

Regards

---

