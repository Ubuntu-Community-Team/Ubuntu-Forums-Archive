---
title: "Synapse/zeitgeist not locating certain directories"
date: 2015-06-07
forum: General Help
---

### Post by Matt M on 2015-06-07
When I type certain directory names into Synapse, no results are shown. For example, the contents of my home directory are as follows: bin, Documents, Learning_Thai, Music, Public, code, Downloads, ovpn-client, Templates, Desktop, ESL, mnt, Pictures, Videos. Typing "Documents", "Learning_Thai", "Music", "Public", "Downloads", "Templates", "Desktop", "Pictures", or "Videos" into Synapse locates these directories immediately, but if I type "bin", "code", "ovpn-client", "ESL", or "mnt", no directory is found.


I have tried updatedb and the following sequence:


zeitgeist-daemon --quit
rm -rvf ~/.local/share/zeitgeist/fts.index/
zeitgeist-daemon --replace


(note that the last command yields the error: "** (zeitgeist-datahub:2400): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!)" -- I don't know if that is relevant)


I have also tried purging and reinstalling zeitgeist. 


None of these had any effect. Before I updated to my current OS (Xubuntu 15.04), I had the same problem with Synapse, but strangely it was a different subset of directories that Synapse was ignoring.

---

### Post by Matt M on 2015-06-11
I've found that answer: I have to go inside the folder and open any file using a GUI app. The folder is then recognised by Synapse.

---

