---
title: "Terminal Server Client"
date: 2008-03-22
forum: General Help
---

### Post by mreynaga on 2008-03-22
i am having a small issue with using the terminal server client. wen i try to login to my terminal server (windows server 2003) as either administrator or my own account (which is an administrator) it logs out the console administrator. 

any way to stop it from doing this? because then if i log in with the admin login and someone back at the office tries to login as the admin it kicks me out. 

plus i cannot have more than one 1 terminal server session going from my laptop because it givves the error that it needs to kick the others off first.

any help please I know terminal services 2003 supports up to 3 simultaneous admin logins (2 remote and 1 at the console) so why is ubuntu doing this?

---

### Post by dchurch on 2008-03-22
I'm not sure it's an Ubuntu error - I had a similar thing with Win2k server, from a Win95 (yes, I know!) machine it would do as you described, but from an XP machine it would behave.

I never did sort it out - but it might help you to diagnose the problem. It must be something to do with the client software, that is a given.

Have you tried it from another OS/Machine?

---

