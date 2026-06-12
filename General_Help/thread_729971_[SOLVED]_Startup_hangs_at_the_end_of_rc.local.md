---
title: "[SOLVED] Startup hangs at the end of rc.local"
date: 2008-03-20
forum: General Help
---

### Post by chochem on 2008-03-20
My startup process hangs at the end of the rc.local script, after I disabled GDM by way of bum. 

I have seen several posts indicating that this, i.e. disabling GDM, would be sufficient in order to have a startup that would end at the command line. I have commented out everything in rc.local except 'exit 0', thinking that some of these lines might prove a problem but that doesn't seem to be it (besides, as pointed out above, it says [OK]...?) 

Any suggestions to what it is it's waiting for?

---

### Post by Jose Catre-Vandis on 2008-03-20
What happens if you press "Enter" or "Return" at this point, do you get a login prompt?

I get this with my server which only runs a command line. i never see it because it is headless, so whenever I ssh in i get a login prompt

---

### Post by chochem on 2008-03-20
I don't think I get anything (though I can only precisely recall having hit Ctrl-c)... It seems pretty stuck, only reacting to Ctrl+Alt+Del :(

---

### Post by chochem on 2008-03-20
Well I'll be.... You're right :) Hit enter and I get a login prompt. It's nice to know that  but I wish it could be avoided  if for nothing else just for aesthethic reasons...

EDIT: BTW what does this mean (ssh?):
> **Jose Catre-Vandis said:**
>  i never see it because it is headless, so whenever I ssh in i get a login prompt

---

### Post by submerged2go on 2008-03-20
For definition of SSH, Wikipedia is your friend: [SSH Explanation]("http://en.wikipedia.org/wiki/Secure_Shell")

Basically, it is just a way to create a very secure connection between two computers, in effort to prevent snoopers and anyone else on the same network seeing what you are doing at the time you have accessed the computer.

---

### Post by chochem on 2008-03-20
So what he's saying is that it isn't an issue for him because he logs in from another computer...? That doesn't help me, though. I'm stuck with this old hunk o' junk... :)

---

### Post by chochem on 2008-03-21
A pseudo-solution to a pseudo-problem: I added 'chvt 2' to my rc.local script, just before exit 0. This has the effect of switching to virtual console 2  at then end of startup, presenting me with a nice clean login.

---

