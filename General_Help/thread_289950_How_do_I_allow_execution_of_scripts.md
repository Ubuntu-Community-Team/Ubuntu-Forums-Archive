---
title: "How do I allow execution of scripts"
date: 2006-10-31
forum: General Help
---

### Post by jincast90 on 2006-10-31
How do I allow execution of scripts which are located at my /home/myname/bin folder? Lets say my file is called me, so I cd to the folder and say chmod 755 me. But I need bash to execute the script when typing me anywhere, instead of cd'ing to the directory and typing ./me all the time. I used to be able to do this but obviously lost the function when I formated and installed edgy.

---

### Post by aysiu on 2006-10-31
I usually plop executables in /usr/local/bin

---

### Post by jincast90 on 2006-10-31
> **aysiu said:**
> I usually plop executables in /usr/local/bin

Good for you. 8) (I'm not trying to be rude) But I need to know how to allow executables to be run from /home/myname/bin

---

### Post by PriceChild on 2006-10-31
You need to add it to your PATH... i've heard... never done it myself.

I'll do a quick search for you.

UPDATE - how's this? [http://ubuntuforums.org/showpost.php?p=1020745&postcount=2](http://ubuntuforums.org/showpost.php?p=1020745&postcount=2)

---

### Post by Iowan on 2006-10-31
[http://www.ubuntuforums.org/showthread.php?t=279154]("http://www.ubuntuforums.org/showthread.php?t=279154") Post #4.
Perhaps (I haven't checked) **/usr/local/bin** is already in the path - so it already works.

---

### Post by aysiu on 2006-10-31
> **jincast90 said:**
> Good for you. 8) (I'm not trying to be rude) But I need to know how to allow executables to be run from /home/myname/bin
[This thread](http://www.ubuntuforums.org/showthread.php?t=182167) might help you with that.

---

