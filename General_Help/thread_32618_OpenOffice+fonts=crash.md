---
title: "OpenOffice+fonts=crash??"
date: 2005-05-08
forum: General Help
---

### Post by rookworm on 2005-05-08
I recently copied a few thousand type 1 fonts into /usr/share/fonts .
Now both versions of OpenOffice (1 and 2-beta) crash on startup. Normally, I'd just remove the fonts, but there are too many, and it's hard to tell which are which anyway. I'd like to know how I can either rm /usr/share/fonts/* and reinstall what was originally there (tell me which packages), or, barring that, to just remove the offending fonts (does openoffice log that sort of thing?). 

Thanks-- Ubuntu is awesome, this is my first headache with it. ;)

---

### Post by rookworm on 2005-05-10
Anyone?

---

### Post by tread on 2005-05-11
Hmm .. you could try to figure out which package installed the fonts, and then delete everything, and reinstall using apt-get from the console.

That should work, I think. I appreciate the fact thats my post is not really a solution, but I don;t know a solution, and this is how I would start to solve the problem :)

---

