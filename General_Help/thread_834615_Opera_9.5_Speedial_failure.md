---
title: "Opera 9.5 Speedial failure"
date: 2008-06-19
forum: General Help
---

### Post by Daveth on 2008-06-19
Calling all Opera users! My speedial in Opera no longer accepts any commands, will not refresh or replace, or abandon any web page assigned to it, and the show/hide speedial option also seems to be missing.
Does everyone elses work? 

I have tried to re-load it without the speedial.ini, to force it to make a new one, but to no avail. It has been like this with the 9.50 betas as well, in both Hardy and feisty, so I guess there is some .ini setting somewhere that is misbehaving. Both compix fusion and avant are running, in case you wonder, with emerald as well.
Any suggestions as to a fix most gratefully received.

---

### Post by Daveth on 2008-06-22
cracked this one - in opera:config the speedial state option was set at 2, which does not allow edit. Changing it to 1 makes it work!

---

