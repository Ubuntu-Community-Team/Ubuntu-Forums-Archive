---
title: "DEL, HOME and END key in gnuplot"
date: 2005-08-03
forum: General Help
---

### Post by ikletti on 2005-08-03
Hi.

I recently started using gnuplot a lot. So far, my DEL, HOME and END key are
working fine in every application (*including* terminal applications like mc, vim, etc.)
*except* with gnuplot running in a terminal window.

There, pressing one of those keys just creates some weird output like "~3" or "OF". 
I've searched a little, but could only find solutions to non-working backspace keys
(which by the way does exactly what it's supposed to do, even in gnuplot).

Since I only started using gnuplot with my current Ubuntu Hoary installation,
I don't know if this behavior happens elsewhere.

Does somebody have an idea about this or knows where to look further?

Ingo.

---

### Post by lev.landau on 2008-05-30
Hi Ingo,

this problem is solved here
[http://ubuntuforums.org/archive/index.php/t-102524.html](http://ubuntuforums.org/archive/index.php/t-102524.html)

As far as I understand, it's caused by not using GNU Readline library when compiling the Ubuntu .deb package 

Matous

---

