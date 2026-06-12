---
title: "super newb question"
date: 2007-11-18
forum: General Help
---

### Post by blacklung on 2007-11-18
hi, i recently migrated from windows vista and havent had too many troubles thus far.  my major problem is that i cant get the ./ command to work in the terminal for the life of me.  im running 7.10, and all i want to do is compile and play glest... any help is appreciated.

---

### Post by HermanAB on 2007-11-18
Here is some general help: [http://www.aeronetworks.ca/compile-howto.html](http://www.aeronetworks.ca/compile-howto.html)

However, if you wish to play games, then you need a dual boot system with WinXP.

Cheers,

Herman

---

### Post by tronica on 2007-11-18
glest is a linux game, and you need to make it executable by doing the following

```
sudo chmod a + x glest_2.0.1
``` 

change the _2.0.1 to match yours

and then run it

```
sudo ./glest_2.0.1-multilanguage.run 
```

again change the _xxx.run to match yours

with that game you may also need libopenal0a 

```
sudo apt-get install libopenal0a 
```

---

### Post by blacklung on 2007-11-19
well, i tried the chmod and all that, but still nothing, i got an error


   chmod: invalid mode: `a'
   Try `chmod --help' for more information.

the worst part of all this is, i have no choice but to learn the ins and outs of linux if i plan to pass my computer science classes i have coming up...

---

### Post by bungnati on 2007-11-19
Did you ./configure and get an error. If so you may need to install some libs

---

### Post by tronica on 2007-11-19
try 

sudo chmod +x glestxxx.run

replacing the xxx with what you have

---

