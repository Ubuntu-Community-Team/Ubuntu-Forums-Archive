---
title: "How I broke Ubuntu"
date: 2007-06-17
forum: General Help
---

### Post by weblordpepe on 2007-06-17
Hello there.
I had a small SH script to run on startup in my gnome-session thingie in gnome.

The thing is - it was a SH script that ran itself. So it just looped.

And it completely rendered the desktop unusable. Coulnt ctrl-alt-fX to another window or anything. Had to boot to recovery mode.

I don't really need help with anything now but just as a pointer - don't make perpectual scripts and link them to startup.

---

### Post by zigx on 2007-06-17
good call, thanks for the heads up.

this is something that when you think about ... is common sense, but its so easy to make a mistake like that.

same thing as forgetting to an end " or ; when scripting for hours :) :KS

---

### Post by weblordpepe on 2007-06-19
What is kinda dissapointing is how easy it was to total the system with such a simple bit of code. 

If one had the password for a system you could write that in. In fact, it was only running as a normal user with no admin access. I couldn't actually log in as root to stop the proccess.

Maybe I could have logged in over network - I dunno. But the system was definately locked up. You guys should try it. Just make a sh script that calls itself, and put it in your session startup.

---

