---
title: "mass .bmp to .png conversion using &quot;convert&quot;"
date: 2008-05-13
forum: General Help
---

### Post by HUNTtheHIPPO on 2008-05-13
I have 20 or so .bmp files that I need to convert to .png. I could do it by hand in the terminal, but I would rather have the computer do it for me. I think I should do 

ls -d *.bmp

and then | this into 

convert (files from ls).bmp (files from ls).png  .

However I do not know how to tell "convert" to reference the files from "ls," and I am not entirely comfortable with how the | works. Any help would be appreciated. Thanks.

---

### Post by SpaceTeddy on 2008-05-14
```
for i in *.bmp; do convert $i ${i/.bmp}.png; done
```

take from [[COLOR="Blue"]this[/COLOR]]("http://www.debian-administration.org/articles/150") site as an example for renameing multiple files

hope it helps :)

---

