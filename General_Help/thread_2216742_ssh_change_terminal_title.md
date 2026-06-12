---
title: "ssh change terminal title"
date: 2014-04-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-04-13
How does the ssh-server change the title bar? clearly it is not done client side since it does not work on all of my terminal windows
[[IMG]http://www.zimagez.com/miniature/screenshot-04132014-032718pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-04132014-032718pm.php")
when i have 3+ windows it drives me nuts looking for the right one

---

### Post by steeldriver on 2014-04-13
It's set by an escape sequence from the shell that's running inside the terminal, I think. In bash, that's usually done by embedding the sequence as part of the PS1 terminal prompt (so that it updates with the user@host:/pwd information) but you can send the escape sequence manually 

e.g. here is the default bash PS1 (defined in ~/.bashrc):

```

\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$

```

IIRC the \e]0; part is what sends the PS1 contents to the terminal title string (you may also see it as \033]0; with octal 33 being equivalent to the \e escape sequence).

You can play with it by sending various alternate strings however bear in mind that the window title may not appear to change unless you disable the PS1 from overwriting your changes everytime you hit enter e.g.

```

steeldriver@think60p:~/Documents$ PSbak="$PS1"
steeldriver@think60p:~/Documents$ PS1="$ "
$
$ echo -ne "\033]0;new window title\007"

```
(window title changes at this point - even PuTTY on Windows respects the instruction); then
```

$ PS1="$PSbak"
steeldriver@think60p:~/Documents$

```
(window title reverts to the same as the prompt)

---

### Post by pqwoerituytrueiwoq on 2014-04-13
thanks
```
cat .profile 
export PS1="\[\e]0;\u@\h: \w\a\]$PS1"
```

---

