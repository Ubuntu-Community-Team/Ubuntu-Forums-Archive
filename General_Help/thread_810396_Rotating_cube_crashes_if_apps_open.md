---
title: "Rotating cube crashes if apps open"
date: 2008-05-28
forum: General Help
---

### Post by riseringseeker on 2008-05-28
I have searched around here, but have not found an answer to one of the very few problems I am having with 8.04, so thought it time to post a request for help.

I am running 8.04-64 on a System76 Darter Ultra (Daru1).  I have compiz, ccsm and fusion-icon installed.  All the effects work like they should but one.

If I try to rotate the cube with *any* apps appearing on the desktop, it crashes before I even see the cube.  Funny thing is, if there are no apps open, or they are minimized to the system tray, the cube rotation works fine.  

If no apps are on the desktop (or open) I can rotate the cube with either <ctrl><alt><button1> or <button1><button2> and the mouse pad.  The second key binding is not listed anywhere that I can see, but works (again, if no apps are open to desktop).

If anyone has a clue, would appreciate a response.

---

### Post by sayakb on 2008-05-28
Did you import the compiz profile from an old one? Do you have the 3D plugin running?

---

### Post by riseringseeker on 2008-05-28
> **LinuxIsInnovation said:**
> Did you import the compiz profile from an old one? Do you have the 3D plugin running?

Nope, clean install.  Since I *can* rotate the cube, yes, 3D is working and installed, at least I think it must be.  It only does *not* work if an app is open.

---

### Post by DaymItzJack on 2008-05-28
> **riseringseeker said:**
> Nope, clean install.  Since I *can* rotate the cube, yes, 3D is working and installed, at least I think it must be.  It only does *not* work if an app is open.

Try disabling the 3D plugin. The 3D plugin makes your windows pop out a little bit while the cube is rotating and since you said it errors only when the 3D plugin should be doing anything, it would be best to try and disable it.

---

### Post by riseringseeker on 2008-05-28
> **DaymItzJack said:**
> Try disabling the 3D plugin. The 3D plugin makes your windows pop out a little bit while the cube is rotating and since you said it errors only when the 3D plugin should be doing anything, it would be best to try and disable it.

That worked, thanks so much!!

---

