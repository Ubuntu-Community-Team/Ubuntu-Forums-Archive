---
title: "[SOLVED] Terminal Question"
date: 2008-04-12
forum: General Help
---

### Post by fifthwind on 2008-04-12
Is there a way to create a launcher that will open a terminal already navigated to a particular folder?

I'd like to have a special terminal launcher that is "pre-navigated" to my desktop. I know how to manually navigate to my desktop after launching a terminal, it just seems that I should be able to open one that's already there.

This is probably ridiculously easy, but any help is appreciated.

---

### Post by Olav on 2008-04-12
Command for your launcher:
```
gnome-terminal --working-directory=DIRNAME
```
Got that from:
```
man gnome-terminal
```

---

### Post by fifthwind on 2008-04-12
Thanks for the fast reply. That's exactly what I needed. I'll mark this as solved and crawl back into the little ignorant hole I came from... :)

---

### Post by Olav on 2008-04-12
> **fifthwind said:**
> Thanks for the fast reply. That's exactly what I needed. I'll mark this as solved and crawl back into the little ignorant hole I came from... :)Ignorance can be fixed... :D

Don't be ashamed to ask good questions.

---

### Post by h4mx0r on 2008-04-12
Kinda dissappointed me thought this would be one of those long winded comparison between different terminal benchmarks and process handling stuffs. They're always rather funny/interesting.

---

