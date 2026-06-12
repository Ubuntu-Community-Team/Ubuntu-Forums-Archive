---
title: "How to configure the font rendering?"
date: 2008-06-06
forum: General Help
---

### Post by DjDarkman on 2008-06-06
A few days ago there was a strange kernel update, where I was asked many things, I was asked never before, but a good side effect was that I could change the font rendering from the default debian for a nicer one, and I also had an option to make the text look better on my lcd screen.

How can I do this again? I have another LCD screen and I want to cofigure it the same way because I like how the font is rendered now.

---

### Post by colo on 2008-06-06
The kernel has nothing at all to do with font rendering under X11.

You might want to take a look into ~/.fonts.conf for configuring Hinting, AA, and all that fancy freetype stuff.

---

### Post by DjDarkman on 2008-06-06
> **colo said:**
> The kernel has nothing at all to do with font rendering under X11.

You might want to take a look into ~/.fonts.conf for configuring Hinting, AA, and all that fancy freetype stuff.

I didn`t mean the kernel had something to do with it, I meant that the update, which was very verbose, I think maybe the devs put the wrong package out the repositories, because it didn`t happen again.

Isn`t there a graphic tool for this?

---

