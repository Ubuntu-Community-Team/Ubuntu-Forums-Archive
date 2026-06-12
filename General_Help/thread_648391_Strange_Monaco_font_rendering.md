---
title: "Strange Monaco font rendering"
date: 2007-12-23
forum: General Help
---

### Post by bidigo on 2007-12-23
Hi folks,

I've been battling this problem for I don't know how long and I'm still at square one.

I have Ubuntu Gutsy and I want to use Monaco 9pt antialiased in gvim. I got the font from [[COLOR="Blue"]this site[/COLOR]]("http://www.gringod.com/2006/11/01/new-version-of-monaco-font/").  It's all fine and I can configure it in .vimrc, the only problem is that at that size (9 points) the font is rendered as aliased. In fact, if I supply any other size than 7 or 9 the font is rendered antialised, only at those two sizes it's not.

What's even stranger is that this strange rendering seems not to affect terminals (both gnome-terminal and xterm) at all. There Monaco 9pt is rendered correctly antialiased.
Firefox renders the font similarly to gvim, that is aliased at certain sizes.

I tried messing with ~/.fonts.conf and tried all sorts of tests and patterns, but to no avail.

Has anyone seen this kind of behavior?

Attached are the two screenshots of Monaco 9pt rendered in terminal and in gvim.

Thanks!

---

