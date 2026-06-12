---
title: "Compiz : Gutsy Gibbon and Nvidia .run driver"
date: 2007-10-22
forum: General Help
---

### Post by fluffykitten on 2007-10-22
Hi everyone,  

I have installed Ubuntu Gutsy Gibbon release version on a notebook, removed the restricted-modules package and installed the NVIDIA .run file.  I cannot use the nvidia-glx package, and need to use the .run file.

My problem is, on starting X, the window decorations (borders) don't show up.  So i can't move windows around or anything of the sort.  

I tried adding the following 2 lines to .Xinitrc with no effect :-

gtk-window-decorator &
compiz --replace gconf &

Any help would be greatly appreciated.

---

### Post by sdil on 2007-10-22
i think that is because compiz ... it's also my problem when using compiz window .....

---

### Post by Jwendib on 2007-10-25
> **fluffykitten said:**
> Hi everyone,  

I have installed Ubuntu Gutsy Gibbon release version on a notebook, removed the restricted-modules package and installed the NVIDIA .run file.  I cannot use the nvidia-glx package, and need to use the .run file.

My problem is, on starting X, the window decorations (borders) don't show up.  So i can't move windows around or anything of the sort.  

I tried adding the following 2 lines to .Xinitrc with no effect :-

gtk-window-decorator &
compiz --replace gconf &

Any help would be greatly appreciated.

I am having the same problem, intermittently, with the active window parking itself in the left-hand corner and hiding its border beneath the top panel. I have been getting round it my using the Alt key, which allows you to grab the active window anywhere, to move it. I've not yet found the complete solution

---

