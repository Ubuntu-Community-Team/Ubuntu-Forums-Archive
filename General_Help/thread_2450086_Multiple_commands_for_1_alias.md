---
title: "Multiple commands for 1 alias"
date: 2020-09-07
forum: General Help
---

### Post by swangnation on 2020-09-07
Hi guys,

I've searched google for a straightforward answer that i can understand but no luck so far.

I need to put 2 commands or multiple commands for a single alias and i don't know how to do that.

Example, i would like to run systemd-resolve --statistics and then systemd-resolve --flush-cache. I have already created a .sh file for this and from the terminal it works fine. I just want to make it permanent.

Can anyone help?

---

### Post by dinkidonk on 2020-09-07
What do you understand by "*multiple commands for a single alias*"?

---

### Post by ActionParsnip on 2020-09-07
if you mean one alias runs lots of commands then you could make a shell script to run what you like.

I think you can also do:
```

alias fullupgrade="sudo apt update; sudo apt -y upgrade; sudo apt clean"

```

---

### Post by swangnation on 2020-09-07
> **dinkidonk said:**
> What do you understand by "*multiple commands for a single alias*"?

Exactly what actionparsnip just indicated. Maybe i worded the question incorrectly but ultimately i want a number of commands for 1 alias.

---

### Post by swangnation on 2020-09-07
thank you very much actionparsnip, that did the trick. I edited the bash rc file and all is well

---

### Post by ActionParsnip on 2020-09-08
No worries. Please mark as solved

---

