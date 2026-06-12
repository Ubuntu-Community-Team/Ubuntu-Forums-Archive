---
title: "Scipt to install snap/flatpaks"
date: 2021-11-08
forum: General Help
---

### Post by yaminb on 2021-11-08
Hi all,

Before i go ahead and write it, does anyone know of a script or something that creates the install commands for the list of apps.
Purpose: So if I ever need to reinstall, I have this list of commands saved and ready to go.

Basically, it does a snap list.
Takes the result of that and creates a list of commands
sudo snap install appA
sudo snap install appB
...

Do the same for flatpak

---

### Post by ActionParsnip on 2021-11-08
Something like
```

xargs sudo snap install <packagelist.txt

```

---

### Post by yaminb on 2021-11-08
this would be to create the packagelist.txt

Example:
I have my system running with snaps A, B, C installed
I run the script and it creates the 'packagelist.txt' file
Then I can execute your command to install it '
xargs sudo snap install <packagelist.txt

---

### Post by ActionParsnip on 2021-11-08
To make the list would be:
```

snap list | grep -v Name | awk {'print $1'} > $HOME/packagelist.txt

```
The "grep -v" part removes the top line from the output which labels the columns in the output

---

