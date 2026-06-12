---
title: "gutsy--how do I change default init?"
date: 2007-11-26
forum: General Help
---

### Post by djjosephk on 2007-11-26
not really sure why Ubuntu decided to reinvent the  'effing wheel on this one but for some god forsaken reason there is no such thing as /etc/inittab any more. To top it all off I can't seem to find any documentation on the frigging subject so I'm having to resort to posting the question (it would normally take me 2 sec to do this on every other form of Unix/Linux I deal with but now it's turned in into a multi day google fest just to flip a &^%$ light switch). 

How do I set the default init level with out an ugly startup script, seriously hacking the /etc/rcX scripts or passing the argument to the kernel on boot?  I can change the init level while I'm running so I know it can be done.....

is there anyway to get rid of this upstart crap and go back?


sorry for the rant....

---

### Post by bingoUV on 2007-11-26
I agree with the apparent lack of documentation (searched about 4-5 months ago). But there is a README file in /etc/rc directory, which is more useful than any google search.

---

