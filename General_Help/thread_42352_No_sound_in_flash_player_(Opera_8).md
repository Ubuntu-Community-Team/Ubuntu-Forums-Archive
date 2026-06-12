---
title: "No sound in flash player (Opera 8)"
date: 2005-06-17
forum: General Help
---

### Post by sapo on 2005-06-17
Anyone knows how to fix it?

I ve using firefox.. but its is crashing each time i  open a flash movie and crashing randomly since i upgraded to the 1.04 version...

And a friend gave me an opera license.. so i m using it.. 

but i dont have any sound in flash player :( everything is working but the flash player is without sound...

anyone knows how to make it work?

thanx  :grin:

---

### Post by codejunkie on 2005-06-17
if your using kde i have no idea but with gnome mine was doing the same thing and i followed the guide configure sound properly at ubuntuguide.org and it seemed to fix the issue hope this helps.

---

### Post by Majlo on 2005-06-17
[QUOTE=sapo]Anyone knows how to fix it?

I ve using firefox.. but its is crashing each time i  open a flash movie and crashing randomly since i upgraded to the 1.04 version...

And a friend gave me an opera license.. so i m using it.. 

but i dont have any sound in flash player :( everything is working but the flash player is without sound...

anyone knows how to make it work?

thanx  :grin:[/QUOTE]

Try this in terminal

*sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1*

---

### Post by sapo on 2005-06-17
[QUOTE=Majlo]Try this in terminal

*sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1*[/QUOTE]

thanx a lot.. that worked :D

---

### Post by icedwater on 2007-01-13
Cheers, it helped for me too, but why? =)

Is it because the flash plugin is configured to look for /usr/lib/libesd.so.1 ?

---

### Post by mt330404 on 2008-04-25
worked for me too-- thank you very much!!!

---

