---
title: "Using Grep in bash"
date: 2012-11-18
forum: General Help
---

### Post by usernamer on 2012-11-18
Hi,

I have two files (ASCII text), pass.old and pass.new, I want to find all the lines in pass.new which don't appear in pass.old (most lines overlap)... here's what I've got so far:

sort -n pass.old pass.new | uniq -u

that prints the lines in pass.new which don't appear in pass.old (but also the ones in pass.old which don't appear in pass.new), I want the output to be only the ones which appear in pass.new and not pass.old, I recon it'll be something to do with grep.

I've tried a few things like:

grep (sort -n pass.old pass.new | uniq -u) pass.new
or grep [sort -n pass.old pass.new | uniq -u] pass.new

I always get error messages, and I'm not quite sure how to write it so that it does grep of the output of sort -n etc. on pass.new,

Hopefully that made sense,

Any help/ideas on this one?

---

### Post by steeldriver on 2012-11-18
why not use use diff?

```
diff pass.new pass.old
```

---

### Post by diesch on 2012-11-18
```
 grep -v -F -f pass.old pass.new
```

---

### Post by usernamer on 2012-11-18
> **steeldriver said:**
> why not use use diff?

```
diff pass.new pass.old
```

Two reasons, firstly the lines have to be in the same order for diff to print the lines in 1 which aren't in the other, (although in this case they were, but I'm also interested in a more general method for doing it incase I come across similar problems in the future).

Also diff prints the different output from both files (although to be fair it does specify which file each line came from),

Not a bad shout, though, and cheers for the input.

---

### Post by usernamer on 2012-11-18
> **diesch said:**
> ```
 grep -v -F -f pass.old pass.new
```

Worked nicely. Cheers.

Also, as a side thing, is it possible to do what I was trying to do earlier somehow?

i.e. do:      grep [output of:  sort -n pass.new pass.old | uniq -u] pass.new

(so it prints the matches of each outputted line from:     sort -n pass.new pass.old | uniq -u with file pass.new)?

---

### Post by Vaphell on 2012-11-18
if you want to embed a command you need $() not ()

this should sorta work
```
grep -E "^("$( sort pass.* | uniq -u | tr '\n' '|' )"$)$" pass.new
```

---

