---
title: "Kpilot - Kontact"
date: 2007-01-25
forum: General Help
---

### Post by jeremy on 2007-01-25
I just upgraded to KDE 3.5.6, and, to my enormous joy, Kpilot successfully synced my T2 with Kontact Calendar for the first time since I started using edgy. This is a great improvement!

Avantgo is still not working however, can anyone help me there?

---

### Post by jeremy on 2007-01-29
After further investigation I have found that there is no longer the mal conduit available under 'Settings' -> 'Configure Kpilot...'

Does anyone else have/not have it?

---

### Post by jeremy on 2007-01-31
Doesn't anyone care?

---

### Post by zvandiver on 2007-02-02
Jeremy,
This doesn't answer your question, but I have a question for you.
Are you having any problems with duplicate calendar entries?  Every time I sync by Treo 700p, I am getting duplicate entries in KOrganizer.  Sometimes I get duplicates on my Treo and sometimes the Treo calendar entries are completely gone.  I have tried having the Treo override KOrganizer, and I have deleted the KOrganizer data file all to no avail.  Should I delete all of the KOrganizer config files?
Zane

---

### Post by jeremy on 2007-02-05
I haven't had this problem, all I can suggest is that you try to backup your calendar file, ~/.kde/share/apps/korganizer/std.ics , delete all cal entries on your palm, then try  renaming the config files.

Good luck.

---

### Post by huck416 on 2007-04-17
For Zvandiver: Check the conflicts resolution tab under "Calendar" in the "configure kontakt" dialog. If you have even one thing different between the desktop entry and the pda entry, it may be duplicating for that reason. 

For Jeremy: I've noticed the same thing: not Avantgo conduit with KDE 3.5.6 and haven't found the solution - still looking. Also don't know why I can't send Knotes to my pda but it will bring them in from the pda. Using a Palm Tungsten E OS 5.x. All else syncs fine.

---

### Post by jherrero on 2007-10-09
Hi,

I had the same problem here. I am using kpilot v3.5.6-0ubuntu6 and it looks like it lacks the /usr/share/services/mal-conduit.desktop file. I added it myself, based on the notepad-conduit.desktop file and I stored it in ~/.kde/share/services/. Here is the content of my file:

[Desktop Entry]
Encoding=UTF-8
Type=Service
Name=AvantGO
Comment=This the conduit for AvantGO.
Implemented=file
ServiceTypes=KPilotConduit
X-KDE-Library=conduit_mal

I hope this fixes your problem as well.

---

### Post by g_rus on 2008-07-12
Well, bust just creating that file mal-conduit.desktop at ~/.kde/share/services/ don't work, i get this messages "Error at download the conduit Avantgo. That means the conduit not was succesfully installed".

What i need to do?

---

