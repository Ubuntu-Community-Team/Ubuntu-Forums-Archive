---
title: "Removing OpenOffice.Org"
date: 2006-07-29
forum: General Help
---

### Post by ProjectGod on 2006-07-29
Hiya

is there a way to remove openoffice.org and all its components e.g. writer, calculator, base etc... without removing "ubuntu desktop"??? because when i try to remove this with synaptic i get a dialog box which displays that you're going to remove "ubuntu desktop" too!?

i really want to get rid of some of these sound video, graphic and office packages and select lighter, equivalents. 

****cheers

---

### Post by CameronCalver on 2006-07-29
have you considered installing ubuntu server instead of the default

---

### Post by ProjectGod on 2006-07-29
yes i tried that but it got stuffed... there were many broken dependencies and i had to use aptitude and the breezy cd to "repair" them... however after i installed the X win sys and rebooted... it got me to the shell... logged in and typed:

startx

it just halted before the log in screen. the cursor showed up and a greyish background appeared but didnt proced from there on. 

furthermore i tried to grab packages via the shell and the apt system kept "stalling" on me.

...anyway are you saying that i can't remove open office.org with the default desktop installation?

---

### Post by CameronCalver on 2006-07-29
no not at all im not sure why is would say it needs to uninstall the ubuntu desktop 
**[SIZE="3"]Come on ppl help him here it should not be a hard problem to fix[/SIZE]**

---

### Post by deanjm1963 on 2006-07-29
ubuntu-desktop is safe to remove, it doesn't remove anything. the ubuntu-desktop is a "collection of default applications", it's not a meta-package that if you remove one program it removes others. the same applies to kubuntu-desktop.

---

### Post by ProjectGod on 2006-07-29
thank you both of you! :D 
what better than to tweak a linux machine on a saturday afternoon eah? its good that the weather permits it (here in australia)

---

### Post by CameronCalver on 2006-07-29
Lol WOOT **[SIZE="4"]GO AUSSIE![/SIZE]**

---

### Post by yopnono on 2006-07-29
> **ProjectGod said:**
> thank you both of you! :D 
what better than to tweak a linux machine on a saturday afternoon eah? its good that the weather permits it (here in australia)

Don't worry about the desktop package, just remove the openoffice and then remove all files that are leftover in synaptic.

I have done this, because i installed the official openoffice 2.0.3 from [www.openoffice.org](www.openoffice.org) and everything work fine. 
Also the 2.0.3 have it's own update manager. (And it's still no 2.0.3 for dapper yet)

---

### Post by Beamerboy on 2006-07-29
> **ProjectGod said:**
> Hiya

is there a way to remove openoffice.org and all its components e.g. writer, calculator, base etc... without removing "ubuntu desktop"??? because when i try to remove this with synaptic i get a dialog box which displays that you're going to remove "ubuntu desktop" too!?

i really want to get rid of some of these sound video, graphic and office packages and select lighter, equivalents. 

****cheers

Just remove OOo (let it remove ubuntu desktop too) then simply reinstall ubuntu desktop (it is in synaptic)

---

