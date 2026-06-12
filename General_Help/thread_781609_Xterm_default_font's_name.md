---
title: "Xterm default font's name?"
date: 2008-05-04
forum: General Help
---

### Post by tmskraus on 2008-05-04
I really like the default font in xterm and I want to use it in gnome-terminal. How do I do this? I can't seem to find it using the normal font selection screen.

Thanks.

---

### Post by cdleary on 2008-06-09
I'm not sure what the exact answer is, but I use "terminus" which comes close. Run the following to get the font and refresh the font cache:

```

sudo apt-get install xfonts-terminus && sudo fc-cache

```

After running the above command some running GTK applications may need to be restarted before you see the font as available (I think gnome-terminal caches its font widget, so you might have to close it and open a new instance).

---

### Post by qns8dn3 on 2008-11-18
I want to change gnome-terminal's font to xterm's one, too.

On my Ubuntu, the default xterm font is small and not anti-aliased, while the default gnome terminal font and gedit font is anti-aliased. I attached my screenshot of xterm and gnome-terminal.

My gut tells me that the xterm font is indeed one of those fonts listed in the normal font selection it's just that xterm refuses to anti-alias fonts.

We have to configure gnome-terminal not to anti-alias fonts, at least for small fonts, in order to have that nice xterm font in gnome-terminal. But I don't know how to achieve that.

Does anyone know how to turn off anti-alias for small fonts?

---

