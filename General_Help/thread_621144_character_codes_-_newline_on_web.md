---
title: "character codes - newline on web"
date: 2007-11-23
forum: General Help
---

### Post by caughran on 2007-11-23
Some scripts on the index page of my Quaker web site, [www.quaker.ca/toronto](www.quaker.ca/toronto), didn't work. I checked the source, ctrl+U in Firefox, and found the entire page was a single line. 

Downloading the file and comparing it, it showed no differences. Gedit showed the same file as what I would expect, but vim (cream) showed a rather different file, with the lines on gedit ending ^m, but with vim continuing without a line break. Back in the far reaches of my brain, I remembered that ^m was a newline for some character set.

Both the version on my computer and the version on the web were wrong.

I tried a change by selecting source ^m in vim, and pasting copied newline. It changed ^m to ^@, but otherwise looked the same. (How does one use newline in a vim replace?)

Tried the same in gedit, with \n as the new character, and it worked. At least, now vim displays the file correctly and when uploaded, the scripts work.

So I've fixed it, but I don't understand what the problem was, or what the fix was. Can someone enlighten me? 

Thanks.

---

### Post by taurus on 2007-11-23
If you want to stripe the ^m at the end of the lines, just run

```
dos2unix filename
```

---

