---
title: "cant type authentication password in terminal"
date: 2007-07-08
forum: General Help
---

### Post by epidemic066 on 2007-07-08
for some strange reason, i cant type the authentication password in the terminal window. for 

example :

epidemic066@epidemic:~$ su
Password: 
su: Authentication failure
Sorry.
epidemic066@epidemic:~$ 


thats what happens when i leave the password line blank.

---

### Post by taurus on 2007-07-08
Did you create a password for root?  That is what it's looking for.  

Try using sudo instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Nekiruhs on 2007-07-08
You have to ```
sudo su
``` su by it self fails, sudo is necessary. Also sudo is more recommended in Ubuntu instead of su.

---

### Post by epidemic066 on 2007-07-08
ahh, well i partly blame the sun java site. i was reading their guide on how to install java on linux, and it says to type su in the terminal, then your pass, and so on.

thanks for the help, maybe im ok from this point


maybe not - it still isnt letting me type anything on the password line :

epidemic066@epidemic:~$ sudo su
Password:
Sorry, try again.
Password:

i cant type letters, numbers, spaces, etc.

---

### Post by taurus on 2007-07-08
Sun's java is also available in the repos.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Mr. C. on 2007-07-08
> **Nekiruhs said:**
> ```
sudo su
``` 

This is redundant, and is the same as:

```
sudo -s
```

Sudo and su do essentially the same thing; in a nutshell, they change a user's UID and GID.

MrC

---

### Post by hikaricore on 2007-07-08
I just wanted to point out that: **Linux Hides Your Password Input!**

This is a security feature and often misunderstood by new users as the password entry not working.

---

