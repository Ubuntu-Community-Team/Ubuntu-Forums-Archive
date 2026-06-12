---
title: "bashrc_profile not loading"
date: 2006-12-06
forum: General Help
---

### Post by odysseus.lost on 2006-12-06
Hi,

I have added some environment variables on my ~/.bashrc_profile.... but whenever I open a new terminal the variables are simply not loaded which means that .bashrc_profile is not loaded unless I manually source it...

Any clues? Cheers.

---

### Post by taurus on 2006-12-06
Have you tried ~/.bashrc?

---

### Post by po0f on 2006-12-06
odysseus.lost,

Follow taurus's advice.  ~/.bash_profile is only sourced on login shells, ~/.bashrc is sourced every time a Bash process is started.  Depending on which terminal emulator you are using, you can have the terminal emulator behave like a login shell.  For example, rxvt-unicode has a configuration option  named loginShell that you would set in ~/.Xresources:
```
[FONT="Courier New"]urxvt.loginShell: true[/FONT]
```

[EDIT]

I believe there is a way to do it in gnome-terminal, but I don't use it.

---

### Post by odysseus.lost on 2006-12-06
Cheers,

adding the environment to the .bashrc instead of the .bash_profile seems to do the job.... I was falsely lead to believe that .bash_profile is loaded every time 1) as when launcing a terminal i thought i was logging in as the current user and 2) since on .bash_profile .bash_rc is loaded if exists... Anyway maybe I should read a bit further on that...

---

