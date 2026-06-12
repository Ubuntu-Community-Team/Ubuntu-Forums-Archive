---
title: "why no tab completion after sudo?"
date: 2005-10-31
forum: General Help
---

### Post by jnoreiko on 2005-10-31
Why doesn't tab completion work after sudo in Terminal?
Eg, I type "sudo chm" and hit tab. I'd expect it to complete the "chmod", but it doesn't.

---

### Post by stuporglue on 2005-10-31
I wish it tab completed too. 

I think the reason is that you're not actually running the command chmod. At least, you're not running it directly. You're actually running the command "sudo", with an argument of chmod. I'm pretty sure that the shell sees chmod in the same way it sees the -l flag, or any other flag, when you run the command ls. 

ie. 
$ ls -l  # has no tab completion for the -l part
$ sudo chmod # has no tab completion for the chmod part

That's my guess.

---

### Post by Pablo_Escobar on 2005-10-31
There is a way to auto complete:
Under /etc there is a bash.profile (as I recall, I 2 hours I'll be on my U box so I'll verify).
You need to comment out 3 last lines (It says about dynamic auto complete - works like a charm).

---

### Post by Pablo_Escobar on 2005-10-31
I'm on my Ubuntu box now and it's EASY !! :)

sudo gedit /etc/bash.bashrc

At the end of file you'll find :
> # enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi 

Change it to :

> # enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

REBOOT AND PRESTO MAGICO :)

---

### Post by nagilum on 2005-10-31
[QUOTE=Pablo_Escobar]REBOOT AND PRESTO MAGICO :)[/QUOTE]
Uhm, a simple logout / login cycle would also do. Or, even easier, parse the /etc/bash.bashrc while still logged in with "source /etc/bash.bashrc". No need to reboot. ;)

---

### Post by beefsprocket on 2005-10-31
[quote=Pablo_Escobar]REBOOT AND PRESTO MAGICO :)[/quote]

Just exit your terminal and start a new one. No rebooting necessary (on KDE anyways).

---

### Post by Pablo_Escobar on 2005-10-31
HEH !! Some of M$ style has been left in me :D

---

### Post by jnoreiko on 2005-10-31
[QUOTE=Pablo_Escobar]
sudo gedit /etc/bash.bashrc[/QUOTE]

The same lines are in your personal .bashrc
I would go with editing those, because then it's in your home & it can't get overwritten by upgrades etc. Just a bit cleaner :)

Anyway, either way works a treat.
Thanks! :)

---

### Post by doc_holiday on 2005-10-31
This is great!!

---

### Post by jasay on 2005-10-31
Hey thanks for the tip.:D

---

