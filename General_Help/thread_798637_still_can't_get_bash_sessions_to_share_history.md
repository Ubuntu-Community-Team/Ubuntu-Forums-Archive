---
title: "still can't get bash sessions to share history"
date: 2008-05-18
forum: General Help
---

### Post by TeeAhr1 on 2008-05-18
I've been prodding at this for a while with no success. Here's what I've got in .bashrc now...
```

# Append history instead of overwriting...
shopt -s histappend
# ... and append and re-read the history every time a prompt is displayed
export PROMPT_COMMAND="history -a; history -n"

```
Not doin' it. Any advice?

thx-
p.

---

### Post by roe_polak on 2008-05-18
Remember to source your bashrc after changing it or just open up two new terminals to test it.

EDIT: According to this site [http://forum.ducea.com/discussion/23/bash-history-for-multiple-session/](http://forum.ducea.com/discussion/23/bash-history-for-multiple-session/) you don't need to export PROMPT_COMMAND

---

### Post by TeeAhr1 on 2008-05-18
I have sourced my .bashrc (yes, in all open terms), and I've tried it with and without export. No luck.

---

### Post by roe_polak on 2008-05-18
If you're really keen on getting the history sharing to work and not afraid to try something different from bash, I can really recommend zsh. It requires some configuration, but I can post my zshrc to get you started.

zsh has history sharing and very advanced tab completion. It probably makes one a sloppy typist because it has error corrections :)

It is available in the repos.

---

