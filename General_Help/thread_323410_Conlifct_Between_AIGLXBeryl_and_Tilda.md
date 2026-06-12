---
title: "Conlifct Between AIGLX/Beryl and Tilda?"
date: 2006-12-22
forum: General Help
---

### Post by BetaMaster on 2006-12-22
Hey, I've been using Tilda (great program), and just recently installed AIGLX/Beryl. There seems to be a conflict with Beryl and Tilda. At first, Tilda will work, but then it will stop showing up. The strangest part is that my cursor still changes to a text cursor when I mouse over where the console should be. So it's just invisible.

If I reload the window manager, then Tilda will work again - for two times or so, and then I get the same problem.

I have uninstalled and reinstalled repeatedly, with no change.

Can anyone help me?

Thank you!

---

### Post by ayoli on 2006-12-22
i can confirm that using tilda with beryl is quite problematic. i stopped use it, i now use gnome-terminal which i launch with a beryl keyboard shortcut and a command like that:
```
gnome-terminal --geometry=102x22+322+100 --working-directory=/home/ayoli
```
and i add in gnome-termeinal in beryl state plugin (in window borders) to hide window deco like that:
```
p:gnome-terminal:1
```
or
```
w:gnome-terminal:1
```
so, now i open a transparent term without border with alt+z (my shortcute) and close it with ctrl+d as fast as i used to do with tilda.

---

### Post by qos on 2007-01-03
I found a solution how to use tilda and beryl together.

Original forum thread:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=605472#p605472]("http://forum.ubuntu-fr.org/viewtopic.php?pid=605472#p605472")

Open beryl settings -> Window Management -> Set Window Attribs by Various criteria -> Window Opacity and add the following line:
```
t:tilda:80
```


But there is still the problem that sometimes tilda is invisible.
But just click on the beryl-settings manager and choose another window manager (like metacity).   
Now tilda should be visible again. The confusing thing is that you now can reactivate beryl as window manager and tilda doesn't gets invisible anymore.

I changed some preferences in tilda too, but i think that hasn't something todo with my success.

---

### Post by wormie_dk on 2007-08-08
There is an easy fix for tilda disappearing. Just go to Beryl settings -> general options -> general options and set "Level of Focus Stealing Prevention" to NONE. 

This has worked for me for a long time :-)

---

