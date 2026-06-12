---
title: "Aaargh! I messed up synaptic!"
date: 2007-10-15
forum: General Help
---

### Post by ziofil on 2007-10-15
Hi everybody!
I have a big (but I hope I'm wrong) problem.

I had a corrupted package, that I couldn't uninstall via apt-get (libpt-1.10.10) so I tried a
```
find / | grep libpt
``` and removed all the files and directories that I thought was necessary to remove.
I did the same with ekiga.
Now I can use neither synaptics nor apt-get from shell!
It always wants libpt-1.10.10 to be reinstalled, but when I download the .deb file for libpt-1.10.10 and use ```
sudo dpkg -i libpt-1.10.10 etc...
``` (even with --force-all) it says (in italian, I'll translate) "dpkg: important notice: the list of the files for the package XXXX is missing, we assume that no files for this package are installed", and it says this for every package that is actually installed, and it finishes with : "dpkg: error processing libpt-1.10.10.....deb: impossible to create the list of the files for the package libpt-1.10.10 etc.." and it quits.
Synaptics crashes... and the updater says that an irrecoverable error occurred (the one above I suppose).

What can I do?? :confused:
Thank you in advance!

---

### Post by Pumalite on 2007-10-15
You might want to try:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by ziofil on 2007-10-15
nope... i get the same output (impossible to find the list of files for the package etc... for every package) as before...:(

---

### Post by Pumalite on 2007-10-15
What about:
sudo dpkg --configure -a
sudo apt-get -f install

---

### Post by ziofil on 2007-10-19
I tried what you suggested, sudo dpkg --configure -a gave no errors, which should be good, but then as I tried sudo apt-get -f install, I got the same damn error. :mad:
it seems to have lost the list of the files of *every* packet that I installed!
should I format and reinstall gutsy? :confused:
how much would i give to know what to do!

---

### Post by ziofil on 2007-10-19
this is another error that i get, maybe it could help!

dpkg: errore processando [name of package] (--remove):
 impossibile creare il file aggiornato con la lista dei file del pacchetto [package]: Nessun file o directory

that is in english
dpkg: error processing [any package] (--remove)
impossible to create the updated file with the list of files for the package [package]: no files or directories

so can't it even create the lists..?

---

