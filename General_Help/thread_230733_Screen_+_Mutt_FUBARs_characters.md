---
title: "Screen + Mutt FUBARs characters"
date: 2006-08-06
forum: General Help
---

### Post by allnameswereout on 2006-08-06
Hey,

I have this small issue with Mutt and Screen I did not have on my Debian/Sarge SPARC.

Here it is:
1) I use PuTTy to SSH to my Ubuntu/Dapper SPARC server.
2) Fire up Screen there. 
3) Ssh to an SSH server.
3) Fire up Mutt on SSH server.

My layout of characters is then screwed. For example if someone wrote an e-mail, and then a reply with same subject is given, there is an arrow to indicite its a followup. This arrow is not an arrow, instead it is a weird A character.

The layout is correct when I do the following:
1) I use PuTTy to SSH to my Ubuntu/Dapper SPARC server.
2) Ssh to an SSH server.
3) Fire up Mutt on SSH server.

OR

1) I use PuTTy to SSH to my SSH server.
2) Fire up Mutt on SSH server.

However I really want to use my systems as described in the way which doesn't function (the 4 steps). I checked out my TERM variable. Its the same in situation 1 and 2. What is being a bitch here?

---

### Post by allnameswereout on 2006-08-21
Up.

---

### Post by allnameswereout on 2006-09-06
Up.

---

