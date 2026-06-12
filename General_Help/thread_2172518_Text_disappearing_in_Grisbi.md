---
title: "Text disappearing in Grisbi"
date: 2013-09-05
forum: General Help
---

### Post by ron-d-ross on 2013-09-05
Hi,

I'm running Grisbi  0.8.9 on Ubuntu 13.04 -- it's actually Kubuntu (after installing the Kubuntu desktop) but after complications related to upgrading to a  backported recent edition, I've come back to using Unity...)

All was fine (I've been using Grisbi for finances for years) until accidentally moving the divider between the transaction window and the accounts window all the way to the right, so that the transaction window disappeared, then moving it back. There was a couple seconds greying out (or "orangeing out") of the window, as happens on Ubuntu when an application hangs, but then it cleared. But when it did, and I had restored the Transactions window, none of the transactions were visible, the text has simply disappeared, or the font has become invisible. I've uploaded a screenshot to show what I mean. In the large transactions window occupying most of the screen up to the right hand side, there should be lines of transactions, but nothing appears, no matter which account I select (in the window on the left). The transactions and the information are there, as the image shows, because if I select an apparently empty line (the one in orange), the transaction details appear in the section below.
I've tried manipulating every display setting possible, I even completely uninstalled grisbi and deleted config files and reinstalled, but the problem remains.
Does anyone have a clue ? 

[ATTACH=CONFIG]246028[/ATTACH]

---

### Post by davetv on 2013-09-05
Maybe you missed a config file. In a terminal try 

sudo apt-get remove grisbi
sudo apt-get purge grisbi

and then re-install

---

### Post by ron-d-ross on 2013-09-06
> **davetv said:**
> Maybe you missed a config file. In a terminal try 

sudo apt-get remove grisbi
sudo apt-get purge grisbi

and then re-install

Thanks for this procedure (and sorry for the late reply - I'm travelling at the moment)
however, after proceeding as above, and also doing an "autoremove" and then 
searching and finding and deleting yet more config files (in ~/.config/grisbi) that still hadn't gone,
the problem remains, exactly the same

I'm wondering if an upgrade of system components caused the problem ... I hadn't done my bookkeeping
 in a while and the interim I had run the system update a couple of times

I've started getting a handle on Gnucash, just in case, but I'd like to get Grisbi working again... but it'll have to be soon ;-(
Any other ideas? The grisbi website has been down for maintenance for a while, so maybe the project is stalling...

---

