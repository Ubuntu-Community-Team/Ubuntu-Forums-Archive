---
title: "run long string using short-name script"
date: 2013-01-29
forum: General Help
---

### Post by marchelloUA on 2013-01-29
Hi all, 

my need is to run long string 

# program -parameter1 -parameter2 ... -parameterN 

using short-name script. 

I'm new to writing scripts, how do I start?

---

### Post by Impavidus on 2013-01-29
If the parameters are fixed you can use an alias.

Open the file **.bashrc** in a text editor. It's in your home directory, but it's hidden. Check wether the lines```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

``` are present. If they are, then close the file and open **.bash_aliases** in your text editor. If they are not, you can add them and open .bash_aliases, or input the following line directly in .bashrc.

Next put in your .bash_aliases the line```

alias shortname='program -parameter1 -parameter2 ... -parameterN'
```Close your terminal and open a new one and your alias should work.

---

