---
title: "Trouble installing Firefox beta 3 on Gutsy"
date: 2007-12-09
forum: General Help
---

### Post by TGDuff on 2007-12-09
I am running Gutsy on an Eee PC and I would like to install the beta version of Firefox 3.  I just cannot get it to work (at least not as root).  I first tried overwriting my default Firefox files ( /usr/lib/firefox/ ) with the beta files.  After chmod-ing I couldn't get Firefox to run without sudo; I get a "Cannot find mozilla runtime directory" error.  I even tried deleting my profile settings in ~/.mozilla.  I then loaded up Synaptic in order to reinstall Firefox 2.  I then noticed there was a Firefox 3.0 in the repositories.  So I downloaded that but it turns out it is an alpha version.  I then attempted to overwrite those alpha files with the beta files.  Unfortunately I still did not have any success.  I set all the files in the firefox-3.0 folder to go+rx and now I get no feedback when I run ./firefox in the terminal; I am immediately returned to the command line prompt.  

Any ideas on what I am doing wrong and how I can get Firefox 3 to run properly?

---

### Post by dpar on 2007-12-09
Did you try following the instructions at Mozilla?

[http://kb.mozillazine.org/Installing_Firefox#Linux](http://kb.mozillazine.org/Installing_Firefox#Linux)

---

