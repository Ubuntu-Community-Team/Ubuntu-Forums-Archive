---
title: "XMMS Looks Awful!"
date: 2006-07-06
forum: General Help
---

### Post by toddedw on 2006-07-06
I've tried uninstalling xmms and reinstalling it, but no matter what I do it looks fuzzy and just plain weird...

Screenshot: [http://toddedwards.us/img/xmms.jpg](http://toddedwards.us/img/xmms.jpg)

I would appreciate any input.

---

### Post by Randomskk on 2006-07-06
Weird problem, but you may want to try completely removing it + config files:
sudo apt-get remove xmms
sudo dpkg --purge xmms
sudo apt-get install xmms

---

### Post by K.Mandla on 2006-07-06
Did you try a different skin? Maybe that one is corrupted somehow.

---

### Post by toddedw on 2006-07-06
Same problem... Do you think it could be related to my video drivers? I had a lot of issues with them when installing ubuntu (ati radeon xpress 200).

I used to following to fix:
apt-get isntall xorg-driver-fglrx
fglrxconfig
startx

Everything seems to work fine (including enemy territory) so maybe I'm just pulling straws here. *shrug*

---

### Post by K.Mandla on 2006-07-06
Hmm. Seems to me if the problem happens no matter what skin you use, then the first step would be trying to clean-install xmms.

I'm no expert, but it seems like a driver issue would have more far-reaching and significant side effects than just the buttons in xmms. Any other programs acting funny?

---

### Post by toddedw on 2006-07-06
Weird... It was the skin. The only reason I hadn't tried another one is because I didn't have any. I downloaded one and extracted it to /home/todd/.xmms/Skins and it looks great now. Sorry for the silly post. :???:

Thanks for the help!

---

