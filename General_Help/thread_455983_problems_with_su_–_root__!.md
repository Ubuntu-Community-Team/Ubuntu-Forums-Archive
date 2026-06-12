---
title: "problems with su – root  !"
date: 2007-05-27
forum: General Help
---

### Post by yento on 2007-05-27
Kubntu, 

Working with Konsol to update software. 
running  
su
password 
not working using root password. 

fails on authentication. 

However running adept installer + root password works every time

Is this a bug or configuration issue ?

---

### Post by bapoumba on 2007-05-27
Hi,
what do you call root password? Your user password ?

edit:
```
sudo su
```
will give you a root shell.

To go back to normal user shell:
```
exit
```

---

### Post by Tyche on 2007-05-27
> **yento said:**
> Kubntu, 

Working with Konsol to update software. 
running  
su
password 
not working using root password. 

fails on authentication. 

However running adept installer + root password works every time

Is this a bug or configuration issue ?

This is a perennial problem, especially with users new to Ubuntu.  There is a "lock" on the root user.  For safety and security reasons, Ubuntu has chosen to bring users up without allowing them to be root automatically.  However, there is a way.

For single commands, sudo is quite effective, and leaves no root open to be exploited.

For those times when one just HAS to be root (and there are some), there is a work-around.

Bring up a terminal and type:
sudo passwd
[This will ask you to type your user password to access a root command.  It will then bring up a line asking you to type a Unix password.  This will be your NEW ROOT password.  It will then ask you to repeat it.  At the end of this sequence you will be able to log into a terminal as root.]

Hope this helps.

Craig
Tyche

---

