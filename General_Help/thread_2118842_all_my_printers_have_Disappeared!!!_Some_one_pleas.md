---
title: "all my printers have Disappeared!!! Some one please HELP!!"
date: 2013-02-22
forum: General Help
---

### Post by badman35 on 2013-02-22
I have three printers that were installed a HP1200, HP4P and a brother MFC-295cn all worked and I could print with all of them they are connected to my home lan. So this morning Feb 22, 2013 I went to my ubuntu 12.04 desktop and tryed to print out some bills that I have to pay and poof no printers at all. Could someone here give me a hand with this. This happen twice before and I had to do a reinstall but that is not an option for me now I.

---

### Post by kurt18947 on 2013-02-22
I've not had the 'pleasure' of something like that happening. Here is what I would do.

I have a retro printer app installed.  It's in the repositories and restores printer management to like it was in gnome2 before the printer management app in gnome3/Unity dumbed it down.

```
system-config-printer
```It can be installed from the software center, Synaptic, or via apt-get install.  You may have to do this from the SUDO/administrator account.  Then <alt>f2 and type "system-config-printer".  A window will open.  Is there anything shown?

You have 2 H-P printers.  Do you have HPLIP and HPLIP-gui installed?  I've had printers paused or disabled for no apparent reason but they were still shown as installed.  If this is what happened to you, it's an easy fix.

---

### Post by badman35 on 2013-02-22
> **kurt18947 said:**
> I've not had the 'pleasure' of something like that happening. Here is what I would do.

I have a retro printer app installed.  It's in the repositories and restores printer management to like it was in gnome2 before the printer management app in gnome3/Unity dumbed it down.

```
system-config-printer
```It can be installed from the software center, Synaptic, or via apt-get install.  You may have to do this from the SUDO/administrator account.  Then <alt>f2 and type "system-config-printer".  A window will open.  Is there anything shown?

You have 2 H-P printers.  Do you have HPLIP and HPLIP-gui installed?  I've had printers paused or disabled for no apparent reason but they were still shown as installed.  If this is what happened to you, it's an easy fix.

Could you tell me the name of the program to install?? I looked for retro and it pulled up a bunch and I need to know which one to use.. Oh  thanks for any and all help..

---

### Post by kurt18947 on 2013-02-22
> **badman35 said:**
> Could you tell me the name of the program to install?? I looked for retro and it pulled up a bunch and I need to know which one to use.. Oh  thanks for any and all help..

I don't have Ubuntu installed so I don't have software center, I'm using Synaptic instead but either one should work.  The name of the 'program' is "system-config-printer-gnome".  The same name is used to launch it from a 'run' box, though I just use  <alt>f2 then "system-config-printer".

---

### Post by badman35 on 2013-02-22
> **kurt18947 said:**
> I don't have Ubuntu installed so I don't have software center, I'm using Synaptic instead but either one should work.  The name of the 'program' is "system-config-printer-gnome".  The same name is used to launch it from a 'run' box, though I just use  <alt>f2 then "system-config-printer".

It does not show anything.. what to do now?????

---

### Post by kurt18947 on 2013-02-22
> **badman35 said:**
> It does not show anything.. what to do now?????

Any luck with HPLIP or HPLIP-gui?  Worst case, I guess reinstall.  I'm not really sure how to procede with HP printers.  Usually they're 'just there'.  I'd probably open the printer app again then click Server ->  new -> printer -> select device -> network  and see if anything shows up there.  I have 3 networked printers and they all show up.

---

### Post by gifford on 2013-02-22
Is it possible that the ip address of the printers on your lan changed?

---

### Post by kurt18947 on 2013-02-23
> **gifford said:**
> Is it possible that the ip address of the printers on your lan changed?

Something along those lines is entirely possible.  I'd had problems with networked printers disappearing in the past.  I finally assigned a static I.P. address to each machine then used this for a device URI:

```
socket://xxx.xxx.xxx.xxx:9100

```

where x=I.P. address.    That has been quite reliable for me.  Do be aware of duplicates;  Just as more than one house cannot have the  same postal address,  more than one machine cannot have the same I.P.  address.   I'd imagine that the procedure to assign a static  I.P. varies by machine, documentation should address it.  In Brother's case, they have a separate publication that addresses network installation and configuration on their web site.

---

