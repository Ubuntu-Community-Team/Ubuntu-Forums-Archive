---
title: "Colorize text in Ubuntu's terminal for normal user"
date: 2006-10-24
forum: General Help
---

### Post by Ariod on 2006-10-24
Hello,

How come that if I use Ubuntu's terminal as regular user, there's no text coloring (e.g. directories are in different color than executables, etc.), but if I switch to root (by using sudo -i), the terminal starts coloring different files? How to fix this?

---

### Post by phranx on 2006-10-24
try to edit your .bashrc. You can find it in your home dir.
```
sudo nano ~/.bashrc 
```

make sure you have the alias enabled

This is extracted from my .bashrc
```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    **alias ls='ls --color=auto'**
fi

```

---

### Post by Ariod on 2006-10-24
Thanks, that works!

---

