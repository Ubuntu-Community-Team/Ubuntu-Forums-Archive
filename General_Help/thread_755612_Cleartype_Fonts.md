---
title: "Cleartype Fonts?"
date: 2008-04-15
forum: General Help
---

### Post by riskbreaker927 on 2008-04-15
I think I posted this in the wrong forum, so I'm trying it again here.

I used the following howto:

[http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/](http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/)

to get the cleartype fonts installed. They now show up in font lists, however, when they are selected, they render as nothing but empty white boxes. Is this an intentional block set up by the Ubuntu developers, or have I made a mistake?

---

### Post by jespdj on 2008-04-15
It is certainly not an "intentional block by Ubuntu developers". Ubuntu is a free and open source operating system, and it does not contain stupid things like this to make it impossible to use one thing or another.

Are the fonts correctly installed? Do you have a hidden .fonts directory in your home directory that contains the TTF files?

If you have a working Windows Vista installation, you could just copy the TTF files (which should be somewhere in C:\Windows\Fonts or someplace like that) to the .fonts directory in your home folder.

---

### Post by riskbreaker927 on 2008-04-15
Solved, I think. The problem seems to be that I ran the script as root and so root owned the files and I couldn't use them as not-root.

However, the fonts don't look that good. Seems to be a problem with lack of hinting maybe?

---

