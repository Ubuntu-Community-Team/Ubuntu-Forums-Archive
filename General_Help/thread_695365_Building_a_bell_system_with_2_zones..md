---
title: "Building a bell system with 2 zones."
date: 2008-02-13
forum: General Help
---

### Post by itzpapalotl on 2008-02-13
Hello again all.
I work at a school, which is actually two schools, an elementary and middle school, and a high school. Our bell system, the current one is an elaborate contraption made of relays, tone generators, and that sort of thing. It doesn't work, can't be made to work, and is generally hated by all anyway for it's "swan being strangled" aesthetic. It has been disabled for a month.

I have built a bell system for the high school using ubuntu, 7.10 server,  mpg321 and crontab, and an mp3 of a school bell (or on occasion a song). It all pipes in to the intercom, and it all works just fine. In fact it works so well that I have been asked to do the same thing for the middle school. Only, I don't have another box to use.

I DO have another sound card or I can get one.

Here's what I need to know:
right now it works like this:
I have a script called ringbell in /usr/bin
which is essentialy:

mpg321 /var/bells/schoolbell1.mp3

I have a crontab that does a bunch of this:

12 14 * * 3 /usr/bin/ringbell #fourth period end
12 19 * * 3 /usr/bin/ringbell #fifth period start

What I THINK I need is two separate ringbell scripts. Two users each logged in with crontab running. and two sound cards connected to the two zones.

How do I tell the computer which sound card to use? Or more realistically where is there is good newbie guide to device redirection?
is it as simple as 
mpg321 /var/bells/schoolbell1.mp3 | dev(whatever) 
that didn't seem to work...

---

### Post by tgalati4 on 2008-02-13
man mpg321

mpg321 -a /dev/dsp1 /var/bells/schoolbell1.mp3
mpg321 -a /dev/dsp2 /var/bells/schoolbell2.mp3

You will have search the forums for getting multiple sound cards to work.  They will have different /dev names depending on the card and module loaded.

---

