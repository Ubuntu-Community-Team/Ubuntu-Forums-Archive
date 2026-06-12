---
title: "Terminal/Shell showing location on each line"
date: 2013-02-18
forum: General Help
---

### Post by lordbux on 2013-02-18
I was editing my .vimrc file when my vim suddenly crashed, then on my terminal is acting strangely 

On eproblem is that it is printing current location abow the command input:
as in:
```
~
auditor@NightHwack$  cd /usr/share/
/usr/share
auditor@NightHwack$
```

instead of
```
auditor@NightHwack:/usr/share/$
```
As is used to show before.

Also som other settings seem to have chnaged. 
I first thought this is an issue with the gnome terminal but then noticed same issue on konsole and terminator. 
I tried Ctrl+Alt+F3 to access the shell and there too this issue is reflected along with strange colorschemes.

Please help me correct this.

Using : ubuntu 12.04 lucid

---

### Post by schragge on 2013-02-18
What does PS1 contain?
```

echo $PS1

```

---

### Post by lordbux on 2013-02-18
> **schragge said:**
> What does PS1 contain?
```

echo $PS1

```

it contain
```
\[\e]0;\u@\h: \w\a\]\[\033[01;31m\]\w\[\033[00m\]\n${debian_chroot:+($debian_chroot)}\[\033[01;34m\]\u\[\033[01;32m\]@\[\033[01;34m\]\h\[\033[00m\]\$ $(parse_git_branch)$(parse_svn_branch)

```

---

### Post by schragge on 2013-02-18
Well, there [color=red]is[/color] newline in your prompt
```

\[\e]0;\u@\h: \w\a\]\[\033[01;31m\]\w\[\033[00m\][color=red]\n[/color]${debian_chroot:+($debian_chroot)}\[\033[01;34m\]\u\[\033[01;32m\]@\[\033[01;34m\]\h\[\033[00m\]\$ $(parse_git_branch)$(parse_svn_branch)

```

---

### Post by lordbux on 2013-02-18
> **schragge said:**
> Well, there [color=red]is[/color] newline in your prompt
```

\[\e]0;\u@\h: \w\a\]\[\033[01;31m\]\w\[\033[00m\][color=red]\n[/color]${debian_chroot:+($debian_chroot)}\[\033[01;34m\]\u\[\033[01;32m\]@\[\033[01;34m\]\h\[\033[00m\]\$ $(parse_git_branch)$(parse_svn_branch)

```

how can I correct it

---

### Post by Impavidus on 2013-02-18
You can change the prompt by editing your .bashrc file. In there the variable PS1 is defined. In my case it looks like```

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

```which is, if I'm not mistaken, the default.

---

### Post by schragge on 2013-02-18
Where does your PS1 get defined? In *~/.bashrc*? If you don't know, try
```

grep -rw PS1= ~ /etc

```
Then open the file and edit PS1 (remove \n from its value).

---

