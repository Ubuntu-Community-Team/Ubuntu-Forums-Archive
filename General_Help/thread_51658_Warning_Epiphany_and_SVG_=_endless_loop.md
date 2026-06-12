---
title: "Warning: Epiphany and SVG = endless loop"
date: 2005-07-24
forum: General Help
---

### Post by stoffe on 2005-07-24
Not sure if this is the correct place to post this, but I thought I should warn others about this, as it can be a painful surprise. :)

I was looking at this page: [http://www.sodipodi.com/index.php3?section=clipart/flags](http://www.sodipodi.com/index.php3?section=clipart/flags) which is a lot of flags in SVG format. I tried clicking on one (in firefox), and it asked me as is its custom what I wanted to do with it. I saw that Epiphany was listed as the default action to take, so I figured I'd try that - who knows, maybe Epiphany supports SVG? I've heard that Mozilla based browsers are working on this, but no real idea about the state of things. Well, it doesn't. :)

Epiphany started and immideately went into an endless loop where it opened a new Epiphany window automatically over and over again - because it encountered SVG, which is handled to the default action in Ubuntu... which happened to be Epiphany. It also filled my Desktop with that same file over and over again (44 copies before I was able to do **pkill epiphany**).

Firefox would do the same if it was set to automatically invoke default action btw, but it isn't.

The biggest reason I have for writing this down, and especially doing it here instead of in a bug tracker somewhere is simply that when installing Epiphany, it or Ubuntu apparently sets this to the default action to take for SVG, and the default setting (if there is any other) in Epiphany is to **not** ask before invoking. So it might be specific to how it is handled in Ubuntu. If not, maybe someone can report this to the proper places or at least point me there.

Just a heads up, so others don't do the same. :) If you do, go to a terminal (CTRL-ALT-F1 or similar) and kill Epiphany from there. Managing that in Gnome is not a fun task since every new window steals the focus. Though it can be done. I realized that I should have switched to terminal afterwards...  :roll:

---

### Post by Xian on 2005-07-24
That is very odd. I use Opera and it just opened the svg image in a browser window.

---

### Post by stoffe on 2005-07-25
[QUOTE=Xian]That is very odd. I use Opera and it just opened the svg image in a browser window.[/QUOTE]
 Not odd at all - Opera can view SVG, while these others can't (yet): [http://www.opera.com/features/svg/](http://www.opera.com/features/svg/) - I specifically stated that this was for Epiphany, and for this special case with default action to take.

It really hasn't much to do with SVG as such, it has to do with a program that is listed as the default action for a format it can't view, and that simply invokes the default action for that format without asking first, which leads to the loop. This could happen for just about any filetype.

---

