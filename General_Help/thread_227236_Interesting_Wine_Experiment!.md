---
title: "Interesting Wine Experiment!"
date: 2006-08-01
forum: General Help
---

### Post by lemix on 2006-08-01
I had an interesting idea to copy the 
> c:/windows/system32
Folder to a ubuntu dapper drake installation and put all the files from the System folder in
> ~/.wine/drive_c/windows/system32
and an expected thing happened. When i restarted my computer, it crashed. (Damn you windows)

This isn't a problem anymore but i was wondering if anyone could look at the ceiling for a breif second and come up with the answer. More like a riddle for you.

I was just wanting some more windows drivers to make a Super Wine! Like that damn good for nothing Cedega.

---

### Post by Tomosaur on 2006-08-01
Why would you expect this to work in the first place? :O

---

### Post by Half-Left on 2006-08-01
You do realize that WINE has no windows code what so ever?, replacing it with native dll's is a good way to screw up WINE.

---

### Post by lemix on 2006-08-01
no way! errors occur frequently when installing applications due to missing dlls and you can fix them by downloading the external dependencies dlls and such. i was just giving wine all of them to use at once.

And it didnt just mess up wine, it messed up the whole system.

And i didnt expect it to work. Hence experiment. If i expected it to work i would have asked why this did not work. Take it easy gents!

---

### Post by hollaburoo on 2006-08-01
it didn't work because there are some dlls  (4 I believe) that wine MUST do itself.  They're very low level system dlls that cant be replaced without breaking linux whenever they're called.  And I think wine is loaded once when ubuntu starts, not sure though.

---

