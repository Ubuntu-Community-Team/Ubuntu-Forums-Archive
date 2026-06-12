---
title: "How use Bash function as a command argument?"
date: 2013-07-09
forum: General Help
---

### Post by DrAlbert on 2013-07-09
Hi.
I wrote a script with name low:
```
#!/bin/bash
sudo nice -n 19 ionice -c 3 sudo -u $USER $1

```
I want to wrote another script that has a function and I want to use that function in that script like this:
```
#!/bin/bash
firstfunc(){
......a lot of commands......
}
low firstfunc

```
I cant use "low firstfunc" (without "") because it doesn't accept function as argument. I tried "low `firstfunc`" (without "") but it doesn't effect the niceness to function.
how can I use a function as a command argument in script?

---

