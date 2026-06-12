---
title: "Ignoring a failed command"
date: 2008-02-25
forum: General Help
---

### Post by legatek on 2008-02-25
I use acroread from the repos to read PDFs, but it crashes on a regular basis, eating cpu cycles and heating up my processor to no purpose. During the day when I'm at the computer I can kill it and restart it, but when I leave for the day and lock my screen I always return in the morning to find my fan running full blast to cool my processor, and a crashed acroread. To account for this bug I made an alias in .bash_aliases to kill all instances of acroread and lock the screen:

```
alias lock='killall acroread && gnome-screensaver-command --lock'
```

The problem is, when I have no instances of acroread running, my terminal returns "acroread: no process killed" and doesn't proceed to lock the screen. How can I change this so that if there are no acroread processes running, bash ignores the failed command and locks the screen anyway?

Thanks for your help.

---

### Post by pointone on 2008-02-25
The "&&" is a logical and operator in Bash, and it does exactly what you describe. If you want both commands to run regardless of the result, use the ";" instead.

```
alias lock='killall acroread; gnome-screensaver-command --lock'
```

If you only want the second command to run if the first command fails, use the logical or operator "||":

```
alias lock='killall acroread || gnome-screensaver-command --lock'
```

---

