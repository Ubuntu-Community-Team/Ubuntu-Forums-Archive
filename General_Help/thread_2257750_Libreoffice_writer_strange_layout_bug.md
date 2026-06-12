---
title: "Libreoffice writer strange layout bug"
date: 2014-12-22
forum: General Help
---

### Post by kuckunniwi on 2014-12-22
Hi,

I'm writing because I'm encountering an odd problem I'd never had before. I'm running libreoffice writer 4.2.7.2 build 2 with the default installation that came with my Kubuntu 14.04. The layout is completely off, both in new documents and opened documents: One page is in portrait, as is should be, while the next one is in landscape with two columns and the following in portrait again.

Here's what it looks like:

[[img]http://s18.postimg.org/6p8oorjs5/libreoffice_layout.jpg[/img]](http://postimg.org/image/6p8oorjs5/)

I'd never encountered anything quite like this before, so I'm not sure how to address it. I've googled the issue, but for *layout problems*[I], all the hits I'm getting are for MS Word compatibility issues, nothing like this. 

Any help would be greatly appreciated :)

---

### Post by kuckunniwi on 2014-12-22
Looks like I was able to find a solution myself. Cottfcfan's suggestion (in [this]("http://ubuntuforums.org/showthread.php?t=2041329&p=12166964#post12166964") thread) of deleting the /Home/.config/libreoffice folder worked like a charm. Will mark as solved.

---

### Post by mcduck on 2014-12-22
That wasn't a layout issue, you actually had 4 pages, all portrait, but you had Libre Office set to book preview mode. (small page icons in bottom right corner, next to the zoom slider). Book preview mode removes border between pages that would appear side-by-side when printed on dual-sided pages, like you'd have on a book.

---

### Post by kuckunniwi on 2014-12-24
Thanks a ton! One learns new things every day...cheers!

---

