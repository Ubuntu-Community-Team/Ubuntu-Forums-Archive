---
title: "program loads at startup unrequested"
date: 2007-06-16
forum: General Help
---

### Post by maarten80 on 2007-06-16
I'm having this strange problem. Everytime I boot into my Xubuntu skype is started automatically, twice!

I don't want it to load automatically and obviously not twice.

It's not in autostarted applications and I don't have a .config/autostart folder/file.
I tried shutting down with saving a empty session. But no luck. They (the skypes) just keep showing up.

Very curious, does anyone know where to find programs that load on startup? Which file needs to be configured and probably holds this faulty applications?

(remind that I'm using xubuntu)

thanks!

---

### Post by zazen666 on 2007-06-16
i'm having a similar problem. I noticed it happend after i used a "saved session" function. then after unchecking "save session" some programs, like totem, are loading un requested. I too am using xubuntu.
Any one can help?

---

### Post by kmangwing on 2007-06-16
I had a similar problem when I first installed xubuntu.  When you go to the shutoff screen, there is a checkbox for something about sessions.  If it is checked, any program that is open when you turn off the computer will reload once you turn it on again.  Simple solution: before shutting off your computer, turn off all programs you don't want to come back up when you restart, or simply uncheck the box.

---

### Post by maarten80 on 2007-06-17
Thanks for the suggestion, but I already tried that and it's not working.

Glad I'm not the only one having this strange problem

---

### Post by zazen666 on 2007-06-17
Hey Guys I found the solution!!!!
Close all the programs that are starting up automatically, then click "save session" and log out. Once you log back in , it should take care of the problem.

At least it worked for me.

It seems that  "save session" works like this: It saves the opened programs at the time you click it and shut down, to be opened FROM THEN ON. In other words, even if you turn off saved sessions later, you are not actually disables the earlier saved session, you are just telling the computer not to save the CURRENT session. So if you want to save the current session (i.e., so as NOT to start up a certian program) then shut down the program(s), then do a new save session before shuting down.

hope this works for you guys.

---

### Post by maarten80 on 2007-06-19
I think I did that... you mean just logging out with no active programs and the save session button enabled? That did not work.

I ended up uninstalling skype which (obviously?) took care of my problem. I didn't reinstall it though too see whether the problem would come back or not...

Isn't there anyone who knows which configuration file actually holds the entries for the programs that have to load at startup? If we could find that, eliminating unwanted startups could be easily resolved by editing this file..

---

