---
title: "Unable to login to account"
date: 2012-11-18
forum: General Help
---

### Post by rushikesh988 on 2012-11-18
I was exploring the terminal commands and I executed this command in the terminal
> sudo startx

after that the desktop without unity started so I shutdown my computer from there.

but after reboot I am just unable to login to my account after whenever I insert my password the system just goes blank for few secs shows login screen again.
howeve I am able to login into another accounts (guests) and created the new account as a temp. option.
but please tell me how can I recover my old account...

---

### Post by Wim Sturkenboom on 2012-11-18
I can't help but I wonder why you use sudo in combination with startx? I mean, that way you run your graphical environment as root.

Another question would be if this is a server install? Because usually startx should not be required; ubuntu should take you straight to a graphical environment.

---

### Post by steeldriver on 2012-11-18
Running startx as sudo usually leaves a root-owned .Xauthority file in the user's home dir - which prevents your regular X session from starting up

If you can log in to one of the non-graphical virtual terminals (Ctrl-Alt-F1 and so on) you can probably fix that by removing the offending file

```
$ ls -l ~/.Xauthority
$ rm ~/.Xauthority
```If that doesn't work you can do the same from the recovery console

```
# rm /home/*yourusername*/.Xauthority
```

Sometimes there is a ~/.ICEauthority file that causes similar problems

---

### Post by rushikesh988 on 2012-11-18
> **steeldriver said:**
> Running startx as sudo usually leaves a root-owned .Xauthority file in the user's home dir - which prevents your regular X session from starting up

If you can log in to one of the non-graphical virtual terminals (Ctrl-Alt-F1 and so on) you can probably fix that by removing the offending file

```
$ ls -l ~/.Xauthority
$ rm ~/.Xauthority
```If that doesn't work you can do the same from the recovery console

```
# rm /home/*yourusername*/.Xauthority
```

Sometimes there is a ~/.ICEauthority file that causes similar problems
worked !! 
Thank you so much !!

---

### Post by rushikesh988 on 2012-11-18
> **Wim Sturkenboom said:**
> I can't help but I wonder why you use sudo in combination with startx? I mean, that way you run your graphical environment as root.

Another question would be if this is a server install? Because usually startx should not be required; ubuntu should take you straight to a graphical environment.
As I mentioned I was just exploring

---

