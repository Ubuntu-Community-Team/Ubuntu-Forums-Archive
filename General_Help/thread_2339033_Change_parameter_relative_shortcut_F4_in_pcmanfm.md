---
title: "Change parameter relative shortcut F4 in pcmanfm"
date: 2016-10-04
forum: General Help
---

### Post by sed_faster on 2016-10-04
Hello folks,

I uninstall lxterminal in Lubuntu 16.04 LTS and replaces the "Terminator". When I press F4, in pcmanfm (file manager), I receive this message:
```

Failed to execute child process "lxterminal" (No such file or directory)

```
because the shortcut didn't find the program lxterminal! How can I change this parameter? I need do this through terminal, command line!

Thanks

---

### Post by CantankRus on 2016-10-04
Set terminator as your default x-terminal-emulator.
In terminal....
```
sudo update-alternatives --set x-terminal-emulator /usr/bin/terminator
```
...and check your pcmanfm preferences are as in pic.

---

### Post by sed_faster on 2016-10-04
Thanks for help.
But the command didn't change the parameter in preferences in pcmanfm! I needed did this on hand!

---

### Post by CantankRus on 2016-10-04
What does the preference in pcmanfm show you.
The command only changes the system x-terminal-emulator, not the pcmanfm preference which should be as in 
the pic I posted...
```
x-terminal-emulator %s
```

---

### Post by sed_faster on 2016-10-04
The command didn't result anything!
Hooo, I thought which was possible changed this preference of the pcmanfm through terminal.

But thanks for your help

---

