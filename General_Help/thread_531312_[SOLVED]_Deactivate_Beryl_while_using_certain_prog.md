---
title: "[SOLVED] Deactivate Beryl while using certain programs?"
date: 2007-08-21
forum: General Help
---

### Post by sci-fi guy on 2007-08-21
Is there a way to have metacity run when I run certain programs that do not play well with beryl, and then have beryl automatically reactivate when I close said programs?

---

### Post by Chymera on 2007-08-21
none that i know of, unless you wanna go and write your own program.... however, if you are referring to video players not working (like vcl for example) you can select a different output mode.
VLC-> Settings -> Preferences -> Video -> Output modules
In the dropdown list, select another, e.g. X11, XVideo or OpenGL.

---

### Post by sci-fi guy on 2007-08-21
Actually, I was talking about Blender, Celestia, and until recently, programs running in fullscreen mode under wine. But I haven't used any media players...

---

### Post by Chymera on 2007-08-22
Well it was the video players i had problems with in ye olde beryl days.... but now i use compiz fusion and have yet to come across any issues of that sort.
But i am sure something similar can be done with any other app, as long as you find how to change its output mode, however i havnt used blender or wine until now so i couldnt know about that.

If it really isnt possible to change the output module you may want to try creating a launcher (and setting a shortcut key) for each of the commands 
```
metacity --replace
```  - turn beryl off
```
beryl --replace
``` - or - ```
beryl --replace &
``` - turn beryl back on (use the 2nd only if the 1st won't work)

you will still not be able to have it switch automatically but you would have a handy way for switching beryl on and off (like super+ctrl+y/n)

---

