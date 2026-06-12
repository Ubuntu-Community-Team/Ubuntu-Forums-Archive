---
title: "Problems with Unicode in Ubuntu font"
date: 2015-01-12
forum: General Help
---

### Post by jeffbarish on 2015-01-12
The Ubuntu font seems to map many unicode characters to other unicode characters.  For example, Latin Capital Letter A With Tilde (U+00C3) appears as Latin Capital Letter A With Macron (U+0100).  This error occurs for Ubuntu 11 regular, but not for Ubuntu 36 regular.  Even at [http://font.ubuntu.com/](http://font.ubuntu.com/), which doesn't let me choose size 11, I find that at size 16 small a with tilde (U+00E3) appears as small a with macron (U+0101), although the capital A versions work correctly at this size.  At size 36 they both work correctly.  I find that Liberation Sans does not have this problem, but I like the Ubuntu font better.  Is there anything I can do to fix this problem, or do I have to use Liberation Sans?

---

### Post by Impavidus on 2015-01-12
Must have to do with font hinting and anti-aliasing. When the deviation of the tilde from a straight line gets smaller than 1 pixel, it's drawn as a straight line. When printed on paper it should still be a tilde, as on paper we have higher resolution than on screen. In Liberation Sans the tilde has a higher amplitude than in the Ubuntu font, when compared to size of the font. So, the tilde will retain a visible wave at smaller font size.

Also note the clearly exaggerated amplitude of the tilde in Liberation Sans 20. This is a rounding error in the opposite direction.

---

