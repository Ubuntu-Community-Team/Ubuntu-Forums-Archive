---
title: "Evolution Calendar off by three days..."
date: 2005-08-10
forum: General Help
---

### Post by erjohan on 2005-08-10
Hi I'm using evolution as a planning tool/ setting up meetings etc.. Now when I use the "calendar month overview widget" on the right side, it's off by three days. Whenever I press July 9th I will be shown the day for July 6th, even though the 9th is marked in the widget. I think this happened during the summer sometime, but it has definitely no been like this before that. I deleted .evolution and .g* and it's still the same even after this.

Further I just noticed (actually it was why I noticed the offset), I have no meetings at all when in day view, but when in week view sure thing I can see them.. This might  be related.. ;-)


So 
[list]
[*]Is there anyone with a clue about evolution
[*]Dos anyone know if evolution has been updated by Ubunut in hoary
[/list]


I just remmebered that I'm not sure evolution ever worked in Hoary, It did in Warty though. But please test this on your installations..

---

### Post by nocturn on 2005-08-10
Strange...

I have evolution working fine...  It has not been updated after the release of Hoary.
Can you try this with a clean profile (save your .evolution directory to .evolution.old)?

---

### Post by erjohan on 2005-08-10
Ok I've solved it  :D   . Was really bad bug. this is what I did:
[list]
[*] Created a new user - still the same
[*] reinstalled evolution - still the same
[*] Changed my timezone - still the same (/etc/localtime)
[*] Changed my timezone in GNOME - and it worked.
[/list] 

 Looked around gnome menus, saw that my timezone (in GNOME) wasn't set, really strange considering that I have a timezone set for my system..

---

### Post by nocturn on 2005-08-10
[QUOTE=erjohan]Ok I've solved it  :D   . Was really bad bug. this is what I did:
[list]
[*] Created a new user - still the same
[*] reinstalled evolution - still the same
[*] Changed my timezone - still the same (/etc/localtime)
[*] Changed my timezone in GNOME - and it worked.
[/list] 

 Looked around gnome menus, saw that my timezone (in GNOME) wasn't set, really strange considering that I have a timezone set for my system..[/QUOTE]

That's pretty strange, I haven't set a timezone in Gnome either... some weird coinsidence...

---

### Post by erjohan on 2005-08-10
maybe my timezone info wasn't setup correctly. but got corrected by using the GNOME setup tool..

---

