---
title: "[SOLVED] Help - missing user database"
date: 2007-11-29
forum: General Help
---

### Post by d_e_monat on 2007-11-29
Uh, oh!

I have two ubuntu installs.  One is 32 bit Gutsy and the other is 64 bit Feisty (for experimentation).

Last night, everything seamed fine.  I shut-down normally and went to bed.

This morning the computer didn't start up right and there were a lot of messages that said, "group XXX does not exist" or "user database missing."

Needless to say, I could not log on.

I am glad that I have the 64 bit, to fall back on.

How can I rebuild the user database?

---

### Post by cmnorton on 2007-11-29
The first part of the message seems to indicate that something happened to /etc/group. I don't know what user database is, unless that is syntactic sugar for /etc/passwd.

---

### Post by d_e_monat on 2007-11-29
I would love to post a log, but none of them have any info from today.  The last entries are from last night (when everything worked).

Both /etc/group and /etc/password are there and readable.

I've also fsck'd the partitions and they are reported good.

I'm a little :confused:

---

### Post by d_e_monat on 2007-11-29
I found the problem.

Somehow the /lib/libdl.so.2 link was broken.  It had a strange charater burried in the link name :confused::confused:

I also found /lib/libnss_compat.so.2 was broken, also.

---

### Post by d_e_monat on 2007-11-30
Uh.  Relinking those files may not have been the whole answer.

I am still getting random "cannot find system.map" then kernel oops (es)

Some times it finds the system.map and boots up OK :confused::confused:

Anyone have any ideas?

---

