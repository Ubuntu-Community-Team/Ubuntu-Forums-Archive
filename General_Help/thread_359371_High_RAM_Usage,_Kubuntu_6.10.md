---
title: "High RAM Usage, Kubuntu 6.10"
date: 2007-02-11
forum: General Help
---

### Post by romUdog on 2007-02-11
Hey Fellow Linux Techies and Enthusiasts,

       I have a problem regarding my RAM I have 2gb of RAM and its saying i only have 129MB Free, I am only running one or two apps....Any idea how i can lower the usage? I am open to any suggestions.

---

### Post by esaym on 2007-02-11
The linux kernel caches all data that goes through the i/o.  Meaning everything that is read off of the hard drive is stored in the memory UNTIL an application needs the memory space.  Then it chunks the data and gives the space to the app.  Type "top" into your console terminal and look for how much "buffer" is using. That is how much ram the apps are actually using.  It will probably be something ridiculously low like 80mb or something.....:biggrin: :biggrin:

---

### Post by romUdog on 2007-02-13
Thanks man, I just noticed that when i need an app it always stays the same in use...lol Thanks!

---

### Post by aysiu on 2007-02-13
Read more here:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

