---
title: "vol_id command"
date: 2007-03-14
forum: General Help
---

### Post by undecidable on 2007-03-14
In the posts about uuids, 
the command vol_id is mentioned.

However when I try the vol_id command, eg
  vol_id -u /dev/hda
(either with sudo or as su)
I get:  "command not found". 
I cannot see it as an available command in the repositories. 

I am using dapper drake 6.06.

Am I asleep at the wheel here,
Or is it not in 6.06?

---

### Post by desmondo on 2007-07-02
Try: /lib/udev/vol_id

Better late than never? :-)

---

### Post by undecidable on 2007-07-03
Thanks.  In fact it gets found in Feisty.
In any case, I should have thought to do a search myself :-(
I was just starting Ub then, 
and I did not think that there might be a command that was not on the path.

---

