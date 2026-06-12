---
title: "Why can't I add this to my PATH?"
date: 2007-04-05
forum: General Help
---

### Post by Kalixa on 2007-04-05
Hello. I am trying to add a folder to my PATH so I can always execute my scripts instead of navigating to the folder where they are located. After typing:

export PATH=$PATH:/home/myname/Scripts

in the command line it worked fine. So I thought I would add it to my .bash_profile. But it doesn't work when I add the exact some line to my .bash_profile. Why is that?

---

### Post by WW on 2007-04-05
Add it to **.bashrc**.

---

### Post by Kalixa on 2007-04-05
> **WW said:**
> Add it to **.bashrc**.

I tried that too. That still doesn't help. Any other suggestions?

---

### Post by raptor2552 on 2007-04-05
Put this as the last line of .bashrc
PATH=/home/myname/Scripts:"${PATH}"

"${PATH}" protects the text of PATH from being runover by other additions. You may also want to add a . (period) which will execute anything in the directory you're currently in.

Like so: PATH=.:/home/myname/Scripts:"${PATH}"

save the file and then type: . ./.bashrc  to effect the change

It may interest you to know that when adding to your path, directories are searched in the order they appear, put your most used first.

---

### Post by WW on 2007-04-05
The file .bashrc is executed for each *new* terminal that you start.  If you also want the definition changed in the current terminal, you can either give the appropriate export command in that terminal, or execute .bashrc after you change it, as raptor2552 suggests.

---

