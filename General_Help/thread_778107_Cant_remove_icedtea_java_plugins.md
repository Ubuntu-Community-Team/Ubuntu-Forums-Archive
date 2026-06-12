---
title: "Cant remove icedtea java plugins"
date: 2008-05-01
forum: General Help
---

### Post by webbie180 on 2008-05-01
Got this error, how to get around it?

E: icedtea-gcjwebplugin: files list file for package `mozilla-mplayer' is missing final newline

---

### Post by webbie180 on 2008-05-01
I'm trying to delete openjdk and icedtea so that I can use sun java.....pse help.  thanks.

---

### Post by csokesz on 2009-02-01
I had the same problem
icedtea plugin cames with cacao-oj6-plugin, so i have typed this:
sudo apt-get remove cacao-oj6-plugin
it worked for me

---

### Post by Jozza The Wick on 2009-05-02
> **csokesz said:**
> I had the same problem
icedtea plugin cames with cacao-oj6-plugin, so i have typed this:
sudo apt-get remove cacao-oj6-plugin
it worked for me

That worked for me too- I was having the same problem! Thanks so much! I had installed Icedtea, tried to switch to official Java, but only after I did this last command did it work - thanks!

---

