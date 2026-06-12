---
title: "GAIM direct connect doesn't work"
date: 2005-06-13
forum: General Help
---

### Post by xbilly on 2005-06-13
I seem to be having trouble with direct connecting and file transfers on gAIM. When I send a file, it doesn't get past the "waiting for file transfer to begin" status.

---

### Post by Arthemys on 2005-06-13
Are you behind a NAT box or router of any sort?

---

### Post by skoal on 2005-06-13
hmmm...

I've been getting this same nagging issue recently on 3 different versions of gAIM.  However, I tend to suspect it has something to do with my router I just recently hooked up.  As best I can tell, it all started then.  Anyone know what ports I need to open up on this doohickey?

\\//_

---

### Post by Arthemys on 2005-06-14
I just route port 5190 to my box for both TCP and UDP. Works sometimes. I barely really use it, I just use my web server for transfer now, that and SCP.

---

### Post by skoal on 2005-06-14
Ahh, thanks for the info.  I went ahead and set myself up in the "Demilitarized Zone" (DMZ) for my router.  I'll test it out in a bit, and if that works, I'll narrow it down to the exact port or google for it later.

thx.

\\//_

---

### Post by Arthemys on 2005-06-14
AIM uses port 5190 for DC.

---

### Post by skoal on 2005-06-14
Ahh...thank you sir!  Direct Connect works again, at least for me.  There were some issues with a latter release (1.2) I believe, like total lockups when sending images (but that's another thread and another time).  However, I'm using 1.3 now with those ports open on my router and have no problems.

\\//_

---

