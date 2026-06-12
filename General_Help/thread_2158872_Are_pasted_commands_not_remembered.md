---
title: "Are pasted commands not remembered?"
date: 2013-07-01
forum: General Help
---

### Post by vasa1 on 2013-07-01
I'm using Lubuntu 13.04 which comes with lxterminal.

I get the impression that if I paste a command into lxterminal and run it by hitting enter and then subsequently close lxterminal (all instances), this command is not available (by using the up arrow) when I restart lxterminal.

If I type in the command, there's no problem in reusing the command later on with the up arrow.

I also don't see the pasted command in .bash_history.

---

### Post by sudodus on 2013-07-01
This is strange, probably a bug. What happens if you run

```
sync
```

before closing the terminal window?

---

### Post by sudodus on 2013-07-01
I checked, and is *not* like that for me in an installed instance of Raring 32-bit.

What  I have noticed is that if I reboot or poweroff from a terminal window,  the last session's commands will not be saved unless I sync before. I'm not sure if it is  always or with some particular version, but I have noticed it, so when  you have a similar issue, I want to mention it.

---

### Post by sanderj on 2013-07-01
> **vasa1 said:**
> I'm using Lubuntu 13.04 which comes with lxterminal.

I get the impression that if I paste a command into lxterminal and run it by hitting enter and then subsequently close lxterminal (all instances), this command is not available (by using the up arrow) when I restart lxterminal.

If I type in the command, there's no problem in reusing the command later on with the up arrow.

I also don't see the pasted command in .bash_history.

If there is a space at the beginning of the line, it will not be in history. Could that be the cause?

---

### Post by vasa1 on 2013-07-01
@sanderj, I checked and there is no space at the start.

@sudodus, I think you have something there! If I close the terminal but don't log off, I **can** recall the command. I'll log off and try. Then, I'll also try your sync trick.

---

### Post by vasa1 on 2013-07-01
The command is remembered after a log-out, log-in! I'll try with a shutdown later in the day. Or maybe I just goofed in some way :(

---

### Post by vasa1 on 2013-07-01
@sudodus, can there be any bad effects to running sync in the context you describe?

---

### Post by CaptainMark on 2013-07-01
I've noticed similar behaviour when running two terminals at the same time, I find that only commands entered into one of the two terminals are logged in .bash_history perhaps the first one open get precedence???

---

### Post by vasa1 on 2013-07-01
> **CaptainMark said:**
> I've noticed similar behaviour when running two terminals at the same time, I find that only commands entered into one of the two terminals are logged in .bash_history perhaps the first one open get precedence???
That's interesting!
Meanwhile, just with the one terminal open, I couldn't reproduce my complaint even after a restart. So it's possible that having two terminals open had something to do with it. And then it shouldn't be just pasted commands but any command. But that should be easy to check.

---

### Post by sudodus on 2013-07-01
> **vasa1 said:**
> @sudodus, can there be any bad effects to running sync in the context you describe?
No, sync means to write buffers to disk now (instead of waiting until the system thinks it has time for it), so it should have no bad effect. In this case it should write the history to to /.bash_history.

---

### Post by sudodus on 2013-07-01
> **CaptainMark said:**
> I've noticed similar behaviour when running two terminals at the same time, I find that only commands entered into one of the two terminals are logged in .bash_history perhaps the first one open get precedence???

I think this happens: There is only on file to save the commands, ~/.bash_history. And the latest exit from a terminal window will write the history of that window (and overwriting any history from other windows that you closed before). So if you want to keep the history of a particular window, close the other ones before.

---

