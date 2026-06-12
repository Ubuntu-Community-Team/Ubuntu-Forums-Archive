---
title: "get string from character number"
date: 2015-02-15
forum: General Help
---

### Post by CkDGTAT on 2015-02-15
Hi,

I have a link 

```
[FONT=monospace]fromCharCode(98,111,114,105,115,46,98,101,97,117,100,101,64,101,112,102,108,46,99,104)+'?')">[/FONT][COLOR=#000000][FONT=monospace]e-mail[/FONT][/COLOR][FONT=monospace]</a>[/FONT]
```

How can I possibly get the string from CLI?

---

### Post by sudodus on 2015-02-15
```
printf %x 65
```

converts from decimal to hexadecimal (41)

```
printf "\x$(printf %x 65)\n"
```

converts to the ascii character (A) where \n gives you a final line feed.

---

