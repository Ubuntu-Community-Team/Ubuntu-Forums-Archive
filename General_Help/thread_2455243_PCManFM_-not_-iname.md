---
title: "PCManFM -not -iname"
date: 2020-12-15
forum: General Help
---

### Post by Kevin McCready on 2020-12-15
I want to use the filemanager PCManFM to list all files except those with a specified extension,

How can I do this? ie it's like using 
ls -I "*.txt"

---

### Post by GhX6GZMB on 2020-12-15
I'm not certain what you mean. UNIX/Linux files don't have extensions. Just names.

---

### Post by guiverc on 2020-12-16
I had a quick play with `pcmanfm-qt` (*I'm on a modern Lubuntu*) and could get it to filter and show files that match a provided filter, but didn't work out how to exclude.

[https://manual.lubuntu.me/stable/2/2.4/2.4.4/pcmanfm-qt.html](https://manual.lubuntu.me/stable/2/2.4/2.4.4/pcmanfm-qt.html)

I also loaded `thunar` (XFCE's File Manager) and could select all that match a pattern, then invert the selection to get equivalent of the "exclude|not", but it's still not what you're after (as it was still showing all, just had selected using the pattern).

---

### Post by Kevin McCready on 2020-12-20
Thanks for trying. I'll have to do it manually. [**[COLOR=#000000]ml9104[/COLOR]**]("https://ubuntuforums.org/member.php?u=2127041") you can give file name extensions if you like in Linux. I usually do so because it helps me know what's what and I can filter via the extensions.

---

