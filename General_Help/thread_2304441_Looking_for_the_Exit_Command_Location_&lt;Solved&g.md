---
title: "Looking for the Exit Command Location &lt;Solved&gt;"
date: 2015-11-26
forum: General Help
---

### Post by ulrichkenneth on 2015-11-26
Hello All, 

I am looking for the exit script itself. Like when you type "exit" to get out of root or to exit the ssh shell.

I know you can type exit, and get out, but I am looking for the actual script that does it. Like apt-get for example is in the /user/bin file. I've looked and even done a locate command for exit, but can't seem to find where the actual script that runs when used is at.

Is it part of the kernel? I've tried looking on Google, but either, I'm the first person to ask, or my searching skills on this isn't good.

---

### Post by sisco311 on 2015-11-26
exit is a shell builtin command. See: [http://mywiki.wooledge.org/BashSheet?highlight=%28builtin%29#Builtins](http://mywiki.wooledge.org/BashSheet?highlight=%28builtin%29#Builtins)

---

### Post by ulrichkenneth on 2015-11-26
Thank you for that!

That was exactly what I was looking for.

---

### Post by Lars Noodén on 2015-11-26
Also the manual page for bash will have a lot of information. 

```

man bash

```

---

### Post by Habitual on 2015-11-27
```
type exit
```
exit is a shell builtin

---

