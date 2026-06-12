---
title: "Can unicode characters be batch-converted to ASCII?"
date: 2008-02-28
forum: General Help
---

### Post by NotPhil on 2008-02-28
I have many text files that have characters that display in both my text editor as "a (circumflex) - box (with four letters or numbers inside it) - box (with four letters or numbers inside it)."

I'm guessing the a-boxes represent unicode characters that my text-editors and word processor can't read. If not, please correct me.

For each file, I can do a search on these characters and replace them with characters that will display correctly, for instance, Edit > Replace ... > (a^[0080][009C]) with ", but I have hundreds of these files and this would take forever.

So, is there any way to batch convert these files? Perhaps SED could do it with a little coaxing?

---

### Post by trobbins on 2008-02-28
I was going to have to make many conversions like this myself a while back but only halfway researched how to do it.  I would look at this program:

[http://billposer.org/Software/uni2ascii.html](http://billposer.org/Software/uni2ascii.html)

Eh, I was going to post some idea of how to use it, but I cannot think of a good example.

---

