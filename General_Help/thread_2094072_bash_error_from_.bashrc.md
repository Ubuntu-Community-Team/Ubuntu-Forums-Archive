---
title: "bash error from .bashrc"
date: 2012-12-12
forum: General Help
---

### Post by donz on 2012-12-12
When starting lxterminal I get the following errors:


bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected

After further investigation I found that the error occurs in files in the directory /etc/bash_completion.d/

A few of the files are:

/etc/bash_completion.d/gcc
bash: [: too many arguments

/etc/bash_completion.d/ifupdown
bash: [: =: unary operator expected
bash: [: =: unary operator expected

/etc/bash_completion.d/ipsec
bash: [: =: unary operator expected

This is more of an annoyance than anything, but I find it hard to understand how this many errors could get into the distribution.  Has anyone else encountered this (and more importantly, fixed it)?

---

### Post by gnuser12 on 2012-12-12
Hi,
please post your .bashrc 
...

---

### Post by donz on 2012-12-14
Attached are my .bashrc file, and the system /etc/bash_completion and /usr/share/bash-completion/bash_completion files.

Also attached are several of the files where the error actually occurs:

---

