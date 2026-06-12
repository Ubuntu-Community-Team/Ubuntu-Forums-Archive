---
title: "sed performing substitution on x number of lines then quitting without cutting file s"
date: 2014-11-10
forum: General Help
---

### Post by O9aIevckc0 on 2014-11-10
currently when i try  sed -i 's/make/test/ ;143 q' file
it performs the desired substitution but after x number of lines and quitting any further content after the x number of lines is lost
(also happens to output when i dont use -i)

is their another way do this while keeping the rest of the file ?

---

### Post by Vaphell on 2014-11-11
if you tell sed to take only first 143 lines and to completely overwrite the source with -i, what do you expect?

```
sed '1,143 s/make/test/'
```

---

