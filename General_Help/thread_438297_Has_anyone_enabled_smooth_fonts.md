---
title: "Has anyone enabled smooth fonts?"
date: 2007-05-09
forum: General Help
---

### Post by crimesaucer on 2007-05-09
Hello, I enabled smooth fonts many months ago from the edgy wiki page.

Well, my fonts are beautiful, but I get this same Line 1 error about my Fontconfig. 

```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed


```

I researched the XML declaration not being well-formed, and I couldn't understand what to do to fix the problem so I gave up. 

That was a few months ago...so, before I start Google searching again, does anybody know the easy answer, or the quick way to fix Line 1 of this code from the wiki page: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts)

```
<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>
``` 

I am just tired of seeing that error every time I do something in terminal.

---

### Post by crimesaucer on 2007-05-10
bump.

---

### Post by qpwoeiruty on 2007-05-10
Your quotation marks are just messed up. Replacing the marks with normal quotation marks solves the problem (it validates with xmlwf).

```
<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

---

### Post by crimesaucer on 2007-05-10
Thank you, I guess they were written funny on the wiki page and I didn't notice.

Thanks again.

EDIT--Whoa, that's nice. I had no idea that my mousepad could look so nice. I had thought that the combo of that script and my User Interface Preferences of sub-pixel hinting, hinting, and anti-aliasing font settings had made my web fonts really nice, but now my mousepad is beautiful too. I didn't know that was for that.

Thank you very much.

---

