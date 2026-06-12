---
title: "Tk Installation issues"
date: 2008-03-26
forum: General Help
---

### Post by Klonoa on 2008-03-26
Ok here is my problem, I am installing Tcl and Tk, and I wanted the latest version. When i installed Tcl, it went smoothly, but when I get to Tk... I get stuff like this for example...

/home/kaze/Desktop/tk8.5.1/unix/../generic/tkInt.h:1184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/kaze/Desktop/tk8.5.1/unix/../generic/tkInt.h:1203: error: expected ‘)’ before ‘*’ token
/home/kaze/Desktop/tk8.5.1/unix/../generic/tkInt.h:1211: error: expected ‘)’ before ‘*’ token

and

/home/kaze/Desktop/tk8.5.1/unix/../generic/tk3d.c:983: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/kaze/Desktop/tk8.5.1/unix/../generic/tk3d.c:983: error: ‘drawable’ undeclared (first use in this function)
/home/kaze/Desktop/tk8.5.1/unix/../generic/tk3d.c:983: error: ‘TkBorder’ has no member named ‘bgGC’

this is a brand new fresh install, am I missing some dependencies or something?

---

### Post by Claus7 on 2008-06-03
Hello,

I have no idea why you get that.
Try my script and you will have both amsn and the libraries you need installed! Of course you can install only the libraries you need.
[http://ubuntuforums.org/showthread.php?t=712425](http://ubuntuforums.org/showthread.php?t=712425)

Regards!

---

