---
title: "help using paste command"
date: 2012-12-02
forum: General Help
---

### Post by spiritech on 2012-12-02
is it possible to paste text stored in a variable rather than a file.

so something like this.

```
paste file1 $VAR
```

rather than

```
paste file1 file2
```

the variable is actually a file with a few changes made to it. i am trying this way so that i can leave the original file intact.

actual code would be

```
paste - $VAR
```

as i already have the first file in STDOUT.

spiritech

---

### Post by Vaphell on 2012-12-02
```
$ echo $'111\n222\n333\n' | paste - <( echo $'abc\ndef\nghi' )
111	abc
222	def
333	ghi
```

---

