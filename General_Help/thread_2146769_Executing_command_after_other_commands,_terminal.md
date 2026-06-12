---
title: "Executing command after other commands, terminal"
date: 2013-05-19
forum: General Help
---

### Post by mjkaufer on 2013-05-19
Hi,
I'm wondering if there's a way for a command to be executed each time another command is executed. For instance, if I execute "mkdir hello", something would happen, and the same thing would happen if I were to do "cp alpha.txt bravo.txt". Could I make it, for instance, such that it would "echo hi" everytime I run a command? Perhaps in .bashrc?
Please let me know if this is possible and how to do so.
Thanks.

---

### Post by fj401971 on 2013-05-19
I know you can create aliases in your .bashrc file.  They are basically creating a shortcut for the command you enter.  Some common aliases already used by Ubuntu are: " alias grep='grep --color=auto'.

I know this not exactly what you asked, but perhaps you can make it work for your scenario.

---

### Post by Nolix on 2013-05-19
f you want to run multiple commands in the terminal respectively, just add a semicolon between two commands. For example:
```
command1; command2; command3;
```

If you want to run multiple commands in the condition that the previous  command must complete successfully first before running the next command  ( in other word, if the first command returns to error, the next  commands wont be executed), 2 and symbols (&&) will be used in  lieu of the semicolon. For example:
```
command1 && command2 && command3
```

If you want to run multiple commands in the condition that the next  command will be executed if the previous one fails ( if the first  command runs successfully, the next commands wont be run), the syntax  will be:
```
command1 || command 2 || command3
```

---

### Post by mjkaufer on 2013-05-19
Thanks for your response. However, I'd like it to work as more of a background process.

---

### Post by dayid on 2013-05-19
This is a very simple hack to accomplish what I believe you are asking for. Giving a better idea of what you are attempting to accomplish will allow for better suggestions.
```

#!/bin/shwhile true; do
    echo -n "Enter command: "
    read command;
    $command;
    echo "hi";
done

```

---

