---
title: "Undo apt-get upgrades"
date: 2007-03-06
forum: General Help
---

### Post by spacebetween on 2007-03-06
Nevermind this post. I figured it out. If anyone else is dumb like me, all I did was delete all the npwrapper.libflashplayer.so files, then reinstalled the file in the home mozilla/plugins directory using nspluginwrapper (per the guide found on the forums). 
--------------------------------------

Today I had some new files to upgrade through upgrade manager, so I figured there'd be no problem in that.

Except now when I open a website in Firefox with Flash, Firefox greys out and freezes. And, it will also just randomly freeze even when I'm not on a page with Flash.

I use nspluginwrapper to run Flash, and it worked fine before. There was an upgrade in update manager for nspluginwrapper, and I'm convinced that is the problem.

How do I downgrade or undo a previous update??

---

