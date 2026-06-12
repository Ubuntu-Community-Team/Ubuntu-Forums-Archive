---
title: "VMWare Workstation"
date: 2007-04-15
forum: General Help
---

### Post by cris on 2007-04-15
I downloaded the archive from vmware.com , unpacked it , and when i get to the installation , it gives me an error message. 
When i do : sudo ./vmware-install.pl    i get this message :
"A previous installation of VMware software has been detected.

Failure

Execution aborted."

I had vmware player but it was uninstalled.

---

### Post by lotacus on 2007-04-15
:) I just finished installing this a few hours ago with your exact problem. However, I forget how I fixed it. LOL

The steps I tried was first, uninstalling through automatix. Then I loaded up synaptic and did a search for vmware. Low and behold synaptic had show vmware to be still installed. I removed all packages BUT xserver-xorg-video-vmware and made sure that NO hidden directories where still on the system ie: ~/.vmware. If it was there I would open console and type sudo rm -R ~/.vmware.

After you made sure of all that, you should be able to install it. After installation, however, vmware wouldn't start. How I worked around this was to start it from console: sudo vmware and it gave me an error saying configuration hadn't been done, so I followed it's recommendation by doing vmware --configure (or something to that sort), configured it, and then was able to run it.

---

### Post by cris on 2007-04-15
I did as you said. There was left a file .vmware in my home folder. Though erased it , it still gives me the same error.

---

### Post by cris on 2007-04-16
I got it . After running gksudo nautilus , i did a search on / for vmware . There was a directory left in /etc , and after deleting it ,  the setup worked fine. Thanks for helping me

---

### Post by lotacus on 2007-04-18
no problem. :)

---

