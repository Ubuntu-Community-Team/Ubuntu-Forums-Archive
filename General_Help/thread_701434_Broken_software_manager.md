---
title: "Broken software manager?"
date: 2008-02-19
forum: General Help
---

### Post by Eisenwinter on 2008-02-19
Hi, I've had some experience on Ubuntu, 2 years ago, for 6 months.
After that, I moved back to Windows, and only came back to Ubuntu today, with a new computer, and an EMU 1212m sound card.

Ever since the installation a few hours ago, I've tried to get sound working, eventually I did, it's alright now, except it's high pitch shifted.

But that's not my main problem.

While trying to install ALSA utils, for the EMU sound driver, I recieved an error, saying that alsa utils has a dependency called ncurses.

I went and tried to download that dependency library, through apt-get.

It would not install, because of further dependency problems.

Ever since then, when I try to install or remove packages, it tells me to apt-get -f install, in order to fix dependency problems.

When I do that, it apparently tries to remove the ENTIRE OPERATING SYSTEM. :shock:

These are the last three sentences in the huge message I get in terminal, after apt-get -f install:

After unpacking 1413MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'

Now, in Synaptic also, it tells me the software manager is broken, and it is impossible to remove or add any packages, and I need to apt-get -f install to fix dependency problems.

I have the package-update orange colour icon on my top bar, when I hover over it, it says  "This usually means some packages have unmet dependencies".

Has anyone ever encountered this problem? and if so, how do I solve it?

I don't want to completely reinstall. :(

---

### Post by oldos2er on 2008-02-19
Go to System, Administration, Software Sources, and make sure all the boxes on the first page are checked.

---

