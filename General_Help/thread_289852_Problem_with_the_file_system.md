---
title: "Problem with the file system"
date: 2006-10-31
forum: General Help
---

### Post by Eleka on 2006-10-31
Hello people.

I'm using Ubuntu Edgy on my laptop. I have my filesystem /dev/sda2 mounted on "/".

Now, when I try to create dirs or files on any location in /dev/sda2 partition, I can't. I do it with sudo and get no error messages, but it don't create anything.

I test creating dirs and files, with "sudo nano /a.test" or "sudo mkdir /a" and it looks like work, because don't prompt me any error message, but it don't creat anything.

My /dev/sda2 is mounted with rw permissions ... what is happening?

---

### Post by matthewstory on 2006-10-31
please post your /etc/fstab file up here so we can take a gander at it.

---

### Post by Eleka on 2006-10-31
Sorry! I can't post before. I have found the solution. I installed stow and tried to add myself to the group "staff" ... but I broke my groups and only have staff, don't admin, my group .... and then, sudo don't works because I wasn't in admin group.

Thanks

P.S. Excuse my bad english

---

### Post by David Corrales on 2006-10-31
Eleka, yo diría que arranque el sistema en recovery-mode para quedar así, en la consola como root y arreglar los problemas de grupos/usuarios. Una vez que esto esté listo, es cuestión de reiniciar (**reboot now**) y ya.

---

