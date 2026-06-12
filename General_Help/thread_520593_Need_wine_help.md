---
title: "Need wine help"
date: 2007-08-08
forum: General Help
---

### Post by bolex on 2007-08-08
When i typed 
```
wine tmoriginaldemo.exe
```
(or any .exe files) in the terminal, it replied:

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\tmoriginaldemo.exe": Module not found
```

What should i configure, so i can run exe games in Ubuntu? :/

I have just configured it, wich i mean pressing the autodetect.

The trackmania demo is located at my desktop, and if i use the command

```
wine ~/Desktop/tmoriginaldemo.exe
```

it just write back:

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.


```

---

### Post by Adramelech on 2007-08-08
I think is because it have no access to your .wine directory, check wine configuration and chek if it has access to your home directory or not. Thats the way i fixed the same problem

---

### Post by bolex on 2007-08-08
by wich you mean?

---

### Post by apetresc on 2007-08-08
> **bolex said:**
> by wich you mean?

He means: what is the output of ```
ls -al ~/.wine
```

I don't know much about wine, but Adramelech sounds like he knows what he's talking about, and that line I just gave you is how you would check the permissions on your .wine directory.

---

### Post by Incense on 2007-08-08
Have you run winecfg yet?

---

