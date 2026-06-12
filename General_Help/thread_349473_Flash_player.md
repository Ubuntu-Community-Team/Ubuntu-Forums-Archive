---
title: "Flash player"
date: 2007-01-30
forum: General Help
---

### Post by kenmiles on 2007-01-30
I have been trying to install Macromedia Flash but at the I keep getting the following message "Automatic instalation failed due to network problems or upstream changes".
This happens if I try to instal from the command line or synaptic package manager.
Can anyone help me please.

Regards, Kenneth.

---

### Post by mikewhatever on 2007-01-30
Have you enabled extra repositories? [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by kenmiles on 2007-01-30
All are activated and server selected is for the uk.

---

### Post by david_2001 on 2007-01-30
What version of Ubuntu are you using and how are you installing Flash Player?  If the answers are 6.10 and the Ubuntu flashplugin-nonfree package then it may be because Adobe recently updated the version of Flash Player for Linux and you need to use the latest version of flashplugin-nonfree from the backports repository to install it.  The Edgy version of flashplugin-nonfree is 7.0.68~ubuntu3 but the backports version, which only appeared a couple of days ago, is 9.0.31~ubuntu1~edgy1.

The sources.list entry for the backports repository is (for the UK):> # Backports Repository
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe  multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


---

### Post by kenmiles on 2007-01-31
Thank you David, that fixed it.
Regards, Kenneth.

---

