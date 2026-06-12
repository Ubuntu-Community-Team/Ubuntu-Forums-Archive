---
title: "How do I make a program start as another user?"
date: 2012-12-19
forum: General Help
---

### Post by Hungry Man on 2012-12-19
I know how to do so from a  custom .desktop file that runs gksudo blah blah blah.

How do I have the program always run from that user, even without being launched by the special file?

---

### Post by rnerwein on 2012-12-20
> **Hungry Man said:**
> I know how to do so from a  custom .desktop file that runs gksudo blah blah blah.

How do I have the program always run from that user, even without being launched by the special file?
hi
i only now this with a C-program (for shell scripts it don't work)
for the executeable program you have to following steps (assume the program name is 
blablu
1. sudo chown desired_user:desired_grop blablu
2. sudo chmod 4755 blablu
4755 gives the permissions: -rw[COLOR=Red]s[/COLOR]-r-x-r-x  where the s-bit is called set-id bit.
your program will then with the user-id desired_user.
have fun but be careful with those thinks. 

cheers

---

