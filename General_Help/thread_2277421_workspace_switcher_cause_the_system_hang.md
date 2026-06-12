---
title: "workspace switcher cause the system hang"
date: 2015-05-08
forum: General Help
---

### Post by elim-qiu on 2015-05-08
It's 14.04 with all the official updates.

The problem started yesterday, nothing special, I got 3 pdf files opened and trying to put them in different workspaces along with a terminal used to try out commands/codes from the ebooks. But drag and drop a window from one workspace to the other now cause the system hang (can reproduce that whenever needed).

I'm not sure what's the cause of that, and really like to find a solution.

Thanks for your help.

---

### Post by Doug S on 2015-05-08
I was able to recreate your situation on my system. It is a VM, and it seems to have hung. It is using a lot of CPU resources in this hung state.
Actually it has not completely hung, as I am able to log-in to the computer via ssh. Compiz is using ~260% CPU (The VM has 4 CPUs available).

Edit: Seems similar to [this]("https://bugs.launchpad.net/ubuntu/+source/compiz-plugins-main/+bug/815996") one.

---

### Post by elim-qiu on 2015-05-09
Looks like many application's title right click menu contains options to move the current window to another workspace, and it works. But some popular apps (say, chrome) don't have that feature....

---

### Post by deadflowr on 2015-05-09
> **elim-qiu said:**
> Looks like many application's title right click menu contains options to move the current window to another workspace, and it works. But some popular apps (say, chrome) don't have that feature....

Some do with  alt + rightclick.
Chrome can/should get a right click without alt if the window is maximized, in this case right click on unity's top panel.

I had a dnd from workspace hang only once, but from memory to fix it I used the expo keyboard keybinding super + S and it reset correctly and stopped the hang.
fwiw
It was one time and haven't seen it since.

---

### Post by mc4man on 2015-05-09
Can't generally re-create here (intel graphic) except in one odd occurrence that when trying to grab a window from the deco area got a resize operation instead of a move op.
In that case a freeze ensued, however as resizing should not happen while in expo so can't duplicate that easily..

---

### Post by Doug S on 2015-05-09
> **mc4man said:**
> Can't generally re-create here (intel graphic)Interesting. It seems quite repeatable for me, but only if I do it "just so". I have to have 3 terminals open, one per workspace (fourth workspace empty), and 3 PDF documents open, all in one workspace. Then try to drag one PDF to another workspace.

I tried other variants, with less things open, and it didn't mess up. 

If I leave things long enough (like minutes or even 10s of minutes) the PDF will continue to move, but it never (well, it was maybe only 4 hours that I left it) returns to normal.

---

### Post by mc4man on 2015-05-09
> **Doug S said:**
> Interesting. It seems quite repeatable for me, but only if I do it "just so". I have to have 3 terminals open, one per workspace (fourth workspace empty), and 3 PDF documents open, all in one workspace. Then try to drag one PDF to another workspace.

I tried other variants, with less things open, and it didn't mess up. 

If I leave things long enough (like minutes or even 10s of minutes) the PDF will continue to move, but it never (well, it was maybe only 4 hours that I left it) returns to normal.
With that exact scenario can cause a hang, not all the time or at first but will happen
(carefully changing focus on the pdf's while in expo & then grabbing a window > move out & then back in without dropping into another ws seems a good way here

---

### Post by elim-qiu on 2015-05-27
My laptop is a rather ancient Dell D430 1.33GhzX2, 2GB Ram. Actually drag and drop the 1st document viewer window to another workspace will cause problem. But this is not the case when 14.04 was newly installed. Something wrong with the newer kernel or updates?

---

### Post by Doug S on 2015-12-20
The [bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz-plugins-main/+bug/815996") was set to fix released. But this issue still occurs for me on two different installations (one is a VM and one is an actual HP Laptop) of xenial-desktop-amd64.iso of 2015.12.20.

---

