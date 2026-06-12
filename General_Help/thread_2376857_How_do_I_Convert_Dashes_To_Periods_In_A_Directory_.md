---
title: "How do I Convert Dashes To Periods In A Directory At Once?"
date: 2017-11-06
forum: General Help
---

### Post by kamrynborden on 2017-11-06
I have a bunch of files I wish to convert from dashes to periods. Is there a way to do that all at once, so I don't have to manually change them all?

I have a bunch of TV shows where I have the season number and episode separated by a dash and want them to be periods instead.

For example:

Matlock 1-1: Diary Of A Perfect Murder
Matlock 1.1: Diary Of A Perfect Murder

---

### Post by TheFu on 2017-11-06
I'd change all the spaces into '_' too.  Scripting is a hassle for things with spaces more than with punctuation.

Anyway ... the program is called 'rename' 

```
$ rename 's/ /_/g' Mat*
```

The tool  uses regex. If you know it, it is trivial. If you don't, then get to a regex tutorial first.

I'd also remove all ':' from the filenames.  That character causes issues with certain OSes.

---

### Post by vasa1 on 2017-11-06
More about naming files: [https://pclosmag.com/html/Issues/201607/page03.html](https://pclosmag.com/html/Issues/201607/page03.html)

---

