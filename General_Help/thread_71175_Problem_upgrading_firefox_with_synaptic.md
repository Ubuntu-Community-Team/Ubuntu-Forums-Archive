---
title: "Problem upgrading firefox with synaptic"
date: 2005-10-02
forum: General Help
---

### Post by isTHEr3mOr3 on 2005-10-02
This is the error message I get after install updates:
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
Any idea what the problem could be?

---

### Post by transactionlogfiller on 2005-10-02
Not sure if this is the right thing to do, but

dpkg -i --force-all /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb 

that should overwrite it.

---

### Post by isTHEr3mOr3 on 2005-10-02
Yep, works. 
Thanks.

---

### Post by crowndip on 2005-10-02
Don't do this ... you will have problems with broken packages in futur.

instead do:
sudo telinit 1        'to go to one user mode
sudo apt-get remove mozilla-firefox
sudo apt-get remove mozilla-firefox-gnome-support
sudo apt-get install mozilla-firefox
sudo apt-get install mozilla-firefox-gnome-support

this worked for me

---

