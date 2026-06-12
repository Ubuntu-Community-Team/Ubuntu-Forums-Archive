---
title: "Terminals command problem"
date: 2008-04-26
forum: General Help
---

### Post by Benjaminang on 2008-04-26
i wonder anyone can help me here, noob linux here.. having some trouble with the terminal command.

i cant seems to able to enter my desktop under /home/USERNAME 

USERNAME@USRNAME-Ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
USERNAME@USERNAME-Ubuntu:~$ 

i've tried cd /home/benjamin/desktop no luck also, but i can access the folder i created myself.. i wonder is there anythngy i done wrong?

i've been trying to enter my desktop folder for days, hope any experts here can lighten me abit.. thanks~!!

---

### Post by AaronMT on 2008-04-26
Post the output of **ls**

---

### Post by Monicker on 2008-04-26
It should be Desktop and not desktop.  Its case sensitive.

---

### Post by Perpetual on 2008-04-26
> **Benjaminang said:**
> i wonder anyone can help me here, noob linux here.. having some trouble with the terminal command.

i cant seems to able to enter my desktop under /home/USERNAME 

USERNAME@USRNAME-Ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
USERNAME@USERNAME-Ubuntu:~$ 

i've tried cd /home/benjamin/desktop no luck also, but i can access the folder i created myself.. i wonder is there anythngy i done wrong?

i've been trying to enter my desktop folder for days, hope any experts here can lighten me abit.. thanks~!!

It's ```
cd Desktop
```

Linux is case sensitive.  desktop and Desktop to Linux are two different locations.  In your case, desktop does not exist.

Edit: too slow :)

---

### Post by Benjaminang on 2008-04-26
okay.. its the fre@kin sensitive case problem.. d*mn..y i never thought of that..thanks!! it got me scratching my head for days..just move from xp, wanna try somethngy diff..

---

