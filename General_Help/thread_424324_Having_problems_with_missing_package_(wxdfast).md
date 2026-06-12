---
title: "Having problems with missing package (wxdfast)"
date: 2007-04-26
forum: General Help
---

### Post by User321 on 2007-04-26
I am using Ubuntu 7.04. Up until the other day the upgrade module worked fine then all of a sudden it came back with an error message saying that the package WXDFAST needs to be re-installed. I have tried to have it installed many different methods but it will not take it.
Anyone know what is preventing this from re-installing? and how do I fix it? (without doing the whole complete System install which I DO NOT want to do!)

Thanks

---

### Post by User321 on 2007-04-27
I figured it out if you want the details here's what I did:

sudo apt-get remove wxdfast
sudo apt-get install wxdfast
then I updated all of the depositories

Walla! it is working fine now!   :smile:

---

