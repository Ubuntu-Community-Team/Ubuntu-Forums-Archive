---
title: "Hardy install"
date: 2008-04-24
forum: General Help
---

### Post by upthelum on 2008-04-24
Just downloaded and installed hardy in vmware but seems it's a text interface. I ran apt-get install xubuntu-desktop to get a gui but it didn't work. 

Can anyone tell me how to get the desktop installed?

---

### Post by upthelum on 2008-04-24
Also are there repos i need to add before an update?

---

### Post by upthelum on 2008-04-24
Anyone

---

### Post by twright on 2008-04-24
could you post the output of the command?

---

### Post by jshurst on 2008-04-24
When you say "it didn't work", what do you mean?  The package was not found, something failed with the installation, or that it did install but still no GUI?

You might need to enable the Universe repositories for some packages.  

Also, perhaps try this (found this online):
sudo aptitude install x-window-system-core xserver-xorg

Regards,

J

---

### Post by upthelum on 2008-04-24
I just read that the server version rc won't install a gui so have the desktop version coming down. I haven't tried any of these commands yet, will they install a desktop? If i know for sure i'll try but for now i'm gonna set up the desktop version.

---

### Post by twright on 2008-04-24
sudo apt-get install ubuntu-desktop will install the standard ubuntu desktop, sudo apt-get install xubuntu-desktop will install xubuntu :)

---

### Post by upthelum on 2008-04-24
> **twright said:**
> sudo apt-get install ubuntu-desktop will install the standard ubuntu desktop, sudo apt-get install xubuntu-desktop will install xubuntu :)

Yes i know i've used them many times but apparently the server installation won't allow a gui to be installed. I was trying to re-enforce this for definite so i don't waste time trying something that wont work.

---

