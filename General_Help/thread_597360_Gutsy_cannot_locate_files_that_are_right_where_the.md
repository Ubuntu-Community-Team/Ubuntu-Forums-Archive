---
title: "Gutsy cannot locate files that are right where they are supposed to be ?"
date: 2007-10-30
forum: General Help
---

### Post by WIREHEAD on 2007-10-30
I was trying to get MP3 export capable in Audacity , to do this I needed libmp3lame.so .

In a terminal :
 " locate libmp3lame.so " gives no results , program terminates with no output .

I used synaptic to install liblame-dev .
locate gives same result

Interestingly enough navigating through the file system shows that I actually DO have the file .

Places > Computer > Filesystem > usr > lib , then scrolling down to the bottom third of the page shows libmp3lame.so is right there where it should be .

Right clicking on the file then selecting " properties " shows this file as a link to libmp3lame.so.0.0.0 ( which is also there ) , however the file permissions on these files are set to " root " .

In a terminal :
 " gksudo " nautilus let me change file permissions .
locate still gives same result .

Audacity appears to not be able to actually use this file either , but shows 3.97 Lame library is current ( this may be unrelated , I dunno ).

So like what the heck do I do now I'm stumped ?

WIREHEAD

---

### Post by cdenley on 2007-10-30
locate doesn't actually search the hard drive, it searches an index of files which I believe is updated daily. If you want to update the index manually, run "sudo updatedb".

---

### Post by WIREHEAD on 2007-10-30
Ahhhh....

More of that darn learning stuff , DANG ! I hate it when that happens ....

Thank you very much !

Problem solved .

WIREHEAD

---

### Post by WIREHEAD on 2007-10-30
BTW

sudo uptadedb is pretty close to sudo updatedb , which works .:lolflag:

---

### Post by cdenley on 2007-10-30
my bad, I fixed it.

---

