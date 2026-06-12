---
title: "Change coloring in mate terminal"
date: 2019-02-25
forum: General Help
---

### Post by raleigh3 on 2019-02-25
I use mate terminal.

When a do a ls, it shows the listing in colors which sometime are hard to read. 

Especially if you have customized the fg and bg colors.

Can I disable the "colorizing." ?

---

### Post by Impavidus on 2019-02-26
You can. Create an alias for ls with the option "--color=never". Maybe you already have an alias for a color option for ls. Check with **alias**:```
$ alias
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
```These are some default aliases, although I don't know if they're still automatically created in the latest release of Ubuntu. These aliases are defined in .bashrc:```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

---

