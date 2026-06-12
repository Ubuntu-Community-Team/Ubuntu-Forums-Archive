---
title: "bash.profile  bash.bashrc  login shell script???"
date: 2008-03-12
forum: General Help
---

### Post by illob32 on 2008-03-12
Hi,
What must I do to achieve this?
I'm completely baffled by all this.

[B]In your bash.profile/bashrc or login shell script, write this:

MSERVER=your_pc_name
export MSERVER[/B]

How can I get access to these files? How can I then enter what is being asked?
I'm a complete newbie at Linux, therefore do not understand all of the terminology
Could anyone help me?

Thanks a lot!!!

---

### Post by amingv on 2008-03-12
You can use this:
```
cp ~/.bashrc ~/bashrc.backup
gedit ~/.bashrc
```

go to the end of the file and add that, then save it.

Info:
~ is your home directory (/home/yourusername)
.bashrc is a script that is run every time you start a terminal session

---

