---
title: "How with grep command exclude search in dubdirectory ?"
date: 2019-11-01
forum: General Help
---

### Post by petrogromovo on 2019-11-01
Hello,
Under Kubuntu 18 I use command
```
grep -Hrn 'backend' --include="*.vue" /mnt/_work_sdb8/wwwroot/lar/hostels2/resources/js/components/BS4

```when I need to search for some string inside of a directory.

I search for an option to exclude “/admin/” subdirectory, something like (that does not work):
```
grep -Hrn 'backend' --include="*.vue" --exclude="*admin*" /mnt/_work_sdb8/wwwroot/lar/hostels2/resources/js/components/BS4

```

I found option to exclude :
```
grep "word1" | grep -v "word2"
grep -r 'wanted_pattern' * | grep -v 'unwanted_pattern'

```

But I failed combine it , like
```
grep -Hrn 'backend' --include="*.vue" /mnt/_work_sdb8/wwwroot/lar/hostels2/resources/js/components/BS4 | grep -v --include="*admin*"

```
Got message : 
```
Usage: grep [OPTION]... PATTERN [FILE]...
Try 'grep --help' for more information.

```

Which is valid format ?

Thanks!

---

### Post by spjackson on 2019-11-01
> **petrogromovo said:**
> 
But I failed combine it , like
```
grep -Hrn 'backend' --include="*.vue" /mnt/_work_sdb8/wwwroot/lar/hostels2/resources/js/components/BS4 | grep -v --include="*admin*"

```

```
grep -Hrn 'backend' --include="*.vue"  /mnt/_work_sdb8/wwwroot/lar/hostels2/resources/js/components/BS4 | grep  -v /admin/

```

---

