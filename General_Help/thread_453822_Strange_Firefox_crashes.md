---
title: "Strange Firefox crashes"
date: 2007-05-24
forum: General Help
---

### Post by fragos on 2007-05-24
Since the recent Ubuntu 7.04 of nvidia-glx and related pieces update firefox has been crashing.  I tried starting it with a terminal to see if there were any additional hints and got the following.

fragos@Geo:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Gecko: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
fragos@Geo:~$ 

Am I alone on this or have others seen it?

---

### Post by fragos on 2007-05-25
Looker but no takers.  Perhaps I have a one of situation.  Another symtom to add though.  Occasionaly my Wacom pad goes dead for no reason.  As a mtter of note, it's parameters are set by xorg.conf which may help uncover the the error.  I forgot to say that when Firefox crashes it just disapears from the screen as if I'd closed it.  There are no display artifacts left behind.

---

### Post by gregmark on 2007-05-30
I have also been experiencing multiple crashses of my Firefox sessions.  I have 5-8 tabs open, with two dynamic pages in gmail and NetVibes.  The crashes are sudden and end in nothing but a "Segmentation Fault" error.

Any ideas on further debugging techniques?

---

### Post by fragos on 2007-05-30
My problem hasn't occured in a while perhaps thanks to an update.  Extensions are a potential cause of crashes.  Some don't work all that well and some users have dozens of extensions which may even interact with each other to cause crashes.  I've become more selective in my choice of extensions and if I rarely use one I've installed, I remove it.  If you have frequent or predictable crashes, I'd try running without extensions to see if the problem goes away.  If it does, add them back one at a time until the culprit reveals itself.

---

