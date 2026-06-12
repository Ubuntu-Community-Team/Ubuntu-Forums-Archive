---
title: "Shell autocomplete for apt-get"
date: 2007-10-21
forum: General Help
---

### Post by neko18 on 2007-10-21
In Ubuntu 7.04 I could type
```
apt-get install python-pyga<TAB>
```
and it would output
```
apt-get install python-pygame
```

If I type that in Ubuntu 7.10, it doesn't do anything and leaves the command at
```
apt-get install python-pyga
```

Is there a way to re-enable 7.04's behavior?

---

### Post by kelbizzle on 2007-10-21
Thats because there isn't a package by that name. If you type...
```
sudo apt-get install pythong-ga [TAB][TAB]
```

It will show you every commant you could finish the rest with. If that doesn't happen then there may be another underlying issue. autocomplete works fine for me in gutsy.

---

### Post by MRiGnS on 2007-10-21
actually the package exists.

There is a problem with the bash-completion being disabled.

```
gksudo gedit /etc/bash.bashrc
```

the line may be commented, so you have to delete the '#' in front of the lines.

```
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

like this.


after that just type 'bash' (without the quotes) to reload the shell, or just restart your terminal-emulator application.

---

### Post by neko18 on 2007-10-22
Thanks MRiGnS, that worked perfectly.

---

