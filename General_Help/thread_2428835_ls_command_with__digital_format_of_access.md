---
title: "ls command with  digital format of access"
date: 2019-10-09
forum: General Help
---

### Post by petrogromovo on 2019-10-09
Hello,
Using command 
```
ls -la

```in ubuntu 18 I see access as “[COLOR=#000000]-rwxr--r--  1 root  root [/COLOR]” are there some keys to show it in digital format, like in cmod command 
when I set command :
```
[COLOR=#000000]sudo chmod 600 ~/.ssh/config[/COLOR]
```[COLOR=#000000]
 
 Thanks![/COLOR]

---

### Post by DuckHook on 2019-10-10
> **petrogromovo said:**
> …are there some keys to show it in digital format…
There is no switch in the [FONT=Lucida Console]ls[/FONT] command for this. The man page for [FONT=Lucida Console]ls[/FONT] is instructive for seeing all switches:```
man ls
```

---

### Post by spjackson on 2019-10-10
Not with ls, but stat may help, e.g. ```
stat --printf="%a\t%n\n" *
```

---

