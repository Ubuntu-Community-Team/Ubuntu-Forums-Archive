---
title: "Wine won't work .."
date: 2007-10-09
forum: General Help
---

### Post by Naatan on 2007-10-09
Just installed Wine on Ubuntu Gutsy, quite a fresh install still..

When I try to launcn something I get the following error:

Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\root\\Desktop".

basically no matter what I do, it can never find the right path and is always complaining about < L"c:\... >

Anyone know what this might be

---

### Post by Naatan on 2007-10-09
still ..

---

### Post by Shazaam on 2007-10-09
Basics.....
Run winecfg?
Install winetools or similar?

---

### Post by Naatan on 2007-10-09
winecfg gives the same error

I shouldnt have to install winetools, and even if i did it wouldn't solve any existing problems.

---

### Post by Naatan on 2007-10-10
Problem solved by completely removing wine and then manually removing ~/.wine

(apperantly "completely remove" does not "completely remove" =\)

---

### Post by bartek_PL on 2007-10-12
hi!
I have a strange problem with my WINE
I have installed Roller Coaster Tycoon 2 for my brother and everything was great
but after exiting program and shutting down the computer and swiching it on next day......
it have not worked at all! the error message says: "Could not load ACTIVE MARK, check if the IE 4.0 is installed" what is going on?
RCT2 worked once... and now its dead... 
ANYONE HELP?!?!?!?

---

