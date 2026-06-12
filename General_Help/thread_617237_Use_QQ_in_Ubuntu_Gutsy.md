---
title: "Use QQ in Ubuntu Gutsy"
date: 2007-11-19
forum: General Help
---

### Post by 7chaos on 2007-11-19
Does anyone know how Tencent QQ (an IM software in China) can be used in Ubuntu Gutsy?

---

### Post by daengbo on 2007-11-19
I don't have your answer, but I'll chime in that I hate these little one-off IM clients that use their own protocols. I have to deal with "Cool Messenger" for my school in Korea. Geez. They should get a Jabber server and be done with it.

Have you tried running it under Wine? I "solved" my Cool Messenger woes by running an entire Windows XP virtual machine for it. What a waste of 350MB of RAM.

---

### Post by sethvath on 2007-11-19
Pidgin supports QQ, try it out before trying to install the standalone client in wine.

---

### Post by por100pre1 on 2007-11-19
Use Eva, it works fine in Gutsy. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo aptitude install eva
```

---

### Post by Sef on 2007-11-19
First, type this command:

```
sudo apt-get update
```

then type in 

```
sudo aptitude install eva
```

---

### Post by 7chaos on 2007-11-20
thx, it  works, but i cannot type chinese when using the software to chat with my friends...

---

