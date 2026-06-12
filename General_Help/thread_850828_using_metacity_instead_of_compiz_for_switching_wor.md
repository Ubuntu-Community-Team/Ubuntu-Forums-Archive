---
title: "using metacity instead of compiz for switching workspaces"
date: 2008-07-06
forum: General Help
---

### Post by magicmanfk on 2008-07-06
Hey, I've been using (and loving) compiz, but noticed that freewins and any sort of workspace switching (desktop cube, desktop wall, etc), don't get along together, and whenever you try to switch workspaces the framerate will significantly drop (5-10fps). I think that if there is a way I can have metacity do workspace switching but nothing else, this could let me still use freewins without sacrificing fps and multiple workspaces. Anyone know if this is possible?

PS- I could have sworn I just made this topic but couldn't find it anywhere, so I'm making it again. If it is somewhere else, my bad :)

~Franklin

---

### Post by sdennie on 2008-07-06
I don't know what freewins is but, I can say for certain that it's not possible to have metacity handle specific operations while running compiz.  Are you sure the problem you are seeing is related to plugins and not drivers?  What video card and driver are you using?  Is it by chance an nvidia card with a laptop?  If so, see: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

---

### Post by sayakb on 2008-07-06
You cannot have freewins with metacity. Metacity doesnot have compositing and you need a composite desktop in order to get desktop effects/animations working.

---

### Post by magicmanfk on 2008-07-06
thanks guys, I'm actually using a ATI x1300 mobility graphics card, and both work fine when running separately, and it's just when both are running together that the system goes kaputz. That kind of rules out a graphics card issue, doesn't it? 

I guess I was kind of hoping it is like window borders where you can have metacity or emerald do it just by running a command to switch between them, but I suppose it makes sense that it works completely different.

---

