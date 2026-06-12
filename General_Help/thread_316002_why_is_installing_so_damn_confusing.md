---
title: "why is installing so damn confusing?"
date: 2006-12-10
forum: General Help
---

### Post by Tekovro on 2006-12-10
i just want to install deluge. i put in some commands in the terminal but i always get errors. someone said installing stuff was easy. not to me!

Running Ubuntu Edgy on AMD

---

### Post by Iarwain ben-adar on 2006-12-10
Well, 
it would help if you posted the errors ;)


Iarwain

---

### Post by Tekovro on 2006-12-10
bash: deb: command not found

---

### Post by Iarwain ben-adar on 2006-12-10
And what did you enter in the terminal?

Could you just post from the beginning? (eg. once you enter the command, untill you get no more errors)


Iarwain

---

### Post by aysiu on 2006-12-10
If you're using Feisty and have the Universe repositories enabled, you can install it with one command: ```
sudo aptitude update && sudo aptitude install deluge-torrent
```

---

### Post by Tekovro on 2006-12-10
i said i was on edgy and i typed in this 

```
deb http://deluge.mynimalistic.net/apt edgy main
```

dont worry i figured it out!

---

### Post by Iarwain ben-adar on 2006-12-10
Great! :D

Just as a help for others, could you post how you solved your problem?


Iarwain

---

### Post by haxer on 2006-12-10
Confusing? May it be any easyier to install an os as in *buntu:-k

---

### Post by Ramses de Norre on 2006-12-10
> **Iarwain ben-adar said:**
> Great! :D

Just as a help for others, could you post how you solved your problem?


Iarwain

He probably found out that he had to paste that line in /etc/apt/sources.list and then use apt-get/aptitude/synaptic to install the program.

---

