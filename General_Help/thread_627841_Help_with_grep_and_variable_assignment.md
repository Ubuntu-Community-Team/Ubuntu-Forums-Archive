---
title: "Help with grep and variable assignment"
date: 2007-11-30
forum: General Help
---

### Post by dizwell on 2007-11-30
I want to be able to check the amount of memory on a box and then assign that value to a variable in a bash script. Quickest way I know of checking the memory amounts would be:

```
cat /proc/meminfo | grep MemTotal
```

...but that outputs a result similar to:

```
MemTotal:         1035584 kB
```

...which then makes it a bit difficult to test for the value being greater or less than some purely numeric value. Could someone propose a bit of shell scripting magic that would return just the result "1035584", please?

---

### Post by PeterJS on 2007-11-30
> **dizwell said:**
> I want to be able to check the amount of memory on a box and then assign that value to a variable in a bash script. Quickest way I know of checking the memory amounts would be:

```
cat /proc/meminfo | grep MemTotal
```...but that outputs a result similar to:

```
MemTotal:         1035584 kB
```...which then makes it a bit difficult to test for the value being greater or less than some purely numeric value. Could someone propose a bit of shell scripting magic that would return just the result "1035584", please?


Try:
```

somevar=`cat /proc/meminfo | grep MemTotal | awk '{print $2}'`

```

---

### Post by dizwell on 2007-11-30
You're a genius, sir!

Thank you. Multiple pipes AND a bit of awk... my head begins to spin!

---

