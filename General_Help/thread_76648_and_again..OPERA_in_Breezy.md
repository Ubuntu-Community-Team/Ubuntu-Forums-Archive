---
title: "and again..OPERA in Breezy"
date: 2005-10-15
forum: General Help
---

### Post by nicomazi on 2005-10-15
instalation went great...but:
                        > Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/opera/plugins/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins

does it means i can't have any plug-ins in opera?

thnx

---

### Post by Turambar on 2005-10-15
I had the exactly same problem. I also found a solution somewhere on this board. Anyway here's how to fix the problem:

Download Opera in tar.gz format from Opera's site.
Decompress the package.
Open the plugins-folder.
Copy all files beginning with operamotifwrapper to /usr/lib/opera/plugins

That should do the trick. After doing this at least flash worked properly.

---

### Post by hanzj on 2005-10-15
or install a file with the name "motifwrapper" from the repository.

---

### Post by Jonathan Drain on 2005-10-15
Turambar: I have the same problem as nicomazi, but your instructions don't work for me.

hanzj: I find nothing called "motifwrapper" or "operamotifwrapper" in Synaptic.

---

### Post by BIGtrouble77 on 2005-10-15
[QUOTE=Jonathan Drain]Turambar: I have the same problem as nicomazi, but your instructions don't work for me.

hanzj: I find nothing called "motifwrapper" or "operamotifwrapper" in Synaptic.[/QUOTE]
I installed 'motif-clients' which automatically installed 'libmotif3'.  It solved all of my opera errors.

---

### Post by Jonathan Drain on 2005-10-15
Ah, libmotif3 fixed it. Thanks!

---

### Post by nicomazi on 2005-10-15
[QUOTE=BIGtrouble77]I installed 'motif-clients' which automatically installed 'libmotif3'.  It solved all of my opera errors.[/QUOTE]

this worked....thank you

---

### Post by soro2005 on 2005-10-16
That other thread on this forum also suggested to install the Other/Static Deb package, instead of the one for Ubuntu Breezy, which I did (after having uninstalled the Ubuntu package), and that also solved the problem. :)

---

