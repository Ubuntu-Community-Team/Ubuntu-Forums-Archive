---
title: "Canon iP7250 printer time/ink wasting?"
date: 2015-04-11
forum: General Help
---

### Post by 2CV67 on 2015-04-11
I recently replaced my (dead print head) iP4300 printer by a new iP7250.
First I installed it in Windows 8, using the supplied CD & with USB connection only.
The driver is version 2.60.2.40 of 25/06/2013.
Then I installed it in Ubuntu 14.10 using the default CUPS+Gutenprint v5.2.10 driver.
Afterwards I also installed it in 14.10 using the Canon cnijfilter 3.9 drivers from the Michael Gruz ppa ([https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk)). That required installing "libtiff4" as I learned from this forum.

All these installations seem to work "out of the box" (except needing libtiff4) & that is a big improvement over my previous experience!
All seem to produce decent results, though I have not pushed very far yet.

But I am nearly always surprised by the time (& noise) the printer takes, before & after printing, doing what I suspect are head-cleaning cycles.

I started timing this, for the first print of each day.
I noted:
A - Time from switching printer on to getting steady white light.
B - Time from Print command to start of paper feed before printing.
C - Time from switching off to light off.

My results so far (which need confirming) are:
W8 Canon: A=18sec B=**147sec** C=5sec
14.10 CUPS/Guten: A=18sec B=**145sec** C=**59sec**
14.10 Canon/Gruz: A=18sec B=19sec C=**60sec**

For most of these times, the printer is whirring & clicking (& wasting ink??).

What sort of time intervals is anybody else seeing with this printer or with other recent Canon printers?

Thanks!

---

### Post by 2CV67 on 2015-04-12
I re-ran the Gruz test today, but did not get the same results:
A=17sec B=**150sec** C=59sec.

I am not alone:
[http://www.forums.usa.canon.com/t5/Personal-Printers/Canon-Pixma-IP7250-consistently-cleaning-itself/td-p/128017](http://www.forums.usa.canon.com/t5/Personal-Printers/Canon-Pixma-IP7250-consistently-cleaning-itself/td-p/128017)
[http://reviews.argos.co.uk/1493-en_gb/9127702/reviews.htm](http://reviews.argos.co.uk/1493-en_gb/9127702/reviews.htm)

---

