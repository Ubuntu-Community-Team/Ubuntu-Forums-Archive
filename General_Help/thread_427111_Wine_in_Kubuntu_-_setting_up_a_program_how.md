---
title: "Wine in Kubuntu - setting up a program how?"
date: 2007-04-29
forum: General Help
---

### Post by mpooley on 2007-04-29
Hi
I am using wine for the first time and the new wine settings utility is very confusing (to me!) also as usual it seems there is no help file!

I want to install a program called code wallet pro- I have clicked 'add program' and put the setup.exe in there - is that right?? whatever it doesn't do anything and i cant see what to do next?
am i going about this the right way?

can someone help me please?

---

### Post by shirilover on 2007-04-29
To install the program you can either double-click the setup.exe file or execute 'wine setup.exe'

---

### Post by mpooley on 2007-04-29
> **shirilover said:**
> To install the program you can either double-click the setup.exe file or execute 'wine setup.exe'
thankyou:)  that worked fine and the installation worked ok no problems:) 

now i take it i then add that exe into the wine setup yes?

i did this and when i ran the program i get an addition to my taskbar that wont do anything!
eeg a left/right click - double click nothing !

what should i do now?

---

### Post by scooper on 2007-04-29
It may be crashing.  I'd find where the program is installed, e.g. "~/.wine/drive_c/Program Files".  Then I'd run from the command line "wine "~/.wine/drive_c/Program Files/My Program/program.exe" where you substitute the appropriate path.  At least you may see error messages.

There are fancy ways to control what DLLs are used, etc. on a per-app basis, but I've never played around with that.  Hopefully someone else can provide that guidance.  Basically I think you can choose whether or not to use real DLLs from a WIndows installation vs. wine's emulation DLLs.

Hope that's slightly helpful.

---

### Post by mpooley on 2007-04-29
Thanks 
I tried that and this is what i got 
wine: could not load L"c:\\windows\\system32\\devo                      necwpro5desktop.exe": Module not found

so it seems to be looking for some module ij system32?

oh dear!

I havnt got a clue now !   lol

---

