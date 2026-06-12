---
title: "how to have a vista c: drive appear on a ubuntu wubi install"
date: 2008-06-21
forum: General Help
---

### Post by tunznath on 2008-06-21
I have installed for a friend Ubuntu using Wubi and would like to know how to make a c: drive from vista appear on the desktop - it isnt mounted and cant mount as i cant see it - any help appreciated - i can see the backup/restore part of the drive but not the c: part

---

### Post by tunznath on 2008-06-26
Can no one help on this?

---

### Post by ercferret18 on 2008-06-26
use /host

:):)

that means in file browser type in "/host" into the address bar lol

---

### Post by WeEatVista on 2008-06-26
Since no one appears to have the answer, i might as well put in a suggestion:

Install Wine Windows Emulator (can be found in add/remove programs, just search for wine)

Once Wine is installed, go to Applications --> Wine --> Browse C:/ drive.

This is just a suggestion, I am not entirely sure if this will work or not, but you might want to try this out.

Hope this helps,

We Eat Vista

---

### Post by ercferret18 on 2008-06-26
> **WeEatVista said:**
> Since no one appears to have the answer, i might as well put in a suggestion:

Install Wine Windows Emulator (can be found in add/remove programs, just search for wine)

Once Wine is installed, go to Applications --> Wine --> Browse C:/ drive.

This is just a suggestion, I am not entirely sure if this will work or not, but you might want to try this out.

Hope this helps,

We Eat Vista

that wouldn't work because that would be the virtual c:\ drive created at install, not the real one...

---

### Post by WeEatVista on 2008-06-26
> that wouldn't work because that would be the virtual c:\ drive created at install, not the real one...

lol true thanks for correcting me, I wasn't sure but no one else seemed to have a solution. Ill search on google maybe I can find something.

---

### Post by ercferret18 on 2008-06-26
the c drive is mounted under /host, thats the solution

---

### Post by tunznath on 2008-06-28
Thank you everyone for helping on this- appreciated

---

