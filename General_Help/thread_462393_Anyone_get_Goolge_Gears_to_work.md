---
title: "Anyone get Goolge Gears to work?"
date: 2007-06-02
forum: General Help
---

### Post by jrjazzman on 2007-06-02
I wanted to try the new offline feature Google Reader has.  It prompts you to install the Google Gears Firefox plugin, which I did.  My next 2 attempts at restarting Firefox were duds (just ended up not opening).  3rd time Firefox opened, so I went to Reader, clicked the offline link, and it wanted me to install Gears again.  So, it doesn't seem to think I have Gears installed.  Anyone else have a similar experience?

Jeremy

---

### Post by cookies on 2007-06-02
Yep, but this is on Fedora Core, not Ubuntu.

---

### Post by djgrant on 2007-06-09
> **jrjazzman said:**
> I wanted to try the new offline feature Google Reader has.  It prompts you to install the Google Gears Firefox plugin, which I did.  My next 2 attempts at restarting Firefox were duds (just ended up not opening).  3rd time Firefox opened, so I went to Reader, clicked the offline link, and it wanted me to install Gears again.  So, it doesn't seem to think I have Gears installed.  Anyone else have a similar experience?

Jeremy

I'm having the same problem.

---

### Post by firefeather on 2007-11-15
Are you both using 64-bit? It doesn't work directly on 64-bit.

---

### Post by swheatley on 2007-12-17
I'm having a similar issue on a fresh install of 32-bit Gutsy. I go to Google Reader in Firefox, click on "Offline", install Google Gears, it asks to (and I let it) restart Firefox, and when I get back into Firefox, the offline option is still not there. Google Gears appears to be installed, as I have a Gears option in my Tools menu. Any thoughts? This is my only show-stopper with Gutsy right now (I previously had Feisty installed on the same laptop with no Gears issues, but had some other issues and went back to Windows for the last few months.)

---

### Post by swheatley on 2007-12-18
Just figured out my problem and I'm posting it here in case anyone else has the same problem. On the Details page for the linux requirements:

[http://code.google.com/support/bin/answer.py?answer=71866&topic=11630](http://code.google.com/support/bin/answer.py?answer=71866&topic=11630)

It mentions that you need libstdc++5. My fresh copy of Ubuntu Gutsy 7.10 had libstdc++6 installed. I installed libstdc++5 and everything is working fine now. It would be nice if somehow the extension would tell me what it was looking for rather than failing silently, but at least I have my offline Google Reader again!

Shawn

---

### Post by objem on 2008-04-06
On my 64 bit system, google gears wont install on firefox 64 bit or firefox 3 BETA 3, but will install on firefox 32 bit.

---

