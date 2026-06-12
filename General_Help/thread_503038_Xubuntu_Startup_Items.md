---
title: "Xubuntu Startup Items"
date: 2007-07-17
forum: General Help
---

### Post by shavenlunatic on 2007-07-17
Hi,

Recently made a side-jump from Ubuntu to Xubuntu.. so far I actually like it.. quite a lot.

With ubuntu, if I wanted to add/remove an item which will run after I log in I would go into sessions.  Xubuntu has an "autostarted applications" ).. which seemed the logical place for me to add/remove items.

So, I'd installed Pidgin (and Skype).. they both run when I log in.. but are not listed in the autostarted applications list.. any ideas?

---

### Post by shavenlunatic on 2007-07-18
*bump*

---

### Post by bobbydale on 2007-07-18
I am experiencing this exact same issue.

---

### Post by shavenlunatic on 2007-07-18
and I assume that from the silence.. nobody knows a work-around :(

---

### Post by shavenlunatic on 2007-07-20
*re-bump*

---

### Post by UJoe4 on 2007-07-20
1) Close all applications, then log out and be sure to tick "Save session for future logins". Log back in, and see if that fixes it. Either way, you can then untick it the next time you log out.

2) If you have the directory "/home/yourusername/Desktop/Autostart/", look around in it.

3) Same for "/home/yourusername/.config/autostart/"

4) If the file "/etc/X11/gdm/PostLogin/Default" exists, look through it.

5) I'm not familiar with either of those programs, can you find any "start automatically" options either in the GUI or in the man pages?

Hopefully one of those will work.

---

### Post by shavenlunatic on 2007-07-20
> **UJoe4 said:**
> 1) Close all applications, then log out and be sure to tick "Save session for future logins". Log back in, and see if that fixes it. Either way, you can then untick it the next time you log out.

2) If you have the directory "/home/yourusername/Desktop/Autostart/", look around in it.

3) Same for "/home/yourusername/.config/autostart/"

4) If the file "/etc/X11/gdm/PostLogin/Default" exists, look through it.


Cheers, will have a play with these. :)  I think I went into the /.config/autostart and nothing was listed in there.. but will have another check and look at the rest :)

> 
5) I'm not familiar with either of those programs, can you find any "start automatically" options either in the GUI or in the man pages?

First place I looked (too many years of supporting windows) but then realised the app would have to have sudo rights to change the startup apps I think.. anyway, the option didn't exist within the apps preferences

---

