---
title: "Apt-get/Firefox problems:"
date: 2005-10-06
forum: General Help
---

### Post by bogoliubov on 2005-10-06
Yesterday I did "apt-get upgrade", which I hadn't done before. Everything worked out OK, except for packages for firefox. The packages were:

mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
moxilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb

At the same time it complained about trying to substitute 
/var/lib/mozilla-firefox/extensions.d/00classic
/usr/lib/mozilla-firefox/components/libmozgnome.so

I can't give you the exact output, since my webbrowser doesn't work on the ubuntu machine...

Is there anyone out there who knows how to solve this? I'm rather addicted to the webbrowser and my pc with Ubuntu...

---

### Post by KingBahamut on 2005-10-06
This I believe is caused by a naming scheme issue. Youll need to clear out your apt cache 

apt-get autoclean
apt-get clean 

apt-get remove mozilla-firefox 
apt-get install mozilla-firefox 

what happens then?

---

### Post by Zelut on 2005-10-06
I've had the same problem (probably).  What I did was apt-get remove firefox and then install it again.  That fixed it for me... give it a try.

---

### Post by bogoliubov on 2005-10-06
[QUOTE=kuyaedz]I've had the same problem (probably).  What I did was apt-get remove firefox and then install it again.  That fixed it for me... give it a try.[/QUOTE]

Ok, I'll give the first one a try.
I almost removed it, but synaptic said that it also wanted to remove "ubuntu-desktop" or something like that. That sounded like a big package, so I hesitated.

kuyaedz: did you have any troubles removing/reinstalling firefox or did it go smoothly?

---

### Post by Zelut on 2005-10-06
ubuntu-desktop is fine to remove.  I had the same scare when I wanted to remove evolution.  don't worry about removing it, its fine.

It went pretty smoothly for me.  I just did the apt-get remove mozilla-firefox and then installed the same package.

---

### Post by bogoliubov on 2005-10-06
It worked! Thanks alot!

---

### Post by KingBahamut on 2005-10-06
No problem....thats what we are here for.

---

