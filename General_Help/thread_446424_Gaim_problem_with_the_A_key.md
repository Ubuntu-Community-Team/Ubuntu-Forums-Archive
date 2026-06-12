---
title: "Gaim problem with the A key"
date: 2007-05-16
forum: General Help
---

### Post by Kobra on 2007-05-16
This problem has arose very recently. Whenever I hit the A key while typing a message in Gaim, it has to be capitalized or else it brings up the "New Instant Message" screen.  It gets very annoying like this: "lAzy, At leAst, the beAst And the hArlot, etc..."

Please help, I have no idea what caused this.  I can type everything in perfect here as you can tell

---

### Post by strabes on 2007-05-16
Have you tried removing, purging, and reinstalling gaim? ```
sudo apt-get purge gaim && sudo apt-get install gaim
```

You could also try upgrading to [pidgin](http://www.pidgin.im/).

---

### Post by lorenco on 2007-05-17
Have you tried "A minor" :-({|=

(Sorry found this quite funny from a musical perspective ;) )

---

### Post by ebash on 2007-05-17
That same thing happened to me a long time ago and it was driving me nuts. Removing and reinstalling gaim didn't fixed it, neither compiling gaim from source or updating gaim from 1.5 to 2.0.

I find out that the key shortcuts are saved in one text file and that that file got some how a strange configuration. The trick is to edit that file and remove the faulty configuration line:

```
gedit ~/.gaim/accels
```

You will see that one of the lines will contain the accelerator "a", remove that line and restart gaim.

I hope that it works.

---

