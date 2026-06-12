---
title: "Torsmo fonts"
date: 2005-05-11
forum: General Help
---

### Post by tread on 2005-05-11
I feel really stupid asking this  :) 

I cannot get the font size to change, I have tried changing it in the .torsmorc file in my home directory. I even ran xfontsel, chose a font, and pasted it in.

My current config file has:
```

# X font used, you can pick one with program xfontsel
font 5x7
#font 6x10
#font 7x13
#font 8x13

```
Edited to add: I am trying to reduce the font size, but even it I say 5x7 I get the same font as I get with 7x13.

Does anyone have any hints/sample config files I could leech off?
Thanks!

---

### Post by jrobcet on 2005-05-11
Here is a sample config file:
[http://www.dotfiles.com/files/18/424_.torsmorc](http://www.dotfiles.com/files/18/424_.torsmorc)

It looks almost the same as my config file and I can easily change font sizes by commenting and uncommenting the appropriate lines. 

Perhaps your problem is related to Xft? I'm not entirely certain, but it appears those font options may only be available when Xft is disabled.

---

### Post by tread on 2005-05-12
Thanks! I knew I was gonna look stupid :) It turns out I was working from an older sample.torsmorc .. that didn't have any xft stuff mentioned. I just added xft settings and its working like a charm now.

---

### Post by jrobcet on 2005-05-12
Glad to hear you got it sorted  :)

---

### Post by Loco_gr on 2006-03-05
I am working in Fluxbox and i am using torsmo. The problem is that I use Greek locale "el_GR" and when I try to appear the date in torsmo then I read only unrecognised characters. I tried to change the fonts but with no luck. 

Of course when I changed the locale to "en_US" then I was able to read the date. But I need the greek locale, so any ideas?

Thanks in advance

---

### Post by Loco_gr on 2006-03-06
I found a solution !!
I start torsmo like with en_US locale like this:
```

env LANG=en_US torsmo

```

---

