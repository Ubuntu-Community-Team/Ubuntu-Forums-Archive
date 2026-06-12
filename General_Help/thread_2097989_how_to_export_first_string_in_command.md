---
title: "how to export first string in command"
date: 2012-12-25
forum: General Help
---

### Post by sccuser on 2012-12-25
Hi, please help me in the following matter, that I would like to export the first string of certain line of command, for example:

root@ubuntu:~#  who
root     pts/0        2012-12-25 17:18 (ubuntu.domain.name.com)
firstname.lastname tty7         2012-12-25 16:55

The thing that I need is ONLY "firstname.lastname" information, not including the rest.
Much appreciated!
Have a good day guys.

---

### Post by steeldriver on 2012-12-25
a couple of ideas

```
$ echo "firstname.lastname tty7 2012-12-25 16:55" | awk '{print $1}'
firstname.lastname
$
$ echo "firstname.lastname tty7 2012-12-25 16:55" | cut -d' ' -f1
firstname.lastname
$ 

```

---

### Post by rnerwein on 2012-12-25
> **sccuser said:**
> Hi, please help me in the following matter, that I would like to export the first string of certain line of command, for example:

root@ubuntu:~#  who
root     pts/0        2012-12-25 17:18 (ubuntu.domain.name.com)
firstname.lastname tty7         2012-12-25 16:55

The thing that I need is ONLY "firstname.lastname" information, not including the rest.
Much appreciated!
Have a good day guys.
hi
 who | awk '{print $1}'

---

### Post by sccuser on 2012-12-25
Perfect!
Thanks so much **steeldriver** & **rnerwein**.

Just one more question please.
For the out put
> firstname.lastname tty7 2012-12-25 16:55what's the solution if I need
> tty7or
> 2012-12-25or
> 16:55

Edit: yep I've got it, please forget. Thanks guys! :)

---

### Post by rnerwein on 2012-12-25
> **sccuser said:**
> Perfect!
Thanks so much **steeldriver** & **rnerwein**.

Just one more question please.
For the out put
what's the solution if I need
or
or


Edit: yep I've got it, please forget. Thanks guys! :)
ok
$0 is the whole string (line)
$1 is the first field delimited by " " space ....
$2 is the second field
......
so if you want to have only the time: who | awk ' { print $4 }'
and if you want to get the tty : who | awk '/tty/  { print $2}'
awk is a powerful tool try to learn it.
cheers

---

