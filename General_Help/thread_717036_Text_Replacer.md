---
title: "Text Replacer?"
date: 2008-03-06
forum: General Help
---

### Post by chr1831 on 2008-03-06
i use to have a text replacer for windows (macro pro i think it was called?) i was wondering if there was anything like that for linux???

-Chris

---

### Post by PeterJS on 2008-03-06
Most text editors have a find and replace function.

If you're looking to do text replacement in batch sed is the way to go. Although a simplitic an contrived example you could use:
```

sed -i 's/replace\ this\ with/this\ other\ text/g' somefile

```

Sed searchs based on regular epressions and supports rembering matches to sub experssions to be reinserted in the replacement text.

---

### Post by pointone on 2008-03-06
```
man sed
```

---

### Post by chr1831 on 2008-03-06
i am looking for more of a i type blah and it replaces the text (after i finish it) with Boys Laugh All Hours

-Chris

---

