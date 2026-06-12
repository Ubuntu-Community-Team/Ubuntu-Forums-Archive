---
title: "root password differs from GUI &quot;Changing user...&quot;"
date: 2005-05-17
forum: General Help
---

### Post by elusivespoon on 2005-05-17
I enabled the root account using 'sudo passwd root'. However when I start a GUI program requiring root access, like synaptic, it does not accept the root password. It does accept the password of the initial regular user account.

What's going on, and how do I fix this (make it accept the root password, and not the regular user password)?

EDIT: I forgot to mention that if I 'su' in an xterm that the root password works. So the problem is the discrepancy between the root password in a shell, and the root password in the "Changing user..." GUI.

---

### Post by Xian on 2005-05-17
I'm not exactly familiar with that 'sudo passwd root' command.
Try this (as I reset my admin password):

```
xian@linux:~$ sudo passwd
Password:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

---

### Post by mravi on 2006-04-04
hi

sudo passwd root changes the root password but thru GUI the password is not accepted for network configuration.

help needed. or can anybody explain how i can activate my ethernet card thru command line interface, set IP address, DNS address, etc.

---

### Post by xenmax on 2006-04-04
i am no expert to speak on sudo issue and i am sure there are others who will tell you why, but the whole point in ubuntu is to use sudo for anything which requires root access.
as for system->administration->apps, it accepts your normal user(first user created which has admin privileges), unless u performed an expert install

---

### Post by localzuk on 2006-04-04
The applications call 'gtksud' (might have it wrong...) which is the gui command to run sudo. So when you click on an admin app, it wants to run 'sudo appname' rather than su followed by the application. This is done on purpose in order to make use of sudo across the system rather than root/su.

Why do you need to use the root account specifically? Why not have a regular user with sudo rights and not giving those rights to other users?

---

