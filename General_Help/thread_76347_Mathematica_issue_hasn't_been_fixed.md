---
title: "Mathematica issue hasn't been fixed"
date: 2005-10-15
forum: General Help
---

### Post by Hikaru79 on 2005-10-15
There's been a bug report for this ever since the new wnck-applet was introduced into Breezy, and it still hasn't been fixed :(

Basically, when you launch Mathematica 5.0 or 5.1, wnck-applet crashes, freezing your gnome-panel. Restarting it works, but this still shouldn't really be happening. A bug report has been filed, but nothing's been done about it. Does anybody have a workaround or idea or a patched libwnck ? Thanks :)

---

### Post by Pausanias on 2005-10-15
Same experience with 4.x as well.

---

### Post by parktownprawn on 2005-10-15
Hi 
I just noticed that prelinking seems to cure this problem :) - 

I'm running Mathematica 5.1 on Breezy. After following [these]("http://www.ubuntuforums.org/showthread.php?t=74197") instructions on prelinking ubuntu, as a added bonus I found the wnck problem seems to have disappeared.

I hope this will work for others.

---

### Post by Hikaru79 on 2005-10-15
[QUOTE=parktownprawn]Hi 
I just noticed that prelinking seems to cure this problem :) - 

I'm running Mathematica 5.1 on Breezy. After following [these]("http://www.ubuntuforums.org/showthread.php?t=74197") instructions on prelinking ubuntu, as a added bonus I found the wnck problem seems to have disappeared.

I hope this will work for others.[/QUOTE]

Hm. I have prelinked libraries too, but the problem still exists :( Do you think perhaps it was something else you did? I'm really excited by the fact that this seems to be fixable for you :D

---

### Post by parktownprawn on 2005-10-15
I'm pretty sure its the prelinking that fixed the problem. I don't recall doing anything other than prelinking after which the problem seems to have disappeared. It's a pity if this doesn't work for you :(.

---

### Post by parktownprawn on 2005-10-15
Further playing around reveals that prelinking only seems to be a partial work around. 

I wasn't running the window-list applet just the work-space switcher.
After prelinking the workspace switcher seems to stop crashing with Mathematica but the window list applet still crashes with mathematica.

---

### Post by Hikaru79 on 2005-10-15
[QUOTE=parktownprawn]Further playing around reveals that prelinking only seems to be a partial work around. 

I wasn't running the window-list applet just the work-space switcher.
After prelinking the workspace switcher seems to stop crashing with Mathematica but the window list applet still crashes with mathematica.[/QUOTE]
Ah, I see. Well, at least now we have some more detailed information to give to the bugtracker. Thanks, park :)

---

### Post by parktownprawn on 2005-10-25
seems like running mathematica with the no splash screen option ```
mathematica -noSplashScreen
``` solves the problem for me (finally) - sombody posted this on the wiki - hope it works for you

---

### Post by Hikaru79 on 2005-10-25
[QUOTE=parktownprawn]seems like running mathematica with the no splash screen option ```
mathematica -noSplashScreen
``` solves the problem for me (finally) - sombody posted this on the wiki - hope it works for you[/QUOTE]

Genius! I love you, thanks :)

---

### Post by yioan on 2005-12-06
[QUOTE=parktownprawn]Further playing around reveals that prelinking only seems to be a partial work around. 

I wasn't running the window-list applet just the work-space switcher.
After prelinking the workspace switcher seems to stop crashing with Mathematica but the window list applet still crashes with mathematica.[/QUOTE]

-noSplashScreen fixes windows list freezing...

but if you try for example to edit your preferences in mathematica, it crashes

but 
someone posted a solution here
[http://www.ubuntuforums.org/showthread.php?t=89899](http://www.ubuntuforums.org/showthread.php?t=89899)
:)

---

### Post by goonface on 2006-01-11
Yes thanks parktownprawn your -noSplashScreen fix works for me too.  Would never  have thought of trying that it's definitely a strange bug.

I've just put an alias mathematica="mathematica -noSplashScreen" into
my ~/.bash_aliases

thanks

---

