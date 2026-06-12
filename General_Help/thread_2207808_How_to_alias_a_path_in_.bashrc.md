---
title: "How to alias a path in .bashrc"
date: 2014-02-25
forum: General Help
---

### Post by iums1 on 2014-02-25
I want to create an alias like this in my .bashrc

```
alias trash="~/.local/share/Trash/files"
```

in order to use the aliased location like this

```
mv trash
```

but it doesn't work. How can i achieve this?

---

### Post by Dennis N on 2014-02-25
An alias must use a command. It cannot just represent a string.

Correct usage:
```
dmn@Sydney:~$ alias greeting='echo "how are you today?" '
dmn@Sydney:~$ greeting
how are you today?

```
Incorrect usage:
```
dmn@Sydney:~$ alias photos="~/Pictures"
dmn@Sydney:~$ cd photos
bash: cd: photos: No such file or directory
```

---

### Post by bluefrog on 2014-02-25
have a look in .bashrc to see what is an alias.

you don't need an alias to delete things in command line. use rm.

you can use functions to ease your life. put those functions in bashrc or bash_aliases

---

### Post by Vaphell on 2014-02-25
that won't work, aliases match only beginning of the line
alias xxx=yyy
xxx something <- this will substitute alias
something xxx <- this won't

you might try:
- using a custom variable
```
trash=~/.local/share/Trash/files
mv ... $trash
```

- creating a symlink to ~/.local/share/Trash/files in ~
```
ln -s ~/.local/share/Trash/files ~/trash
mv ... ~/trash
```

- creating a custom function
```
mvt() { mv -t ~/.local/share/Trash/files -- "$@"; }
mvt <files>
```

i'd go with a function

---

