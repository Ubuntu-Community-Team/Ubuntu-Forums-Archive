---
title: "Share aliases between users"
date: 2006-07-18
forum: General Help
---

### Post by glinsvad on 2006-07-18
I need to share a list of aliases between various users (including root), but so far the only thing that has worked for me is editing ~/.bashrc to uncomment the following lines:
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
... and creating the file ~./bash_aliases containing the aliases.

However doing this with many users is really tiresom, especially because it is the exact same aliases for all users.

If heard mention of a universal /etc/bash_aliases but it does not exist on my system and if I move my aliases to this filename nothing happens.

Do I edit some universal bashrc-file like i edited ~/.bashrc? I know there is a /etc/bash.bashrc but it doesn't contain any mention of aliases anywhere... is this the file? Can I just add the formentioned code with /etc/bash_aliases as the filename?

---

### Post by glinsvad on 2006-07-18
Yes I can. It works!

Please feel free to comment if editing /etc/bash.bashrc this way is a bad idear...

---

