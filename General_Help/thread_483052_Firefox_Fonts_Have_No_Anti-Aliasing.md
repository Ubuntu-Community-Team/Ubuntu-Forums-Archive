---
title: "Firefox Fonts Have No Anti-Aliasing"
date: 2007-06-24
forum: General Help
---

### Post by CompactDestruction on 2007-06-24
Hello, I'm quite new. I've enabled sub-pixel rendering but it appears Firefox has no anti-aliasing on its fonts at all, which is quite ugly on an LCD ;) I can't help thinking there's a simple setting I've missed somewhere! All other apps have smooth fonts.

---

### Post by reclusivemonkey on 2007-06-24
Open a new tab in firefox. Type in "about:config" (without the quotes of course) and hit enter. In the filter box at the top, type in "anti" (again without the quotes) and either post back what it says or take a screenshot and attach it.

---

### Post by CompactDestruction on 2007-06-24
font.antialias.min - default - integer - 10

---

### Post by reclusivemonkey on 2007-06-24
What fonts/sizes have you chosen?

---

### Post by CompactDestruction on 2007-06-24
Proportional- serif
Serif- Bitstream Vera Sans
Sans-Serif- Bitstream Vera Sans
Monospace- Bitstream Vera Sans mono

All size twelve.
Pages may choose their own fonts.

---

### Post by reclusivemonkey on 2007-06-24
Is it every site you go to? Can you take a screenshot?

---

### Post by CompactDestruction on 2007-06-24
Yes as far as I can tell

[IMG]http://img231.imageshack.us/img231/4201/screenshotli4.png[/IMG]

---

### Post by reclusivemonkey on 2007-06-24
Try unticking "Allow pages to choose their own fonts", or you can try to install msttcorefonts; a lot of websites use these;

```

sudo aptitude install msttcorefonts

```

---

### Post by CompactDestruction on 2007-06-24
Forcing Firefox to use my specific fonts seems to help readability a lot thanks. Although it still looks quite different.

---

