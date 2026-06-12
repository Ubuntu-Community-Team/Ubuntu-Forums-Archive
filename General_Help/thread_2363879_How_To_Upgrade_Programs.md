---
title: "How To Upgrade Programs?"
date: 2017-06-15
forum: General Help
---

### Post by blackfish2 on 2017-06-15
How to upgrade programs?  For example, I like to use Geany for my HTML and text editor, but when the program is downloaded and installed, it does not have all the bells and whistles, like spell check.  This needs to be added later, but how to do it?  I am a Puppy Linux user, and it is incredibly easy to do with that distro with the package manager.  But with Ubuntu, I can't see how this is done.

---

### Post by mc4man on 2017-06-15
Best bet is to install synaptic (sudo apt-get install synaptic), then open & search geany. You'll find 30+ plugin packages, for instance - 
geany-plugin-spellcheck
Or in terminal to see names, 
```
apt-cache search geany-plugin
```
or names & status
```
apt-cache policy geany-plugin*
```

---

### Post by papibe on 2017-06-15
Hi blackfish2.

I believe you are looking at how to install geany plugins. I think you'll feel very at home if you install 'Synaptic Package Manager'.

After that, launch it and it would be easy install the plugins (search for geany-plugin).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by blackfish2 on 2017-06-17
Thanks to both of you!  It works great!

---

