---
title: "lots of missing packages"
date: 2014-02-03
forum: General Help
---

### Post by Tristan_Williams on 2014-02-03
I am attempting LFS, but I can't even get past the preface.

For some reason, I am missing packages that (at least I thought) should be part of the base ubuntu system.

Here is the output from the script in Preface section vii:
```

Tristan: ~ $bash version-check.sh
bash, version 4.2.45(1)-release
/bin/sh -> /bin/dash
Binutils: (GNU Binutils for Ubuntu) 2.23.52.20130913
bison (GNU Bison) 2.7.12-4996
/usr/bin/yacc -> /usr/bin/bison.yacc
bzip2,  Version 1.0.6, 6-Sept-2010.
Coreutils:  8.20
diff (GNU diffutils) 3.2
find (GNU findutils) 4.4.2
version-check.sh: line 14: gawk: command not found
/usr/bin/awk -> /usr/bin/mawk
gcc-4.8.real (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
g++-4.8.real (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
(Ubuntu EGLIBC 2.17-93ubuntu4) 2.17
grep (GNU grep) 2.14
gzip 1.6
Linux version 3.11.0-15-lowlatency (buildd@batsu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #8-Ubuntu SMP PREEMPT Sun Dec 15 21:38:27 UTC 2013
m4 (GNU M4) 1.4.16
GNU Make 3.81
GNU patch 2.7.1
Perl version='5.14.2';
sed (GNU sed) 4.2.2
tar (GNU tar) 1.26
version-check.sh: line 31: makeinfo: command not found
Texinfo: 
xz (XZ Utils) 5.1.0alpha
g++ compilation OK

```

And don't tell me to go to synaptic and install those packages... 
I tried that, and none of them could be found. I keep getting the "no installation candidate" error.

So maybe, since I am running Ubuntu MINIMAL, I could be missing a repository or something... 

As a side note, I just had almost this same problem with gnucash, because apt-get could not find some of its dependencies.


So what do I do?

---

### Post by steeldriver on 2014-02-04
IIRC mawk is the default awk (instead of gawk) regardless of which version you install - supposedly for performance reasons (gawk has some extra features including some regex stuff like a case-insensitive match flag and support for regexes as field separators - but that makes the 'engine' slower). You should be able to install gawk from the main repository.

makeinfo should be part of the texinfo package - again that should be in 'main'

I don't see anything else missing?

---

