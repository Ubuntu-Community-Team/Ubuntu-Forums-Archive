---
title: "Serious problems with Edgy"
date: 2006-11-03
forum: General Help
---

### Post by jimbob on 2006-11-03
I have (2) serious problems with the Edgy distro as installed new from the .iso file:  

1)  When I select the restart button from the Quit panel, Edgy causes my BIOS to reset itself to the default values destroying my custom settings.  If I don't happen to notice it this causes the system to fail on the next boot.  If I select shutdown everything stays set as I want it.

2)  Edgy will not install at all on my Toshiba laptop.  The CDROM thrashes almost forever in order to even present the desktop display giving me the choice of running live or installing.  When I select install the thrashing resumes for at least a half-hour finally terminating in either a completely black screen or presenting an empty desktop with no mouse or keyboard control whatsoever necessitating dropping the battery out to get the laptop back. (Yes, the checksums are all valid and this same CD installed fine on my desktop PC).

Do either or both of these warrant a bug report?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by roderikk on 2006-11-03
Hi!
I have no idea about your first problem. I don't believe edgy should cause any changes in your BIOS.
Your second problem sounds quite familiar with me. I don't know the system specs of your laptop but they are usually lower than those of a desktop pc so the live cd might not be a really good choice for that. What I usually do is use the alternate cd for installation (actualy I take it one step further by only doing a server install and only later from the command prompt install gdm and ubuntu-desktop because I have found that sometimes the installer crashes during the installation/configuring of x).

Hope this helps.

---

### Post by jimbob on 2006-11-04
Roderikk:  Thanks for the tip.  I downloaded and burned the alternate CD iso and was able to do a text mode install on my laptop with out any problems.  The only thing extra that I had to do was install the linux restricted modules in order to get my Atheros drivers installed.

  Now if I could only figure out what is clobbering my bios on an Edgy restart.  Must be something strange my motherboard doesn't like.

---

