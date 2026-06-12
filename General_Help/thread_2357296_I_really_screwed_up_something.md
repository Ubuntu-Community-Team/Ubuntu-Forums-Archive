---
title: "I really screwed up something"
date: 2017-03-31
forum: General Help
---

### Post by jrmymllr on 2017-03-31
I have 64 bit Ubuntu Server 14 LTS.

I was trying to get a web-based SSH system to work and per the advice of a webpage ran this command:

sudo apt-get install libssl0.9.8 libpam0g openssl

So far, no problem.  Well, I decided to go a different route so I ran:

sudo apt-get remove libssl0.9.8 libpam0g openssl

A colored screen appeared saying something about there being no PAM profile to remove, choose the one to remove.  There was nothing in the list, and I couldn't get out of it so I closed the SSH session, and now I can't login even at the attached monitor and keyboard.  I know enough to be dangerous, and upon looking up what libpam0g is, I think that's just what I was.

So, I can't login, the Samba share isn't there, however I have a security camera system running that is still accessible so something is running.

Is there any way to fix this, or is it a reinstall?

edit: SOLVED.  I restored my boot drive from backup.  Fairly painless.

---

