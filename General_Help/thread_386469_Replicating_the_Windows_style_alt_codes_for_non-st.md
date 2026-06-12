---
title: "Replicating the Windows style alt codes for non-standard ASCII characters"
date: 2007-03-17
forum: General Help
---

### Post by Eschatokyrios on 2007-03-17
I like the Windows alt codes, damnit! I wish there were a linux equivalent. There's no other easy way that I know of to input a wide variety of foreign characters easily. Is there perhaps a program that some kind soul made that replicates this function for linux? And maybe even improved on it by adding codes for some of the unicode characters?

---

### Post by aepfelx on 2007-03-17
Many applications implement the still-relatively-obscure recommendation in the [ISO 14755]("www.cl.cam.ac.uk/~mgk25/volatile/ISO-14755.pdf") standard: hold down Control-shift-, and then type in the hexadecimal unicode codepoint of the character you want. Some examples that work in my browser (with the fonts i have):

Ctrl-Shift-F1 - ñ (latin lower-case n with tilde)
Ctrl-Shift-FE - þ (latin lower-case thorn)
Ctrl-Shift-5D2 - &#1490; (hebrew gimel)
Ctrl-Shift-1332 - &#4914; (something amharic)
Ctrl-Shift-2741 - &#10049; (8-petal flower)
Ctrl-Shift-6666 - &#26214; (some cjk ideograph)

---

