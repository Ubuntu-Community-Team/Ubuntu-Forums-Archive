---
title: "Find all images using grep"
date: 2014-12-04
forum: General Help
---

### Post by blairm on 2014-12-04
Have returned to Linux after several years away, and need to find all images on my server - they're not in the expected folder.

Have forgotten most of what I used to know with the command line but my first thought was grep - after some reading it seemed grep ".jpg$" should do the trick but nothing happens; cursor just sits there blinking, even after leaving it 15 minutes. Running it from root.

Am I on the right track here? Is the command correct and, if so, should it be taking this long?

Cheers,
Blair

---

### Post by papibe on 2014-12-04
Hi blairm. Welcome back ):P

To find files with a particular name I'd would recommend using the command 'find'.

For instance:
```
sudo find / -iname '*.jpg'
```
It would be also a good idea to consider images with other names, like ending in 'jpeg', or may be other types like gif, etc.

This would find files with ending in jpg and jpeg (case insensitive).
```
sudo find / -iname '*.jpeg' -or -iname '*.jpg'
```
Hope it helps. Let us know if you have more questions.
Regards.

---

### Post by blairm on 2014-12-05
Thanks for your help, worked great.

---

