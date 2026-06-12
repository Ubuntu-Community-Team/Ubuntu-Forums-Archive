---
title: "How to Install a Printer on Kubuntu"
date: 2006-09-07
forum: General Help
---

### Post by RedMage on 2006-09-07
I have one quick question for the Ubuntu people:

Can you explain to me how to install a printer of ubuntu?

Thanks,

-RedMage

---

### Post by N6546R on 2006-09-07
If you don't have it already,

apt-get install gnome-cups-manager

Click on the Add Printer icon and follow the prompts, it's relatively painless.

Perry

---

### Post by jeremy on 2006-09-08
If you are using Kubuntu go to >System Settings >Printers >Add

---

### Post by N6546R on 2006-09-08
Even Kubuntu users should use gnome-cups-manager, as the KDE printer dialogs seem to be broken.

Perry

---

### Post by Najand on 2006-09-08
Just use the KDE Printing setting in the system settings. It works with all of 8 printers we have in the office and default printer drivers are more than gnome-cups.

---

### Post by Najand on 2006-09-08
> **N6546R said:**
> Even Kubuntu users should use gnome-cups-manager, as the KDE printer dialogs seem to be broken.

Perry

At least in my case it is not broken... However better to mention that I upgraded kubuntu from default ubuntu dapper and did not install it with KUBUNTU live CD.

---

### Post by MoebusNet on 2006-10-29
Please add this thread to the how-to thread.

Edgy-Eft Kubuntu clean install; I couldn't figure out how to install my printer until I read this. I installed gnome-cups-manager (I don't know if I really needed to) then K Menu > System Settings > Computer Administration > Printers. The menu selections took it from there. Thank you Forum contributors!

---

### Post by Poohbuntu on 2007-12-12
I realize this thread's been dormant for some while, but I was having trouble using a printer with my fresh install of Kubuntu Gutsy Gibbon, and I came across this thread in the process of looking for answers.  Per the above advice, I installed the Gnome print manager.  Upon trying to use it, however, it failed - and informed me that my CUPS server was unavailable.  

The solution from there was simple:  I went into the Synaptic Package Manager and searched for "cups."  When I saw something called cups server, I marked it for "reinstallation" and clicked the Apply button.  Voila!  I was able to then use the printer manager that comes with Kubuntu Gutsy to add my printer and print a test page.  All is good in Gutsy Land.

---

