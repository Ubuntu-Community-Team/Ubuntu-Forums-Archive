---
title: "problem with terminal"
date: 2023-07-14
forum: General Help
---

### Post by jgw on 2023-07-14
I am trying to install a program and I am being asked for a password.  I tryING  to enter the password.  I found out I can enter nothing when this occurs.  I am trying to install  pia vpn. I cannot paste OR enter the password.  

Thank you......................

---

### Post by Holger_Gehrke on 2023-07-14
Might work if you just type the password blindly and hit enter; that is the standard behaviour of 'sudo' (and no, that's not a programming error; it's meant to stop "shoulder surfers" from seeing the length of the password which would make brute force attacks on the password simpler).

Holger

---

### Post by #&amp;thj^% on 2023-07-14
If Holger_Gehrke suggestion dose not work, then what password are you trying to enter?
I has it's own login credentials. 1st username and then that 2nd password .
Not to be confused with Ubuntu user password

This is still the suggested install from PIA
After you Download your app or run file, then run from the directory it is in:
```
cd Downloads
```
Then run the installer and no "sudo" yet
```
sh pia-linux-<current version>.run
```
The installer will prompt you for your [Root/Sudo] password (Note: do not run the installer with sudo)
Is this where you get stuck??

---

### Post by jgw on 2023-07-14
thank you for the replies!

I got it done.  It was very odd.  I did the install yet again.  This time, when it asked for my password I gave them my system password.  When I did that it just went away.  So, I did it again!  This time it installed everybody.  During the entire time I never had to give them my name or password, it just got installed!  None of this makes any sense but it worked!

One can only wonder - thanks again!

---

### Post by ActionParsnip on 2023-07-14
Yes you won't get feedback in most cases when you enter a password. This is to hide it's length

---

