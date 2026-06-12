---
title: "Some fonts are broken, please help."
date: 2013-01-07
forum: General Help
---

### Post by e64462 on 2013-01-07
I've tracked a bug I'm experiencing in conky to an old font that has historically worked quite well. Here is the link:

[http://www.fontspace.com/curtis-clark/pie-charts-for-maps](http://www.fontspace.com/curtis-clark/pie-charts-for-maps)

After being installed on my system, only one character is ever displayed (regardless of which is called)--an empty (unfilled) pie chart. This is indeed one of the characters in the font package, but it's certainly not the only one (or it's not supposed to be at least). 

Perhaps the strange part is that some applications render the fonts correctly, while others do not. For example Kubuntu's "Font Management" fails to display previews, and when I attempt to print the fonts, it again shows only empty circles where pie charts should be; while LibreOffice displays the fonts just fine using the keys a-z.

How can I get this font displaying properly again, or is there an alternative which would be easily implemented in a conky script? 

Steps to reproduce on my end:
```
unzip curtis-clark_pie-charts-for-maps.zip
cp PIE4MAP.TTF ~/.fonts
fc-cache -f -v

```

Your help and advice is appreciated.

---

### Post by e64462 on 2013-01-08
bump

---

### Post by e64462 on 2013-01-10
uhh... bump, please?

---

### Post by stinkeye on 2013-01-11
Have the same problem with downloaded fonts I use in conky in  ubuntu 12.10.
Yet to find an answer.
Seems to me some settings change has been made to accommodate libre office fonts.

---

### Post by stinkeye on 2013-01-16
Found a fix [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12459119&postcount=16") using fontforge.
Follow the instructions using the attached pics in the link.
or
try this one I have already re-encoded.

---

### Post by e64462 on 2013-01-18
Excellent, thank you so much. I'll give this a try and post back with the results.

edit: worked like a charm. Thanks again, marking this as solved.

---

