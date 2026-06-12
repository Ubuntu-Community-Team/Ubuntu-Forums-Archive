---
title: "Running self-compiled programs easily."
date: 2015-04-30
forum: General Help
---

### Post by kazakore on 2015-04-30
I have just compiled a program called Sonic-Pi [1] not available in the repos but don't want to have to type ~/Downloads/debs/sonic-pi/app/gui/sonic-pi every time I want to run it, but would rather just type sonic-pi into the CLI. I  know there is somewhere you can list commands and what they really mean, I even know there are some set by default (eg I don't believe ls under Ubuntu is just ls but rather has some default arguments such as -c which is set in a file if I remember correctly.) I know this should be something easy to find but I haven't been able to find the right search words to get the answer through Google...

[1] [https://github.com/samaaron/sonic-pi](https://github.com/samaaron/sonic-pi)

EDIT: Alias was the term/command I was looking for.

alias sonic-pi="~/Downloads/debs/sonic-pi/app/gui/sonic-pi"

---

### Post by sudodus on 2015-05-01
You can also create the directory **~/bin** and collect your own programs and scripts in that directory. The next time you boot it will be in your $PATH, and your own programs and scripts will start when you enter the name (without path). So that is another way to get away with writing only

```
sonic-pi
```

to start your program.

I have a **~/bin** directory and I use alias too. I add my ***own aliases*** next to those in **~/.bashrc** to make them persist past reboots.

---

### Post by kazakore on 2015-05-01
Thanks for that sudodus. I didn't realise Alias was per session when I posted so I will use one of those methods to make it persistent :)

EDIT I was almost tempted to clone the whole Github directory/program into ~/bin but I assumed that would be bad practice. Is this generally an ok this to do? If I had done would it have picked up the right files to be executed from the command line easy? For now I've added my own little "script" pointing at its location :)

---

### Post by btindie on 2015-05-01
You could of course just create a sym-link from ~/bin/sonic-pi to the actual file. Then when you update/recompile the binary the new one will be instantly available.
```
ln -sf ~/Downloads/debs/sonic-pi/app/gui/sonic-pi ~/bin/sonic-pi
```
If you don't already have a bin directory in ~/ just do a 'mkdir ~/bin', close your terminal and open a new one and the binary files in there will then be available.
The PATH variable gets updated from ~/.profile when a new shell is created. If the ~/bin directory exists at that time it gets added to your PATH variable, so no need for a reboot!

Regarding aliases, you can create a file called ~/.bash_aliases, if that exists it'll get sourced by ~/.bashrc when a new shell is created.

---

