---
title: "Setting HDD writting permission"
date: 2008-03-01
forum: General Help
---

### Post by Askalton on 2008-03-01
I just installed ubuntu on my desktop which has two HDD. I set the 1st HDD with / mount point and the other as /media/Dados (so it appears on the desktop) But i can't save a single file on the HDD. I got a command on the IRC ubuntu chat but it has been a long time and i forgot the command :/ could anyone tell me the command to have full access to the ABC folder? :) ty

---

### Post by taurus on 2008-03-01
What filesystem is /media/Dados?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Glaxed on 2008-03-01
perhaps;
```

mount /media/Dados

```
?
edit: Sorry, didnt see previous post, dont go by what I say.

---

### Post by Askalton on 2008-03-01
> **Glaxed said:**
> perhaps;
```

mount /media/Dados

```
?
edit: Sorry, didnt see previous post, dont go by what I say.

the HDD is mounted. It was a simple command but i dont recall it. The File system is ext3 IIRC but cant be sure.

---

### Post by Askalton on 2008-03-01
Ill try those commands once it finishes installing. Seems one of the HDD is dying so it fails during install sometimes. Strangely never had probs when installing XP :P

---

