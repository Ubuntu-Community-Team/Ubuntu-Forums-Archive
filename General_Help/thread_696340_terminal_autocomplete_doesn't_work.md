---
title: "terminal autocomplete doesn't work"
date: 2008-02-13
forum: General Help
---

### Post by plr4ever on 2008-02-13
I have this small but EXTREMELY annoying problem of the tab-autocompletion not working with apt-get in the terminal. I use it a lot to install programs and related packages, but now i need to know the specific name instead of tabbing to see what i can type. 

I am fairly sure if this contains the problem, but i have NO clue what to or if this is the problem at all. My bash_autocompletion file is attached.

---

### Post by Anduu on 2008-02-14
I ran into this problem a while ago.Not sure how or why it happened but I noticed that other users autocompletion still worked so I just replaced my /home/<username>/.bashrc with a working one and all was well.

---

### Post by plr4ever on 2008-02-14
> **Anduu said:**
> I ran into this problem a while ago.Not sure how or why it happened but I noticed that other users autocompletion still worked so I just replaced my /home/<username>/.bashrc with a working one and all was well.

Sounds good, but where did you get the new bashrc file?

---

### Post by farruinn on 2008-02-14
A couple options:

1. check /etc/bashrc - not sure if autocomplete will be turned on there though

2. create a new user and copy over their bashrc

3. read some documentation and find out where new accounts get their bashrc

---

### Post by Anduu on 2008-02-14
I just grabbed a copy from root's home directory.

---

