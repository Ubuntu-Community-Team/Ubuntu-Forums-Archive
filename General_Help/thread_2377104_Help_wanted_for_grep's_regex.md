---
title: "Help wanted for grep's regex"
date: 2017-11-09
forum: General Help
---

### Post by vasa1 on 2017-11-09
I'm trying to come up with a grep for the following list (in a file called test.txt)> **less**
liba52-0.7.4
libe-book-0.1-1
libfreehand-0.1-1
libmeanwhile1
librdf0
[B]libreadline6
libreoffice-writer[/B]
libroken18-heimdal
libsamplerate0so that, of the lines beginning with "lib", only the two lines starting with "libre" are output. In other words, I want the output to be:> less
libreadline6
libreoffice-writerIf I use```
grep -Ev "^lib[^r]" test.txt
```I get```
less                                                                    
librdf0
libreadline6
libreoffice-writer
libroken18-heimdal

```But if I use```
grep -Ev "^lib[^r][^e]" test.txt
```things get worse rather than better :( ```
less
lib_me_anwhile1
librdf0
libreadline6
libreoffice-writer
libroken18-heimdal
```My thinking was that```
grep -Ev "^lib[^r][^e]"
```should retrieve all lines excluding those beginning with "lib" except for those beginning with "lib" but also being immediately followed by "r" and then "e". Obviously, I'm not getting something right..

---

### Post by steeldriver on 2017-11-09
I don't think you can achieve that with an extended regex pattern - however you can do it with a PCRE lookahead:

```

$ cat test.txt
less
liba52-0.7.4
libe-book-0.1-1
libfreehand-0.1-1
libmeanwhile1
librdf0
libreadline6
libreoffice-writer
libroken18-heimdal
libsamplerate0

$ grep -Pv '^lib(?!re)' test.txt
less
libreadline6
libreoffice-writer

```

---

### Post by aromo2 on 2017-11-09
grep -e "less|libre"

---

### Post by untrustytahr on 2017-11-10
Yeah, I have problems on inverting regex stuff too. I apologize in advance because this will probably get wordy... hard to get around it.

There are a couple of ways to look at it:
First way-  instead of doing grep -Ev PATTERN,  do a regular grep -E PATTERN.  For most people working in the "forward" direction makes more sense (at least it does for me).  If the 'forward' results make sense, the -v (invert) selection just means exclude those results from the list. So:
```
grep -E "^lib[^r][^e]" test.txt

means return results that "start with lib" - "not r" - "not e"

that would return

liba52-0.7.4
libe-book-0.1-1
libfreehand-0.1-1
libsamplerate0
```the -v invert means take those 4 out of your original list of 10.


The second way is to do the -v first so:

grep -Ev "^lib[^r][^e]" test.txt

means return results that do not: "start with lib" - "not r" - "not e"

so let's go through the list with the 3 parts of your pattern. If any part of the pattern fails, it will print since we are using -v:

```
less <---** fails** on ^lib = print
liba52-0.7.4 <--- pass on ^lib, pass on 'not r', pass on 'not e' = don't print
libe-book-0.1-1 <--- pass on ^lib, pass on 'not r', pass on 'not e' = don't print
libfreehand-0.1-1 <--- pass on ^lib, pass on 'not r' pass on 'not e' = don't print
libmeanwhile1 <--- pass on ^lib, pass on 'not r', **fail on 'not e'** = print
librdf0 <--- pass on ^lib,** fail on 'not r'**, pass on 'not e' = print
libreadline6 <--- pass on ^lib,** fail on 'not r'**,** fail on 'not e'** = print
libreoffice-writer <--- pass on ^lib,** fail on 'not r'**, **fail on 'not e'** = print
libroken18-heimdal <--- pass on ^lib, **fail on 'not r'**, pass on 'not e' = print
libsamplerate0 <--- pass on ^lib, pass on 'not r', pass on 'not e' =don't print

```
I'm not sure if that all makes sense... it's difficult to explain without getting into long explanations.

---

### Post by vasa1 on 2017-11-10
Thanks all!

steeldriver's solution does it for me!

---

