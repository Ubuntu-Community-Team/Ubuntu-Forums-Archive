---
title: "Can someone please explain &quot;inherits&quot; in icon themes?"
date: 2013-06-14
forum: General Help
---

### Post by vasa1 on 2013-06-14
I've read through [http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) and here's a quote from there:
>  The name of the theme that this theme inherits from. If an icon name is not found in the current theme, it is searched for in the inherited theme (and recursively in all the inherited themes).

If no theme is specified implementations are required to add the "hicolor" theme to the inheritance tree. An implementation may optionally add other default themes in between the last specified theme and the hicolor theme. 

I'm using Lubuntu and its icons are in /usr/share/icons/lubuntu. In there, there's a text file called index.theme. The line of relevance is this:
Inherits=elementary

So I look at /usr/share/icons/elementary/index.theme and I see:
Inherits=gnome,hicolor

But when I look in /usr/share/icons/gnome/index.theme, the word "inherits" doesn't figure at all.

Q1: why doesn't gnome's index.theme have hicolor as an "inherit"? According to my understanding of the quote above it should.
Q2: why does a icon theme like lubuntu have inherits other than hicolor? Why not just incorporate the necessary icons and become complete? That way, there would be no need of including the elementary icon theme (and the gnome icon theme).

---

### Post by CatKiller on 2013-06-14
1. It's right there in the spec that you quoted; Inherits=hicolor is implied.

2. There are *lots* of icons and the names change from time to time. Unless a theme is constantly maintained there will end up being icons missing. Filling them in with icons with a similar style is entirely sensible. The nature of an open spec like this is that it encourages building on the work of others to avoid duplicative effort.

---

