---
title: "Gnome-terminal in Ubuntu"
date: 2005-06-01
forum: General Help
---

### Post by redflyingpig on 2005-06-01
Hi, all, I'm a beginner of Ubuntu. I find that the gnome-terminal in Ubuntu doesn't read the .bash_profile when initialized, thus several programs won't start correctly, while text-mode and Eterm work fine. What might be the reason for this? ](*,)

---

### Post by Leif on 2005-06-01
Try using .bashrc instead.

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=redflyingpig]Hi, all, I'm a beginner of Ubuntu. I find that the gnome-terminal in Ubuntu doesn't read the .bash_profile when initialized, thus several programs won't start correctly, while text-mode and Eterm work fine. What might be the reason for this? ](*,)[/QUOTE]
 According to manual page,

When  an  interactive shell that is not a login shell is started, bash
reads and executes commands from ~/.bashrc, if that file exists.

It is not supposed to read .bash_profile (it is only used at login!)

---

### Post by garlito on 2005-06-01
You may go to Edit -> Current profile -> Title and command -> Run a custom command ...

And type: bash --login

Bye

---

### Post by redflyingpig on 2005-06-01
Yeah, that works, thanks a lot.

---

