---
title: "Font Configuring"
date: 2008-04-22
forum: General Help
---

### Post by Exsecrabilus on 2008-04-22
In Gutsy, to add fonts, you only had to do two things:

1. Copy .ttf files and paste them into the *fonts:///* directory.
2. Open up Terminal, type *fc-cache -f -v* and press *Enter*.

It was simple.

But now, in Hardy 8.04 RC amd64, I'm confused what to do.
When I type in fonts:/// into the location entry, it says *Nautilus cannot handle fonts: locations.*.

What's gong on here?
How do I add fonts?

---

### Post by Jammy4041 on 2008-04-22
In Hardy (on an x86 Machine at least) the fonts are located at /usr/share/fonts. The fonts you probably want to add will likely to be true type, so click the truetype folder, and add your font.

---

### Post by Exsecrabilus on 2008-04-22
Do I do the fc-cache -f -v thing after I paste the .tff files in?

And which subfolders do I paste it into? Do I just make a new folder?

---

### Post by peterdk on 2008-04-26
As long as it is somewhere in /usr/share/fonts, fc-cache -fv will find it. The map names are more for human overview.

---

