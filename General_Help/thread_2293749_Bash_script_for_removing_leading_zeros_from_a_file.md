---
title: "Bash script for removing leading zeros from a file name"
date: 2015-09-07
forum: General Help
---

### Post by glenn_morrissey2 on 2015-09-07
Hi all

I would like to know if anyone has any ideas for a simple bash script for removing leading zero's from a set of file names. So, for example,
0230.jpg becomes 230.jpg. But making sure that any trailing zero's are retained, so 0230.jpg stays as 230.jpg.
Any ideas?

---

### Post by vasa1 on 2015-09-07
For these files: 000abcf.txt  00abce.txt  0abcd.txt  abcn000.txt  abcy00.txt  abcz0.txt
running ```
rename 's/^0+//' *.txt
```gives me```
abcd.txt  abce.txt  abcf.txt  abcn000.txt  abcy00.txt  abcz0.txt
```
There's a man page for *rename* and the code above simply says that an occurrence of zero at the start of a filename (because of '^') one or more times (because of '+') should be replaced by nothing.

Edit: I know you asked for a Bash script!

Edit 2: and the -n option is available as well:```
       -n, --no-act
               No Action: show what files would have been renamed.
```

---

### Post by steeldriver on 2015-09-07
In pure bash, you could use a construct** like

```

for f in 0*.jpg; do echo mv -- "$f" "${f##+(0)}"; done

```

provided the extended glob shell option is enabled (shopt -s extglob) - I doubt it's faster than the perl-based `rename` command though, since it has to spawn multiple `mv` commands.

** [`echo` left in for testing - remove that if it seems to be doing the right thing]

---

