---
title: "Missing utility in 12.04"
date: 2012-10-21
forum: General Help
---

### Post by wbg45 on 2012-10-21
I just upgraded to 64-bit 12.04, on an AMD 4-core.

Imagine my surprise to note that apparently the "alias"
utility is no longer in  /etc where I would have expected to find it.
A substantive search does not produce it anywhere else, either.

Synaptic hasn't heard of it either, apparently.

I've  always thought of this as a common *ix utility.

Why has this been left out?  And what's the workaround if any?

Thanks,


Brewster

---

### Post by efflandt on 2012-10-21
Not sure what you mean by alias "utility".  Bash has alias, which you can set in your ~/.bashrc, which gives some examples:
```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
    alias mc='minecraft'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
```

Or if you want a command to have a different name, you could use symlinks (ln -s), which you could put in your ~/bin, which if you have not created it yet would end up in your $PATH after you log out and log back in.  If you want to put symlinks in system paths, you would need to use sudo to do that as root.

---

