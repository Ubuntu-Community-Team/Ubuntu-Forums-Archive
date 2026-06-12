---
title: "can't change directory when i am root"
date: 2008-05-11
forum: General Help
---

### Post by dino99 on 2008-05-11
hi all,
i run Hardy and i need to be root to install a driver: so, i do "sudo init 1" and then jockey dialog box appear and i choose "prompt to box"

at this time i try cd /home but it return "no such file or directory"

how to change directory when we are root ?

please give me help

---

### Post by Joeb454 on 2008-05-11
You need to have a terminal open to use the terminal commands :)

From what I gather you don't have a terminal open

---

### Post by jocko on 2008-05-11
> **dino99 said:**
> hi all,
i run Hardy and i need to be root to install a driver: so, i do "sudo init 1" and then jockey dialog box appear and i choose "prompt to box"

at this time i try cd /home but it return "no such file or directory"

how to change directory when we are root ?

please give me help

Where did you type "sudo init 1"?
I have no idea what "jockey dialog box" is or what you mean by "prompt to box".
When you type "sudo init 1" in a terminal, what will happen is that your gnome session and any other user processes will be terminated, you will be logged off and you'll get a single user (root) command line interface. Is that what you get?

---

### Post by ASULutzy on 2008-05-11
There's a big long sticky here somewhere about how you don't ever want to login as root.

You don't need to login as root to install a driver, you simply need to execute it with sudo.

The number of times you actually need to login as root are very very very few and far between, so much so that Ubuntu doesn't technically support it, and in writing how-tos, posters are discouraged from ever instructing someone to login as root. It's just not secure!:lolflag:

---

### Post by jocko on 2008-05-12
> **ASULutzy said:**
> There's a big long sticky here somewhere about how you don't ever want to login as root.

You don't need to login as root to install a driver, you simply need to execute it with sudo.

The number of times you actually need to login as root are very very very few and far between, so much so that Ubuntu doesn't technically support it, and in writing how-tos, posters are discouraged from ever instructing someone to login as root. It's just not secure!:lolflag:
This is NOT the same as enabling a root password, which is what [that sticky]("http://ubuntuforums.org/showthread.php?t=765414") is about (and I fully agree with the sticky, better to teach people the ubuntu way than having them compromise the system integrity/security if it's not necessary).

"sudo init 1" will do exactly what you do by booting up into recovery mode, without enabling any root password.

But, I suspect that the op may be trying to install something the complicated way, when it probably already exists in the repos... so instead of helping him/her to make a beginners mistake, maybe we should ask exactly what he/she's trying to accomplish...
**Dino99:** Are you by any chance trying to install nvidia drivers for your graphics card?

---

