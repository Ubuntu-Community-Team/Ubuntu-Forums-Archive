---
title: "beryl update: cant &quot;drag&quot; windows out of maximised mode"
date: 2007-02-02
forum: General Help
---

### Post by Choad on 2007-02-02
one of the truly awesome touches in linux, and specifically beryl (for the way it renders the action) is the ability to drag a window out of being maximised. i love it. the lates beryl update appears to have disabled this somehow.

anyone know how i can get it back?

---

### Post by r0pe on 2007-02-02
I noticed this too, does anyone know how to fix it?

---

### Post by Choad on 2007-02-02
> **r0pe said:**
> I noticed this too, does anyone know how to fix it?
glad im not alone :)

---

### Post by Choad on 2007-02-03
buuuuump

---

### Post by LinuxforHumans on 2007-02-03
I had a similar problem, whenever my windows are maximized the window decorations disappear and turns completely white...any reason why that happens?

---

### Post by redsp1der on 2007-02-03
I've been having problems with the last Beryl update too.
Everything was running smoothly but now the water effect is broken. Whenever I move a window or anything that causes waves the whole screen flickers or switches between very dim almost black screen and normal.

is there any way to roll back that last beryl update?

---

### Post by Choad on 2007-02-03
i dont wanna roll back. this update has made things so much faster! dont get frame drops at all any more. just the dragging out of maximised that is an issue. i suppose it'll only be a few weeks till a new update is rolled out. hopefully it will be fixed then

---

### Post by kilou on 2007-02-04
You must go in the Move plugin and select Snapoff/Snapback. See [http://forum.beryl-project.org/viewtopic.php?f=36&t=3092](http://forum.beryl-project.org/viewtopic.php?f=36&t=3092)

However I have tried to uninstall/reinstall beryl but I can't get this option for some reason. If any one can help how to get this Snapoff/snapback option in the Move plugin??

---

### Post by Choad on 2007-02-04
thanks. unfortuantely i have the same problem as the guy in that forum: i dont have that option. i already looked here actually, trying to find something. all to no avail :(

---

### Post by Nikron on 2007-02-04
> **redsp1der said:**
> I've been having problems with the last Beryl update too.
Everything was running smoothly but now the water effect is broken. Whenever I move a window or anything that causes waves the whole screen flickers or switches between very dim almost black screen and normal.

is there any way to roll back that last beryl update?

I had this too, except I realized I really didn't like the water effects anyway, so I turned them off =P   I also can no longer drag around maximized windows and don't have the option to enable it...  I'll report back if I fix it..

---

### Post by kilou on 2007-02-05
SOLVED: you have to use different repositories to get the Snapoff option in the Move plugin. Look here 

[http://forum.beryl-project.org/viewtopic.php?f=36&t=3092&p=18852#p18852](http://forum.beryl-project.org/viewtopic.php?f=36&t=3092&p=18852#p18852)

and add the 2 repositories in your source list (remove the old one for beryl) and update beryl. Then go in the Move plugin and enable Snapoff.

---

### Post by Choad on 2007-02-05
thanks! perfect.

---

### Post by kilou on 2007-02-05
After having the snapoff feature working I got another problem: the border of some window would become white after snapping them off. I think this is due to the "Widget layer" plugin that is enabled by default in the Desktop category. After disabling it the snapping oof feature seems to work correctly. You might want to try this out if you get the same issue with white borders.

---

### Post by Choad on 2007-02-05
yeh this version of beryl runs slow on my laptop

get frame drops all the time pretty much. quite disapointing, because the one before (where snapoff didnt work) was very VERY fast. much more so than any other beryl i had tried. so gutted that the speed is gone. i would have prefered the speed over snapoff

(oh and i got the white borders thing too once)

---

