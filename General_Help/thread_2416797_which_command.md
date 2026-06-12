---
title: "which command"
date: 2019-04-15
forum: General Help
---

### Post by Skaperen on 2019-04-15
i have a command set up as a function in bash.  when i was unsure where this command was i did the which command with that command name and it showed nothing.  i eventually found i had set it up as a function.  is there a way, such as a command, to reveal that a given command name is a function?

---

### Post by Impavidus on 2019-04-15
The **type** command should help you.

---

### Post by Skaperen on 2019-04-17
thanks, it works on the function i created to do this:```
lt2a/phil /home/phil 200> type whix
whix is a function
whix () 
{ 
    if [[ -z "$1" ]]; then
        set | egrep '\(\) $';
    else
        which "$1";
        set | egrep '\(\) $' | egrep "$1";
    fi
}
lt2a/phil /home/phil 201>
```

---

