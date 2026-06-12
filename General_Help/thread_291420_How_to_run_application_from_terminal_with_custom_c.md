---
title: "How to run application from terminal with custom command"
date: 2006-11-02
forum: General Help
---

### Post by amanita on 2006-11-02
Hi, I was wandering how to set it up if I want to run application from terminal with custom command. 
E.g. I want to write stel + enter to run stellarium. Also how to generally find executable file of that application ? :-k

---

### Post by Ramses de Norre on 2006-11-02
Find executable:```
which stellarium
```

To change the name: make an alias for it, in ~/.bashrc uncomment these lines:```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```
Then make ~/.bash_aliases and put this inside:```
alias stel='stellarium'
```

You'll need to restart bash then, it sometimes work when you run "bash" but to be sure log off and back on.

---

### Post by closer9 on 2006-11-02
You can also do this with symbolic links.

Assuming that stellarium is in /usr/bin/:
```
sudo ln -s /usr/bin/stellarium /usr/bin/stel
```

---

### Post by amanita on 2006-11-03
Awesome, cheers guys :cool:

---

