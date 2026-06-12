---
title: "Problem with shell prompt color"
date: 2007-06-22
forum: General Help
---

### Post by leeyee on 2007-06-22
Hi guys,

I've just installed Feisty two days ago, and when I configure shell prompt I encounter the following problem.

First I added the line into .bashrc file, this line worked fine under Egye.
```
export PS1="\[\e[1;32m\][\[\e[1;34m\]\u\[\e[1;36m\]@\[\e[1;36m\]\h\[\e[1;32m\] \w\[\e[1;32m\]]\[\e[0m\]$ "
```

Things look fine when I enter English-named folder, but went to wrong when I tried to enter Chinese-named folder, it leaves a big space between prompt and command I typed. However, if I comment the line, things would be fine again. for details please to see the attached screenshot. One of them is plain prompt, and the other is colorful one.

I just wondered if Feisty has changed the way to configure colorful shell prompt? If so, can anybody help me with this issue? 

Thanks alot

---

