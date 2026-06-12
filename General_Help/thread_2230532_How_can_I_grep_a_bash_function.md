---
title: "How can I grep a bash function"
date: 2014-06-19
forum: General Help
---

### Post by CkDGTAT on 2014-06-19
Hi,I was wandering if you had any idea to select a function from { to } in a .bashrc for instance.All I have done so far isfunction select_my_function_from_a_file(){        if [ -n "$(awk "/function $@()/ {print}" ~/.b)" ] > /dev/null            then                   awk "/function $@()/,/}/ {print}" ~/.b | grep -99999 "$@"        else           awk "/$@/ {print}" ~/.b | grep -99999 "$@"fi}Thank you

---

### Post by Vaphell on 2014-06-20
if you wanted to list functions that the system has loaded you could use
*declare -F* to list function names
*declare -f* to list function definitions

eg

```
$ declare -F
...
declare -f quote
declare -f quote_readline
declare -f set_prefix
$ declare -f quote
quote () 
{ 
    echo \'${1//\'/\'\\\'\'}\'
}
```

---

