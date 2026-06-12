---
title: "how to change window border widths??"
date: 2007-05-11
forum: General Help
---

### Post by fuzz500 on 2007-05-11
Hello All,
I've got a nice dual monitor setup running feisty at 3200 px wide, and I find the borders on metacity windows are very very tiny and hard to grab if I want to do a window resize... I've been searching everywhere to find out how to increase the window border width. This must be a very well kept secret!!

Any suggestions? How do you specify your window border width??

regards,
Fuzz

---

### Post by heimo on 2007-05-11
I don't know how to do it, but this may be a work-around: Window borders are "themed", so you can go to System->Preferences->Theme, choose customize, choose Window Border tab and try other borders. Some of those are thicker. If non of those works for you, you could try searching for more at 
[http://art.gnome.org/themes/metacity/](http://art.gnome.org/themes/metacity/)

---

### Post by fuzz500 on 2007-05-11
thx. It's a pretty good workaround. I tried "Hacked"... nice pretty much what I was using plus the borders are a bit easier to grab. I'm still curious to see how to tweak a theme yourself.

---

### Post by heimo on 2007-05-11
Here's how to do it... Let's assume you use clearlooks theme. Edit:
/usr/share/themes/Clearlooks/metacity/metacity-theme-1.xml

You probably need to at least edit these:

```
<distance name="left_width" value="5"/>
<distance name="right_width" value="5"/>
<distance name="bottom_height" value="5"/>

```

Change 5 to some higher value. Change to some other theme and then back to the clearlooks to reload theme. See this tutorial for more instructions:
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

---

