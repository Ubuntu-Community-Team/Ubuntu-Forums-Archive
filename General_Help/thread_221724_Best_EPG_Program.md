---
title: "Best EPG Program?"
date: 2006-07-23
forum: General Help
---

### Post by tonyr1988 on 2006-07-23
I'm tired of opening websites to find out what's on TV. Is there any Electronic Program Guide that will tell me what's playing on TV in Ubuntu?

The only one I've found (TV-Browser) only works for German TV. None for America?

If not, it's really no big deal. Checking TV Guide's website or tv.yahoo.com isn't too inconvenient - just thought I'd check.

---

### Post by JoWilly on 2006-07-23
OnTV (gnome applet, in the repo) , TVlistings, there are others.

You need to configure xmltv to get them to work (there are howtos).

---

### Post by tonyr1988 on 2006-07-24
> **JoWilly said:**
> OnTV (gnome applet, in the repo) , TVlistings, there are others.

You need to configure xmltv to get them to work (there are howtos).

I downloaded OnTV from the repo, and it shows up as a Panel (looks cool). I can't find anything on the xmltv configuration, though. It's asking for an xmltv file, but I don't know how to make one of those.

---

### Post by JoWilly on 2006-07-24
Howto setup xmltv here (search google for better howtos):
[http://cvs.gnome.org/viewcvs/ontv/README?view=markup]("http://cvs.gnome.org/viewcvs/ontv/README?view=markup")

Ontv screenshots:
[http://johan.svedberg.com/projects/coding/ontv/#screenshots]("http://johan.svedberg.com/projects/coding/ontv/#screenshots")

gtvlistings shots:
[https://sourceforge.net/project/screenshots.php?group_id=124066]("https://sourceforge.net/project/screenshots.php?group_id=124066")

---

### Post by tonyr1988 on 2006-07-24
I got it working fine, but there's one problem: it's wrong! I tested it with a random channel on TV, and it wasn't right. I tried two different time zones (in case I got daylight savings wrong), and neither of them are right. Should I just type in a wrong time zone to hopefully make them correct, or what?

This is an awful lot of hassle, though (not that I mind...I think messing with this stuff can sometimes be fun) for something that's easily accessible on the 'net.

---

### Post by JoWilly on 2006-07-24
> **tonyr1988 said:**
> I got it working fine, but there's one problem: it's wrong! I tested it with a random channel on TV, and it wasn't right. I tried two different time zones (in case I got daylight savings wrong), and neither of them are right. Should I just type in a wrong time zone to hopefully make them correct, or what?

This is an awful lot of hassle, though (not that I mind...I think messing with this stuff can sometimes be fun) for something that's easily accessible on the 'net.

Yes, I don't understand why ontv does not automatically setup xmltv.

Contact the author to report your bug (so that the time you have lost can be of some use :) ) and also ask the author when he will and automatic xmltv support. This manual xmltv configuration definitely should not be acceptable for a gui app.

---

### Post by JoWilly on 2006-07-25
I had an email exchange with the author.

He said he will implement xmltv setup with a gui in ontv. Something like this :

[http://gshowtv.sourceforge.net/xmltv-druid.html]("http://gshowtv.sourceforge.net/xmltv-druid.html")

---

