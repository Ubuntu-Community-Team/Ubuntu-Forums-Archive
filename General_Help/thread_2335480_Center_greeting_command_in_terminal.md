---
title: "Center greeting command in terminal"
date: 2016-08-29
forum: General Help
---

### Post by SnuKies on 2016-08-29
[COLOR=#111111][FONT=Ubuntu]Hello
I've recently added a greeting message (something like 'Hello Alex!') in ~/.bashsrc file. Now everytime I open a terminal, this command will appear first.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My question is : How do I make to center the command, no matter if my terminal is maximized or not?[/FONT][/COLOR]

---

### Post by steeldriver on 2016-08-29
Deja vu ;)

One fairly crude way would be to print the string in a *field width* that uses the value of the terminal's `COLUMNS` variable e.g.

```

user@pc:~$ str='Hello Alex!'
user@pc:~$ printf '%*s\n' $(( (COLUMNS+${#str})/2 )) "$str"
                                  Hello Alex!
user@pc:~$

```

OTOH you could do fancier stuff with one of the available "banner" packages such as 'figlet':

```

user@pc:~$ figlet -c "$str"
                  _   _      _ _            _    _           _
                 | | | | ___| | | ___      / \  | | _____  _| |
                 | |_| |/ _ \ | |/ _ \    / _ \ | |/ _ \ \/ / |
                 |  _  |  __/ | | (_) |  / ___ \| |  __/>  <|_|
                 |_| |_|\___|_|_|\___/  /_/   \_\_|\___/_/\_(_)

```

See [http://askubuntu.com/questions/818145/ubuntu-16-04-center-greeting-command-in-terminal](http://askubuntu.com/questions/818145/ubuntu-16-04-center-greeting-command-in-terminal)

---

