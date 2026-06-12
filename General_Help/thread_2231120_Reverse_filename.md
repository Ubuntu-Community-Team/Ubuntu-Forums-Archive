---
title: "Reverse filename"
date: 2014-06-23
forum: General Help
---

### Post by matrooswolf on 2014-06-23
Hi, 
Is there an easy way to reverse filenames? Example: abcdef.jpg becomes fedcba.jpg.

---

### Post by steeldriver on 2014-06-23
You can use the rev command

```

DESCRIPTION
     The rev utility copies the specified files to standard output, reversing
     the order of characters in every line.  If no files are specified, stan&#8208;
     dard input is read.

```

If you don't want to reverse the suffix as well, you will need to remove and replace it e.g.

```

$ f="abcdef.jpg"
$ 
$ r="$(rev <<< "${f%.*}").${f##*.}"
$ 
$ echo "$r"
fedcba.jpg

```

---

### Post by matrooswolf on 2014-06-23
Thanks for mentioning the rev command. Does it actually reverse the filename on disk (this it what I want), or does it simply make a string of the reverse characters?

---

### Post by Vaphell on 2014-06-23
it's a string that can be plugged into *mv* command, thus solving your problem

in steeldriver's example it would be
```
mv "$f" "$r"
```

---

### Post by matrooswolf on 2014-06-29
Thanks for explaining, vaphell.
Is there a way to combine the rev and mv command in one command that I could reuse, while simply replacing the filename?

---

### Post by steeldriver on 2014-06-29
Well you could just do a "one-liner" to loop over the list of files, like

```

for f in *.jpg; do echo mv "$f" "$(rev <<< "${f%.*}").${f##*.}"; done

```

However I thought about this some more in the meantime - since Ubuntu provides the perl-based rename command, and perl has its own string reverse function, you should be able to do something like

```

rename -vn -- 's/(.*)[.]([^.]*)$/join(".",my $rev=reverse($1),$2)/e' *.jpg
abcdef.jpg renamed as fedcba.jpg
pqrstu.jpg renamed as utsrqp.jpg

```

The -n option is only for testing purposes.

---

