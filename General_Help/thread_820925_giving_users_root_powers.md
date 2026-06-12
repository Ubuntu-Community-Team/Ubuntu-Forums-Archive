---
title: "giving users root powers"
date: 2008-06-06
forum: General Help
---

### Post by pedwards on 2008-06-06
hey all, I need to give 3 users full root powers, due to security reasons we cannot share 1 root account but we all require root powers.  Ive added the users to the sudo group but that seems to not be enough.  I NEED MORE POWER.

---

### Post by Monicker on 2008-06-06
You added them to the admin group in order to be able to run commands with root privileges?

How do they not have enough power?  What difficuly is being encountered?

---

### Post by jocko on 2008-06-06
To be able to get root access through sudo, the user have to be a member of the group "admin".

---

### Post by pedwards on 2008-06-06
solution:  
add users to the sudoers file.

---

### Post by Monicker on 2008-06-07
> **pedwards said:**
> solution:  
add users to the sudoers file.

Adding them to the admin group would have given the same access.

---

### Post by Separ on 2008-06-07
Ok, my first question is why do you need user accounts which have root privileges? Very few things (apart from some installations and configurations of your computer) need to be run as root. If a program is asking you to run it as root, I would be very wary of it if I were you.

Second, why is it such a problem to have everyone use "sudo" to gain temporary root powers?

---

### Post by rampageoberon on 2008-06-07
Best thing would be to add users in the file to only allow root for certain commands rather than the whole system. /etc/sudoers using the command

```
sudo visudo
```

See the guide below

[http://www.ducea.com/2006/05/19/linux-tips-the-proper-way-to-allow-regular-users-to-run-commands-as-root/](http://www.ducea.com/2006/05/19/linux-tips-the-proper-way-to-allow-regular-users-to-run-commands-as-root/)

---

### Post by jocko on 2008-06-07
> **Separ said:**
> Second, why is it such a problem to have everyone use "sudo" to gain temporary root powers?

I don't think he meant it's not enough for him to allow the other users to use sudo. The question he had was HOW to give them the right to use sudo.
It's probably a bad idea to do so (the more chefs, the worse soup, but if he thinks they can handle it, it's his choice...), but the "correct" way of doing it would be to add them to the admin group (editing the sudoers file may be catastrophic if you make a mistake).
Also, I think rampageoberon's advice (above) is probably safer than giving complete root access, as long as you know what you do when you edit the sudoers file.

---

