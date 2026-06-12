---
title: "Way to keep grep's colored results when piped into less?"
date: 2014-09-10
forum: General Help
---

### Post by greg2lapa on 2014-09-10
If I run ```
cat /etc/login.defs | grep -A 50 -B 50 "^USE\+"
``` grep colors any matches in red. 

If I run ```
cat /etc/login.defs | grep -A 50 -B 50 "^USE\+" | less
``` the red color is not displayed in the less program. 

Is there a way to get less to highlight the grep finds in red?

---

### Post by papibe on 2014-09-10
Hi greg2lapa.

Try this:
```
cat /etc/login.defs | grep **[COLOR="#FF0000"]--color=always[/COLOR]** -A 50 -B 50 "^USE\+" | less **[COLOR="#FF0000"]-r[/COLOR]**
```
or just
```
grep **[COLOR="#FF0000"]--color=always[/COLOR]** -A 50 -B 50 "^USE\+" /etc/login.defs | less **[COLOR="#FF0000"]-r[/COLOR]**
```
Regards.

---

### Post by greg2lapa on 2014-09-11
Thanks :)

---

