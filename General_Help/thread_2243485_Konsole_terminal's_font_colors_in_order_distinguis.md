---
title: "Konsole terminal's font colors in order distinguish files, subdirectories"
date: 2014-09-09
forum: General Help
---

### Post by Untarnished_Truth on 2014-09-09
Good day.  I'm using Kubuntu 14.04, and I like using the Konsole terminal.  But I would like to improve how I use it.  When I was still using openSUSE, I always had useful text colors in my terminal -- something like displaying subdirectories with blue fonts, and executable binaries with light green, when running 'ls'. In my Konsole terminal in Kubuntu 14.04, I simply get white text, which makes it less easier to identify file types.  How can I turn on this text coloring/highlighting feature in Kubuntu?  Thanks!

---

### Post by Impavidus on 2014-09-09
I don't use KDE, but I assume Konsole supports colour. **ls** has the option **--color**, which turns on coloured output. My .bashrc had by default the line```
    alias ls='ls --color=auto'
```turning this colour on whenever writing terminal output.

---

### Post by Untarnished_Truth on 2014-09-09
> **Impavidus said:**
> I don't use KDE, but I assume Konsole supports colour. **ls** has the option **--color**, which turns on coloured output. My .bashrc had by default the line```
    alias ls='ls --color=auto'
```turning this colour on whenever writing terminal output.

Thanks, this works.

---

