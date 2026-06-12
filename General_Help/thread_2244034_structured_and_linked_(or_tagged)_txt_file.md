---
title: "structured and linked (or tagged) txt file"
date: 2014-09-13
forum: General Help
---

### Post by evaristegalois on 2014-09-13
I like mindmaps and have a lot of emacs org files organizing information. The idea, for those who don't know org-mode, is that you have information like this sitting in a text file:

* house
** kitchen
** living room
** basement
*** table tennis room
*** laundry room
*** wood shop
** bedroom A
** bedroom B
* garage
* lawn

and so on. There are nodes and levels. Some of my org files are quite large, and I want to think about breaking them up into smaller files and reading them with vi rather than emacs (large org files are a challenge to read with vi). There would be one file called house.txt, for example, which has a list of the rooms in the house, but each list item has its own file corresponding to it and when I go to that file I get the list items which are on the next level. HTML pretty much does just that, but I want as little markup as possible and I want to do the jumping around between files in vi (or emacs), not in a browser. ctags seems to do something like this (e.g. in the vi or emacs help files), but I can't figure out how to write files for ctags, as ctags only processes known coding languages, and no coding language seems to want to do what I want to do. Any suggestions?

---

### Post by evaristegalois on 2014-09-13
[http://vim.1045645.n5.nabble.com/making-your-own-tagfile-td1191896.html](http://vim.1045645.n5.nabble.com/making-your-own-tagfile-td1191896.html)

---

