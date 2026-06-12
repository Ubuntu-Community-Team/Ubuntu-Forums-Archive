---
title: "Blender 2.71 crashing on armature bone edit"
date: 2014-06-26
forum: General Help
---

### Post by vanessax on 2014-06-26
Has anyone else noticed that, since upgrading to the new Blender 2.71 from the Irie repository, editing any armature bone in the 3D view causes Blender to crash?

---

### Post by Bobisha on 2014-06-29
The same thing happens to me too. I even tried reinstalling blender and it still happens. I even did a fresh system install as well o see if that might be the problem, and I got the same results. I am not sure what the problem is, but if I find something out, I wil llet everyone here know.

---

### Post by vanessax on 2014-06-29
I had to go back to Blender 2.70, it works without crashing.

Two problems with 2.70; sometimes moving a bone does not cause any meshes with weight associated with that bone to move, you have to move the bone (wiggle it) several times to get the mesh to move (in pose mode).

Editing a latice vertex will cause a crash in 2.70. :(

---

### Post by BCtom on 2014-07-27
I'm having the same issue too. I'm filing a bug report with Blender since I have not seen any bug reports about this on their bug tracker.

---

### Post by BCtom on 2014-07-28
Okay, after submitting a bug report at Blender.org, this was the response I got in less than 1 day:

"[mont29]("https://developer.blender.org/p/mont29/") closed this task as "Invalid".Via Web · [Mon, Jul 28, 12:37 PM]("https://developer.blender.org/T41218#8")[mont29]("https://developer.blender.org/p/mont29/") claimed this task.
[Comment Actions]("https://developer.blender.org/T41218#")You  are using Blender 2.71RC1, which had known bug with armatures and  lattice. Please use real 2.71 release, not release candidates!"

I loaded up 2.71 (stable), and voila, creating an armiture worked flawlesly. 

Hope this helps you all out.

---

