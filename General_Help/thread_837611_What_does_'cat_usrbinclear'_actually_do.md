---
title: "What does 'cat /usr/bin/clear' actually do?"
date: 2008-06-22
forum: General Help
---

### Post by secondstage on 2008-06-22
[COLOR="Red"]WARNING MAY CAUSE SOMETHING TO HAPPEN THAT YOU DON'T WANT TO HAPPEN![/COLOR]

A couple of minutes ago, I typed ```
cat /usr/bin/clear
``` into terminal, and all of the text turned into weird symbols. I typed exit, and the computer seemed not to be damaged in any way. Does anyone know what this does and why?

---

### Post by brian_p on 2008-06-22
> **secondstage said:**
> [COLOR="Red"]WARNING MAY CAUSE SOMETHING TO HAPPEN THAT YOU DON'T WANT TO HAPPEN![/COLOR]

A couple of minutes ago, I typed ```
cat /
``` into terminal, and all of the text turned into weird symbols. I typed exit, and the computer seemed not to be damaged in any way. Does anyone know what this does and why?

You got the weird symbols because /usr/bin/clear is a binary file. If the terminal is left in an unreadable state type

```
reset
```

blind to restore it. No harm is done.

---

### Post by mali2297 on 2008-06-22
The command **cat** just prints the content of one or several files to standard output. Since /usr/bin/clear is a binary file, it will be unreadable (to a human).

---

