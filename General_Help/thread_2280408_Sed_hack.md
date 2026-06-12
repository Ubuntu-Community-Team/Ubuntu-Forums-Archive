---
title: "Sed hack"
date: 2015-05-30
forum: General Help
---

### Post by CkDGTAT on 2015-05-30
Hi,

I need to convert latex to bash calculator sentences. How can I convert

```
\frac{a_{i}}{b_{i}}
```

to

```
 a_{i}  /   b_{i}  
```

Thank you

---

### Post by Lars Noodén on 2015-05-30
One way to do it is like this:

```

sed 's**#**\\frac{\([color=#00ff00]**[^}]***[/color]\)}}{\([color=#00ff00]**[^}]***[/color]\)}}**#**[color=#00ff00]**\1} / \2}**[/color]**#**g'

```

The s/// is written like s### instead to allow for use of / in the replacement pattern.  The backslash is escaped with another backslash. \\

There are other ways if that does not do it.

---

