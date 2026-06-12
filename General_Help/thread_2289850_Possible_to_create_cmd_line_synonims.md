---
title: "Possible to create cmd line synonims ?"
date: 2015-08-07
forum: General Help
---

### Post by browser_ice2 on 2015-08-07
Is it possible to do something like below without having to create a shell script for it ?

A) command x -parm xyz ....

B) create a synomim command called  ABC that once I I type this in the cmd line, it will convert it to actualy execute the command in A)

C) this is for one line commands not for multiple line

---

### Post by VMC on 2015-08-07
aliases come to mind. Look under bash.
```
man bash
```

---

### Post by browser_ice2 on 2015-08-07
Thx.  I hadn't done scripting in years and I had totally forgotten about that command.

Thank you.

---

### Post by yetimon_64 on 2015-08-07
> **VMC said:**
> aliases come to mind. Look under bash.
```
man bash
```

+1, exactly bash aliases.

> A) command x -parm xyz ....

B) create a synomim command called  ABC that once I I type this in the  cmd line, it will convert it to actualy execute the command in A)

C) this is for one line commands not for multiple line          

Some I use for updating, I store these and others in a text file at "/home/$USER/.bash_aliases",
> alias agu='sudo apt-get -y update'
alias agg='sudo apt-get -y upgrade'
alias agug='sudo apt-get -y update && sudo apt-get -y upgrade'
alias agdu='sudo apt-get -y dist-upgrade'
alias upd8.full='agug && agdu'
alias ug='sudo update-grub'
alias uirfs='sudo update-initramfs -u'

@ OP note the entry "upd8.full" is an alias that strings two other aliases together etc. Cuts down a lot of typing in the terminal ;)

Edit: just noted mark as solved, :-)

---

### Post by Keith_Helms on 2015-08-07
There are some canned aliases that are provided in the ~/.bashrc file.  As mentioned above, if a .bash_aliases file exists, it will be pulled in.

If you want to get fancier that what you can do in an alias, you can also add a function.  For example, I added the following to the end of my .bashrc file:

```
lsless() {
    ls -Cw 160 --color "$@" | less -r
}
```

I use that function to list directories that would normally scroll off the screen, while still keeping the color and column formatting that I would lose by just doing "ls /dir | less".

---

