---
title: "How do I save an alias?"
date: 2007-08-28
forum: General Help
---

### Post by bone2006 on 2007-08-28
How do you save alias so that they can be used each time you close a terminal?

I was reading to put them in ~/.bash_aliases , but can't seem to find this one.  Any help is appreciated.

---

### Post by jamvegan on 2007-08-28
You can add them at the end of ~/.bashrc, in the form:
```
alias ll="ls -l"
```

---

### Post by bodhi.zazen on 2007-08-28
some people like to keep their aliases in a separate file, in which case you need to add

```
source .bash_aliases
``` in your .bashrc :twisted:

There is also a .bash_profile which I usually add ```
source .bashrc
```

And I skip .bash_alases (I just use .bashrc)

Here is a reference on bash configuration files :

[http://heimhardt.com/htdocs/bashrcs.html](http://heimhardt.com/htdocs/bashrcs.html)

If you want to try something new, try zsh :twisted:

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

The "problem" with zsh is you need a .zshrc : [http://dotfiles.org/~Ryuzaki/.zshrc](http://dotfiles.org/~Ryuzaki/.zshrc)

---

