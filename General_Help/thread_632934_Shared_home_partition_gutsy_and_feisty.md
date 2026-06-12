---
title: "Shared home partition: gutsy and feisty"
date: 2007-12-06
forum: General Help
---

### Post by Irihapeti on 2007-12-06
I've just installed Gutsy on a separate partition, updated Grub and all that, and so far it seems to be working ok.

I'm thinking about sharing the /home partition between the two versions. I see no problem with documents, music etc etc, but what about program config and history files? Will this work, or will they get messed up because each OS runs different versions of the same programs?

Has anyone else tried this?

---

### Post by daviddehoog on 2007-12-06
Hi Iihapeti

It's certainly possible, but I think the two could be quite confused by the different configuration files. Some files will need to contain different information to control Gutsy and Feisty. I'd be very reluctant to try it without a comprehensive backup of the /home partition and a spare rescue CD !

Cheers
David

---

### Post by pebo on 2007-12-06
I tried this using ubuntu & arch. The only problem I had was the shared ~/.xinitrc file - I was using gnome and kde in ubuntu and xfce in arch, so when logging in I had to explicitly choose the right wm.
HTH

---

