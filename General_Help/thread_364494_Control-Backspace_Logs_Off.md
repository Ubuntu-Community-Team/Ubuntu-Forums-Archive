---
title: "Control-Backspace Logs Off"
date: 2007-02-18
forum: General Help
---

### Post by jengerer on 2007-02-18
**Edit: I solved it. Solution is on the bottom for anyone else experiencing this.**

Hello, everyone.

I've been using Ubuntu for a couple of days now, and I think I'm getting the main hang of things.  However, there is one problem that's getting kind of annoying.

Whenever I press Control-Backspace, the screen turns black, and then it shows the logon screen.

Then if I put in my credentials, it starts to load everything, but after it finishes that, it doesn't show anything else.

Has anyone else had this problem? Is anyone daring enough to try this combination? :) 

It's not really urgent, but if someone can tell me what exactly this combination does and if there are any workarounds.

I checked Google, but there wasn't any luck.

Thanks,

Jengerer

**Solution: Open up your terminal and type in: xmodmap -e &#8220;keycode 22 = BackSpace BackSpace&#8221; **

---

