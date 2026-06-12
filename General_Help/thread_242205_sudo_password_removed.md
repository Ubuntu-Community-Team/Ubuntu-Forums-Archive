---
title: "sudo password removed"
date: 2006-08-23
forum: General Help
---

### Post by chiflito on 2006-08-23
i hope my ignorance is not too disturbing; for some reason sudo stopped demanding my password for permission to access sudo in a terminal or even to access such programs as the package manager or system controller. i am confused and afraid it may represent a security risk. my question: how can i get sudo to once again require my password for any use of administrative rights? thank you in advance for any support.

---

### Post by abelthorne on 2006-08-23
When you use sudo and enter your password, you won't be prompted for it again until 15 minutes have passed.
Is it what is happening ?

---

### Post by bigken on 2006-08-23
you could try **sudo passwd** in the terminal its worth a try ;)

---

### Post by chiflito on 2006-08-23
thank you for quick responses. :D 

first, it is not a question of having used sudo within 15 minutes; no matter when i want to do something it is the same thing -- easy access, no password required. 

haven seen the proposal of changing the password that is what i tried. nothing changed, so i then gave the command sudo -k and then tried it again. still, i could access any program that should require administrative rights.

---

