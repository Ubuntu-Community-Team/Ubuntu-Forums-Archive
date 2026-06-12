---
title: "Difference between insmod and modprobe"
date: 2012-12-21
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-21
Can anyone please tell me the difference between "insmod" amd "modprobe" command?

---

### Post by mcduck on 2012-12-21
Insmod is a  lot simpler and less smart tool, it usually requires you to give full path to the module, and to figure out the correct loading order and all the modules the one you want to load depends on.

Modprobe, on the other hand, is a higher-level tool for the task, it uses a pre-existing module dependency tree to find and load the module you want, and all the other modules it requires.

---

### Post by fdrake on 2012-12-21
i am sure the  man command will be helpfull in find all the options relative to each command
```

man insmod
man modprobe

```

---

