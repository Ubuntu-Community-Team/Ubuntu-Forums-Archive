---
title: "the &quot;search&quot; option in the left panel of the &quot;save as&quot; command of several application"
date: 2018-01-19
forum: General Help
---

### Post by gianluca3 on 2018-01-19
dear all,

not easy to explain for a not-expert as I am...

several applications such as Thunderbird, Gedit, Firefox misses the "search" option in the left panel of the "save as" command. Some other such as, e.g., Open Office, they have it.

I remember very well that TB had it for a while, I also wrote in a TB forum but it seems that this a Ubuntu feature rather than TB one.

Any idea on how to restore this useful option?

thanks in advance and sorry for the poor description
g.

uname -a
Linux laresa 4.4.0-109-generic #132-Ubuntu SMP Tue Jan 9 19:52:39 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Dennis N on 2018-01-19
Looks as if the 'search' feature appears in the gtk2 file 'open/save as' dialog. It is removed from the gtk3 version. So, applications that now use gtk3 won't have that feature any longer.

---

### Post by vanadium on 2018-01-20
gtk3 dialogs "save as" have the search function, but in Ubuntu, it is broken because they try to keep the type-ahead feature in. You still can activate the function with Ctrl+f while your cursor is in the name field. You will see the search field pop up. Start typing your search term, and you will see that after two or three key presses, the type-ahead function kicks in. This will work as designed on other distributions than Ubuntu.

---

### Post by gianluca3 on 2018-01-20
thanks for your replies.

the ctrl+f "would" solve my problem, however... it works in a weird manner. Tried both with TB and Gedit:

- I hit ctrl+f and the search field nicely pops up in the top-center of the window
- type the first letter, ok
- when I type the second letter and following this goes in a bottom-right field (unless I'm very, very fast in typing as in the attached image)

best
g.

---

### Post by vanadium on 2018-01-22
That is exactly the issue I was pointing out in my previous post.

---

### Post by gianluca3 on 2018-01-22
yes, sorry, i misunderstood. so, it doesn't work very nicely... :(

---

### Post by gianluca3 on 2018-02-08
meanwhile i had the time to check a live distribution with gnome and the issue with the search is exactly the same... :(

it seems to me a huge drawback, so maybe there is an alternative way i'm not aware of? 

best
g.

---

