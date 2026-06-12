---
title: "Revert from zsh to bash"
date: 2019-02-24
forum: General Help
---

### Post by qtheginger on 2019-02-24
I am using 18.04, and change does not work to change default she'll back to bash. I have tried every conceivable variation on that command, and nothing works. I have tried logging out and back in again, it doesn't help. It appears that chsh no longer actually works to revert from zsh. Any tips?

---

### Post by dragonfly41 on 2019-02-24
I simply run the command **exec bash** to convert to bash shell
and the command **exec zsh** to revert back.

---

### Post by sisco311 on 2019-02-24
What is the exact command are you using?

Are you getting any type of error message?

What login shell is listed in the /etc/passwd file?```
grep $USER /etc/passwd
```

Is bash listen in  /etc/shells as a valid login shell?
```
cat /etc/shells
chsh -l
```

---

