---
title: "'split' command files have no file ending!"
date: 2006-12-22
forum: General Help
---

### Post by RyanPower on 2006-12-22
Am I missing something? I'm trying to split a movie file into two using the 'split' command but the resulting files have no file ending.

```
split -b 90m MovieFile.avi
```

So hopefully that should (and does) split MovieFile.avi into files of max. 90 megabytes each: xaa, xab etc.

But how can I define a file extension to the code? Or change the file extension without having to use the terminal?

---

### Post by kidders on 2006-12-22
Hi there,

Can I ask why you would want to?

The answer to your question is that you can't ... I imagine split's author didn't see the need to implement a feature that would add suffixes to the names of bits of files :-(

Since you'd be using a terminal to issue the "split" command in the first place, why not try something like...
```
split -b 90m MovieFile.avi chunk && find -maxdepth 0 -iname chunk* -exec mv {} {}.chunk \;
```

---

