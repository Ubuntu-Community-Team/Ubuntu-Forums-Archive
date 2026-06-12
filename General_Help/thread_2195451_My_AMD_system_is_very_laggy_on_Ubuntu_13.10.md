---
title: "My AMD system is very laggy on Ubuntu 13.10"
date: 2013-12-24
forum: General Help
---

### Post by rahulbali on 2013-12-24
My sytsem is AMD FX 6300 8GB Ram and ATI 300 HD on board graphics which looks like a decent build but Ubuntu is very laggy specially the Unity, I have seen Unity operating much more smoother on very low end system but mine is pretty decent and I am using free ATI drivers, i tried non-free legacy drivers in other distros but they were horrible, can't even play a video file properly. Should I stick with free drivers or start using Non Free Legacy drivers ?

---

### Post by mips on 2013-12-24
Get a new GPU I reckon, even a lowly GT610 will be better.

---

### Post by rahulbali on 2013-12-24
I understand but for time being what should i do, please reply to the post ?

---

### Post by mips on 2013-12-24
> **rahulbali said:**
> I understand but for time being what should i do, please reply to the post ?

Sorry I have very little experience with ATI GPUs, especially one that old. Hopefully someone else has some good advice.

---

### Post by cariboo on 2013-12-24
Moved to General Help.

---

### Post by 3rdalbum on 2013-12-25
You need to remove the non-free ATI driver if you have installed it. It wontbwork with your old graphics card. Only the default, open-source one will work, albeit with low performance.

Unity can be sped up by turning off animations and semitransparency which causes most of the speed problems you notice on that old video card. Do a Google search, it is easy to turn off the animations and transparency and it makes a real difference on old ATI cards.

If you can't find the instructions on Google, PM me and I'll find the instructions for you from my archive.

---

