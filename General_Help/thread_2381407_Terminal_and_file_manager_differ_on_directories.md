---
title: "Terminal and file manager differ on directories"
date: 2017-12-30
forum: General Help
---

### Post by raleigh3 on 2017-12-30
How come a terminal shows ~, while my file manager shows /home/andy/ ??

---

### Post by The Cog on 2017-12-30
~ is shorthand your your home directory.
Try the command "echo ~" to see.

---

### Post by HermanAB on 2017-12-30
One can use ~ in a script and then it will work for any user.

---

### Post by sisco311 on 2017-12-30
> **HermanAB said:**
> One can use ~ in a script and then it will work for any user.

While tilde expansion in very handy in interactive shells, in scripts is recommended to use $HOME.


For more info:
[http://wiki.bash-hackers.org/syntax/expansion/tilde](http://wiki.bash-hackers.org/syntax/expansion/tilde)
BashPitfalls 26 & 28

---

### Post by raleigh3 on 2017-12-31
Thanks for the explanation.

---

