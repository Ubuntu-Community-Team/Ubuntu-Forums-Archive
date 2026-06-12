---
title: "Zope/Plone"
date: 2005-05-13
forum: General Help
---

### Post by elwis on 2005-05-13
*Ouch*
I've been playing with zope/Plone for the company intranet. I did the mistake to use apt-get for zope and plone. 
Both the zope and the plone developers told me not to, and they got right. Noticed that the debian/ubuntu ploneinstall only lasts until reboot?

Now, I 'll of course follow the plone developers advice and never ever go for any pre-packaged versions (the suse one in the office offers me other kind of troubles).

Just curious if anyone else have played with plone? And why on earth does it only live through one reboot? The files are nowhere to be found by zope, which means you have to apt-get it again and NOT perform a reboot.. then it will work? Seem .. stupid if you ask me?

---

### Post by elwis on 2005-05-14
Or it could be that one shouldn't play with Plone when too tired.

Found out that when I installed UBuntu's plone-packages, it also installed another Zope version. Which means.. /etc/init.d/ has two start scripts.. and I started the good old one.. which of course didn't have any plone-site in it's instance..

---

### Post by themoddingden on 2005-05-16
hi;
could you tell me what sources you had to add if any to get zope and plone???
I'm sure you also had to get the apache server fully running is there anything else special you have to do with the server once you get zope and plone???
Can we use the tar file at plone .org also or is that a bit messy???

---

