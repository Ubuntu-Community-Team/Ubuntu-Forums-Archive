---
title: "problem launching an ssh connection with a new X session"
date: 2008-02-18
forum: General Help
---

### Post by Biochem on 2008-02-18
To connect to one my my University server I need to pass through ssh, XDMCP doesn't work well in gutsy even with the patch. Right now this is what I do:

xinit -- :1 vt12
than in the new X server
ssh -X user@host
startkde

It work, but what I would like to do is write a script that would send the ssh command automatically in the new X server to make it easier for new user. I read the Xinit man page but I can't find the appropriate option.

I tried:
xinit -e $(ssh -X user@host) -- :1 vt12
and
xinit -- :1 vt12 -e $(ssh -X user@host) 
both command ask for the password but none give me a new x server.

Am I asking for someting impossible or is there some magic somewhere I unaware of?

Thank you for your time.

---

