---
title: "Firefox too many dictionaries"
date: 2013-06-01
forum: General Help
---

### Post by gabo.cr on 2013-06-01
Hi,

I fixed this problem once a few years ago, but I forgot how to do it and I can't find a solution anywhere.

I installed the Spanish spell checker dictionary on Firefox. But now I have Spanish for 22 countries and I have English for the US twice, Australia and South Africa. I only need two dictionaries.

How can I delete those extra dictionaries? 

I use Ubuntu in Spanish.

Thank you !

---

### Post by gabo.cr on 2013-06-01
Nevermind, I found the solution:

I closed Firefox and I did this in Terminal:

> cd /usr/lib/firefox/dictionaries

and then I removed all the dictionaries I don't need:

> sudo rm en_CA.aff en_GB.dic en_ZA.dic es_AR.dic es_CO.dic     etc...

Thank you !

---

