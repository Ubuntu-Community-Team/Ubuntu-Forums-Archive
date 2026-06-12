---
title: "Gnome-terminal broken"
date: 2008-01-01
forum: General Help
---

### Post by scubanator87 on 2008-01-01
For some reason gnome-terminal has stopped coloring all my directories, executables, etc... I have tried editing the current profile and using different color schemes but nothing so far.

The other problem its now having is that my auto complete [Tab] is not functioning as it used to. e.g. before i could do sudo apt-get in[tab] and it would auto complete the install how ever now it will only auto complete the first argument unless the second argument is a location e.g. gedit /etc/apt/sources.list

Any ideas?

---

### Post by mmb1 on 2008-01-01
You may just have to reinstall through synaptic, or you could try a new terminal program, like konsole.

---

### Post by Tenken on 2008-01-01
Try to open xterm, (Alt+F2, then type xterm) if it also isn't displaying colors either it is probably a problem with your bash profile. Add this line to the .bashrc file in your home folder.

```
alias ls='ls --color=auto'
```

---

### Post by scubanator87 on 2008-01-01
it seems that the .bashrc was missing from my home dir form some reason. I just created another user and stole that one :-D 

That fixed both problems. I think i might actually check out why i can do multi auto complete with regular users but not root and add it to root so when i sudo su  i can administer with less typos

Thanks for your tips!

---

