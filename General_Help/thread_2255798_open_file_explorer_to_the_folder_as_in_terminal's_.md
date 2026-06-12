---
title: "open file explorer to the folder as in terminal's pwd"
date: 2014-12-07
forum: General Help
---

### Post by IAMTubby on 2014-12-07
Hello,
 Say, I'm working at the terminal on a particular directory. Is it possible to open the graphical file explorer to the same folder by running a command on the terminal?

Thanks.

---

### Post by qamelian on 2014-12-07
In the terminal, you can enter:
```
(nautilus $PWD &)
```
This tells nautilus to open in the directory currently stored in the $PWD environment variable. It also releases the terminal so you can continue working in it as well. The $PWD environment variable will always contains the same value that would be returned by the pwd command.

---

### Post by Vaphell on 2014-12-07
*nautilus .* should be enough, $PWD and . point to the same thing and that & voodoo is not necessary because *nautilus* run in cli seems to spin off another independent instance and die instantly, leaving the command prompt usable for the user.

---

### Post by nerdtron on 2014-12-07
Ubuntu
```
 nautilus .
```
Xubuntu
```
 thunar . 
```

Confirmed :)

---

### Post by IAMTubby on 2014-12-07
> **qamelian said:**
> In the terminal, you can enter:
```
(nautilus $PWD &)
```
Thanks qamelian, but why do we have to run it in the background?

> **Vaphell said:**
> *nautilus .* should be enough
Thanks Vaphell.

> **nerdtron said:**
> Confirmed :)
Thanks nerdtron.

---

