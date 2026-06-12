---
title: "reverse-i-search - Ctrl-R doesn't seem to work"
date: 2013-06-09
forum: General Help
---

### Post by noah++ on 2013-06-09
Hi,

I am trying reverse-i-search in Bash for the first time. Several sources I read say that I can just enter some of a command at the prompt and press Ctrl-R to retrieve a matching history item. Here's how my session goes, though.

```
$ grep cheddar cheesemenu.txt<CR/LF>
$ grep<^R>
(reverse-i-search)`': grep<^R><^R>...
```
I expect it to show me it found[FONT=courier new] grep cheddar cheesemenu.txt[/FONT]. Instead, the terminal bell sounds, and no such result appears. I can up-arrow in my command history to that command, so I know it's not that I don't have a history file.

Any ideas?

---

### Post by noah++ on 2013-06-11
Ping. Anyone know what I'm doing wrong? It seems incredible that something so basic can be a bug and not my fault.

---

