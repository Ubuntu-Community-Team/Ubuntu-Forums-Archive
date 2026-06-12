---
title: "What does the session startup program do?"
date: 2007-05-27
forum: General Help
---

### Post by B-Con on 2007-05-27
If you add a program to your session startup via
```
System -> Preferences -> Sessions -> Startup Programs
```
what actually happens? I looked through my /etc/init.d directory and found no changes, so, I'm wondering what settings get added where to make the startup program you specify actually start on startup?

---

### Post by Ateo on 2007-05-27
Launches programs when you log in to Gnome. Sort of like Start -> Program -> Startup in Windows.

---

### Post by B-Con on 2007-05-28
Yeah, but I mean, how does it do that? Ie, if I wanted to add something to that list or write a script to manipulate it in some way, where would I look for the data files?

---

### Post by thesm on 2007-06-13
> **B-Con said:**
> Yeah, but I mean, how does it do that? Ie, if I wanted to add something to that list or write a script to manipulate it in some way, where would I look for the data files?

I don't think this is exactly what you wanted but I had a similar question and this thread answered it: [http://ubuntuforums.org/showthread.php?t=389955&highlight=startup+program](http://ubuntuforums.org/showthread.php?t=389955&highlight=startup+program)

Basically you edit /etc/rc.local .  If you want to run a program that you want to continue running add an ampersand & to the end of the line (to make it run in the background I think).  Not sure what happens when you add a program to startup sessions since none of the programs I have running at startup are listed in this file.  Hope this helps you.

---

