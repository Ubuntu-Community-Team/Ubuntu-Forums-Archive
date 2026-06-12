---
title: "Beryl Install Issues"
date: 2007-01-14
forum: General Help
---

### Post by healthpellets on 2007-01-14
Howdy.

Been trying to get this new toy all up and running and have run into a bit of a snaaaaaaaaaag.  

I followed Lenart Hasen's guide ([http://lhansen.blogspot.com/search/label/Ubuntu]("http://lhansen.blogspot.com/search/label/Ubuntu"))
to the letter.  So I restart and get a big ugly blue screen indicating that something is not compatible with my graphics card (which is ATI) and it also said that "Extentions" was not a valid section (i believe), in reference to the following text which i inserted:  

Section "Extensions"
Option "Composite" "false"
EndSection

So if anyone else has had this problem, OR if you happen to know how to solve it for my next attempted install, I'd appreciate any help I could get.

Operating under 6.10

Thank you!!!

---

### Post by Waappu on 2007-01-14
Hi

It should be ```
"Extensions"
``` not ```
"Extentions"
``` Could that be your problem?

---

### Post by healthpellets on 2007-01-14
Thank you...that's the last time I do an attempt an install at 4am...HOWEVER...

I still have an issue.

I'm not getting the Beryl splash nor an icon in the system tray or anything.  How can I confirm that everything is actually installed and running correctly.

---

### Post by Waappu on 2007-01-14
Hi

Did you start beryl? press Alt+F2 and type beryl-manager. Tray icon and splash should come

---

### Post by Azakus on 2007-01-14
Uh, that should be
```
Option "Composite" "true"
```
If you don't want Composite enabled, then it should look like this:
```
#Option "Composite" "true"
```
"Composite" "false" will return an error because if you don't want composite on, don't put it in there.

---

