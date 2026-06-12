---
title: "Customizing PS1 gives weird behavior"
date: 2007-07-26
forum: General Help
---

### Post by B-Con on 2007-07-26
I have the following in my .bashrc profile script:
```
export PS1="\e[1;36m\u@\h:\e[1;34m\w\e[1;36m\$\e[m "
```
This customizes my prompt perfectly fine. But for some reason whenever I try to enter a command more than roughly 18 to 21 characters (its inconsistent) long the command now wraps back to the very beginning of the line and the cursor starts overwriting the prompt itself. The command will execute fine, though, it's just that the visual is all messed up.

I know his has to be related to my PS1 variable because it started when I changed it and disappears when I restore it's original value.

Any solutions? I have no clue what could be wrong.

---

### Post by B-Con on 2007-07-27
Solution:

I had to enclose all escape sequences in [ ]:
```
export PS1="\[\e[32m\]\u@\h:\[\e[1;31m\]\w\[\e[1;34m\]\$\[\e[0m\] "
```

---

