---
title: "colors while listing the files using 'ls' in bash"
date: 2007-08-28
forum: General Help
---

### Post by rajarshihri on 2007-08-28
HI,

I have installed ubuntu in my system.
When I list the files using ls, it shows evey type of file in same color, while I expect it to show in different colors e.g  directories show up in blue, while jpg files in pink....

what should i do?

---

### Post by ayoli on 2007-08-28
edit or create a file called .bashrc in your home directory (note the leading dot that means it's an hidden file) and put these line in it:
```
eval `dircolors -b`
alias ls='ls --color=auto'
```
close your term and reopen , should work.

---

