---
title: "[SOLVED] Check free space with df"
date: 2008-03-18
forum: General Help
---

### Post by PurposeOfReason on 2008-03-18
I'm trying to check my free space through a terminal. df on it's own does that, but is there a way for that to only show the Use% column?

---

### Post by johnl on 2008-03-18
I don't think df by itself has an option to only show the used%.  I generally do "df -h" to get a little nicer output.

---

### Post by unutbu on 2008-03-18
```

df | cut -c1-20,51-55

```
(I'm not sure that always works... it depends on df's formating.)
or maybe
```

df | tr -s ' ' | cut -d" "  -f 1,5

```
This second one should always work, but the spacing in the output looks bad.

---

### Post by PurposeOfReason on 2008-03-18
First one worked like a charm, thanks.

---

