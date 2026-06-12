---
title: "Add new bash auto-completion feature?"
date: 2007-06-21
forum: General Help
---

### Post by grenadier32 on 2007-06-21
So...weird question. Is there a way to add new bash auto-completion features? Like, for example--if I type
```
ooffice -writer
```
I can tab-complete filenames after it. However, I've aliased
```
write
```
as the above command. Is it possible to get auto-completion for files to work with that too? If so, that would make it really easy to open files from the command line.

So is it possible to do this? Thanks in advance.

---

### Post by olejorgen on 2008-03-31
```

$ complete -p oowriter 
complete -o filenames -d -X '.[^./]*' -F _ooexp_ oowriter

```
```

complete -o filenames -d -X '.[^./]*' -F _ooexp_ writer

```
Also see [http://ubuntuforums.org/showthread.php?t=733397](http://ubuntuforums.org/showthread.php?t=733397)

PS: Normal completion (off all filenames) should work regardless of the above

---

