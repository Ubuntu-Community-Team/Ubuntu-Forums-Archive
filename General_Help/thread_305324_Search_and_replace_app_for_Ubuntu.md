---
title: "Search and replace app for Ubuntu?"
date: 2006-11-23
forum: General Help
---

### Post by Vinze on 2006-11-23
Hey, does anyone know of an application with which I can search and replace words in multiple files?

Thanks in advance.

---

### Post by eeGhoong0ais on 2006-11-23
I can't immediately think of a GUI app that would do it [maybe something like Bluefish, but that seems like overkill]. It's dead easy in a terminal though: ```
for x in file1 file2 file3; do sed -i 's/old/new/g' ${x}; done
``` - where "old" and "new" are replaced by your search word and its replacement.

It's also pretty easy to do something horrible to your files with sed though, so you might want to back things up first.

---

### Post by Vinze on 2006-11-23
> **Etiol said:**
> I can't immediately think of a GUI app that would do it [maybe something like Bluefish, but that seems like overkill]. It's dead easy in a terminal though: ```
for x in file1 file2 file3; do sed -i 's/old/new/g' ${x}; done
``` - where "old" and "new" are replaced by your search word and its replacement.

It's also pretty easy to do something horrible to your files with sed though, so you might want to back things up first.

No worries, I don't mind the command line, I'm just no good at it. However, I wanted to do this recursively, is that possible?

---

### Post by eeGhoong0ais on 2006-11-23
> **Vinze said:**
> I wanted to do this recursively, is that possible?

Anything is possible ;-)

Let's say you wanted to replace "McCormick" with "Stotch" in every file in the directory sp/ and its subdirectories. This would do the trick: ```
find sp/ -type f -print0 | xargs -0 sed -i 's/McCormick/Stotch/g'
```It's definitely worth making sure you know what's going on here, though, so if you're not familiar with find or xargs it'd be a good idea to read up on them a little.

---

### Post by Vinze on 2006-11-23
> **Etiol said:**
> Anything is possible ;-)

Let's say you wanted to replace "McCormick" with "Stotch" in every file in the directory sp/ and its subdirectories. This would do the trick: ```
find sp/ -type f -print0 | xargs -0 sed -i 's/McCormick/Stotch/g'
```It's definitely worth making sure you know what's going on here, though, so if you're not familiar with find or xargs it'd be a good idea to read up on them a little.

Right... I also found rpl, a command line program, which can do it for me. The man page (Section "See Also") says "find" and "sed" so I guess it's a front-end for what you specified. Thanks a lot!

---

### Post by defconoii on 2008-01-24
Here is a decent search & replace tool I found:
[www.ubuntu-unleashed.com/2007/09/howto-search-and-replace-text-in-files.html](www.ubuntu-unleashed.com/2007/09/howto-search-and-replace-text-in-files.html)

---

