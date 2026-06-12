---
title: "dvd encryption"
date: 2005-05-16
forum: General Help
---

### Post by hoover93 on 2005-05-16
how can i setup ubuntu to play dvd movies?  i know there are encryption schemes on the dvd discs these days, but i can play the movies from windows.  i'm hoping ubuntu can be setup to play dvd movies as well.

thanks in advance.

---

### Post by bored2k on 2005-05-16
Ask and you shall receive.
[Q: How to install DVD playback capability](http://ubuntuguide.org/#dvdplayback)

---

### Post by blueplazma on 2005-05-16
You might need to install libdvdcss.  You can also check out the [Ubuntu Media HOWTO]("http://www.linuxforums.org/tutorials/1/tutorial-25783.html").  It's for Warty, but it should still work.

---

### Post by hoover93 on 2005-05-17
thanks bored2k.  now i can enjoy dvd movies.

for anyone else trying to duplicate this setup just follow the steps in the ubuntu guide in this order:

1. add extra repositories
2. install multimedia codecs
3. install dvd playback (libdvdcss2)
4. install a movie player (xine-ui)

---

