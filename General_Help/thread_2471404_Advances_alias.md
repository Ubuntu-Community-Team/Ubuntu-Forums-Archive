---
title: "Advances alias"
date: 2022-01-29
forum: General Help
---

### Post by w202mg on 2022-01-29
Good day,
I'm about to optimise my aliases. What I want to do is to consider a parameter in one of the multiple commands in an alias.

Example for input: remove **nginx**
Example of output: sudo apt-get remove --purge **nginx** -y && sudo apt-get autoremove -y

In this particular example **nginx **would be the parameter mean.

Thank you!

---

### Post by Holger_Gehrke on 2022-01-29
From 'man bash', section 'ALIASES':
> 
There is no mechanism for using arguments in the replacement text.  If arguments are needed, a shell function should be used (see FUNCTIONS below).


So no, you can't use an alias in the way you want but you can define a function:

```

function remove () 
{
sudo apt-get remove $1 -y && sudo apt-get autoremove -y
}

```

Holger

---

### Post by dragonfly41 on 2022-01-29
I found this ..

[https://askubuntu.com/questions/847753/list-or-remove-terminal-aliases](https://askubuntu.com/questions/847753/list-or-remove-terminal-aliases)

---

### Post by KBar on 2022-01-29
> [FONT=courier new]Aliases allow a string to be substituted for a word when it is used as the first word of a simple command.[/FONT]

**bash**(1)

---

### Post by &amp;KyT$0P# on 2022-01-29
> **w202mg said:**
> Example for input: remove **nginx**
Example of output: sudo apt-get remove --purge **nginx** -y && sudo apt-get autoremove -y

In this particular example **nginx **would be the parameter mean.

In this particular example, you could do
```
alias remove='sudo apt-get --autoremove -y purge'
```

---

