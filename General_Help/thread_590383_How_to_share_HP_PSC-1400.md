---
title: "How to share HP PSC-1400?"
date: 2007-10-24
forum: General Help
---

### Post by Pappasan on 2007-10-24
I have a HP PSC 1400 series all-in-one.  If I install it in Windows, I can share the printer just fine to other Windows machines but not to my Mac or Ubuntu box.  I called HP and they told me that it can't be done.  This base model print/scan/copiers don't have network capabilities, even though Windows can share the printer.  I can't get it to share on my Mac and now my kids want to print off of their Ubuntu box (They don't touch my other machines ;-) ).
I can print from Gimp when the printer is attached via USB on my desktop.
I have checked the box for "Share Printers" in the "Global Settings" menu.  
Does this set up IPP or LDP printing?  How can I find it on the network?
Where do I go from here?

_______________________________________________________________________
HP Vectra VL420 [P4 1.7/768mg/80gb/GeForce2 mx 400] Fiesty
Mac Mini [G4 1.42/1gb/80gb] OSX 10.4
iBook [G3 500/384mb/10gb] xunutu Fiesty

---

### Post by linuxwizard on 2007-10-24
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by gpalmercableone on 2007-11-12
Are you sharing it using Samba? I was able to share this model printer attached to an xp box. Use the 

links provided earlier to set up in Samba, Then SMB://<host computer>:631/printers/<printer name>. My

 problems start when running this printer on an Ubuntu server and try to share it to a Winxp client. I am

 finding that very difficult to get done, HP support no help, they use a screwy driver setup that prevents 

installing this as a network printer unless its shared by another windows machine.

---

