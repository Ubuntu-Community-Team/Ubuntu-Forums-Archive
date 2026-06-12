---
title: "[SOLVED] Make a file &amp;quot;only append&amp;quot;?"
date: 2007-06-26
forum: General Help
---

### Post by olejorgen on 2007-06-26
After loosing my list of packages to try, when I get access to real dsl, atfer doing a 'echo waijn > try' instead of 'echo wijn >> try' I was wondering if it's possible to make a file "append only"?

I tried to make the folder unwriteable, but 'echo asdf > try' still worked. (I would guess that > overwrites the file?)

I tried to compare creation time with 'stat', but it's not an attribute!?

Then I tried 'strace echo asdf >try' to check what was going on, but "try" did not exist in the output (?)

Help would be appreciated :)

---

### Post by olejorgen on 2007-06-29
Figured it out:
```

sudo chattr +a try

```

---

