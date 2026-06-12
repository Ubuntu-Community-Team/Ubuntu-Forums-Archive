---
title: "A bit of help installing Deer Park anyone?"
date: 2005-07-13
forum: General Help
---

### Post by spaceballl on 2005-07-13
Hi there,

I'm new to linux but hoping to learn quickly. I want to have the newest version of Deer Park. I downloaded the *.tar.gz file and extracted it. I ran the installer and everything went fine. However, how do I run Deer Park once I install it? I've tried using two directories. After the installer completes, it opens up a Deer Park window. But once i close it, i have no idea how to re-open it. I try by just going into the directory and typing "firefox" but that opens the old version. Any help? Thanks ahead of time.

-Kevin

---

### Post by bgstratt on 2005-07-13
if you make a new icon have it go to /usr/local/firefox/firefox  or just type in terminal /usr/local/firefox/firefox, alternatively change to the /usr/local/firefox directory and then type firefox.

<<edit>> It installs to the /usr/local directory be default instead of the /usr/lib directory.

---

### Post by bgstratt on 2005-07-13
Before I forget, you will probably want to sudo cp /usr/lib/mozilla-firefox/plugins/* /usr/local/firefox/plugins/  that way you have all your plugins working already.  if you installed java from the backports you may have to reinstall from the java website if you need the latest java.

---

