---
title: "Apt/Synaptic installation history..."
date: 2005-05-24
forum: General Help
---

### Post by davide_bruzzone on 2005-05-24
Greetings all...

Does anybody know of a tool (or a tool's feature) that would allow me to determine which packages (including dependencies) were installed on a machine after the base distribution was installed? Can either apt or Synaptic (or dpkg, etc.) do this?

Cheers...

Dave

---

### Post by shakin on 2005-05-24
In Synaptic, click File -> History

You can go through the history day by day.

---

### Post by davide_bruzzone on 2005-05-25
[QUOTE=shakin]In Synaptic, click File -> History

You can go through the history day by day.[/QUOTE]

Doh!...

...I didn't have my laptop in front of me when I asked. Regardless, I wasn't aware of the option and didn't find it in any of the online Synaptic documentation.

Cheers...

Dave

---

### Post by dustigroove on 2007-11-06
Any way to generate this from the command line? It's a bit cumbersome through the option in Synaptic.

---

### Post by cyran on 2008-04-06
> **dustigroove said:**
> Any way to generate this from the command line? It's a bit cumbersome through the option in Synaptic.
I was thinking the same thing. It's probably in a text file somewhere-- Where does Synaptic store its data? *Edit: Never mind, I checked and found it.*

Synaptic stores its installation history in separate files inside /root/.synaptic/log . By default, the .synaptic and log directories are both unreadable except by root; you have to do 

sudo chmod +rx /root/.synaptic/log

just to make it easier to see what file you want to look at.

---

