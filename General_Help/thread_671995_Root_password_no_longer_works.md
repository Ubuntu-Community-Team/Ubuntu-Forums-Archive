---
title: "Root password no longer works"
date: 2008-01-19
forum: General Help
---

### Post by Antexter on 2008-01-19
running kubuntu the version under 7.10, 7.07 or something.
When ever I try to run a sudo command it doesn't work, if I try and run a sudo command in konsole it doesn't give a error but it doesn't work.
If I try to run adept manager it gives the error incorrect password; please try again.
So I try again and then get conversation with su failed.

How do I go about fixing it?

---

### Post by amo-ej1 on 2008-01-19
Could you simply open an terminal and type  'sudo ls', when prompted enter your user password and paste the output here.

---

### Post by Antexter on 2008-01-19
no output it just goe

> computer@KDElappy:~$ sudo is
Password:
computer@KDElappy:~$

---

### Post by dabang on 2008-01-19
By default there is now "root" password in (K)Ubuntu (no matter what release you are running) as the root account is deactivated. The first user you create during installation of (K)Ubuntu has the privilege to run commands with "sudo" giving him temporary root access. The password you need to enter is the one of this user. To check your user's sudo privilges type:
```
sudo -l
```
and post the output here.

---

### Post by Antexter on 2008-01-19
computer@KDElappy:~$ sudo -l
Sorry, user computer may not run sudo on KDElappy.
computer@KDElappy:~$

Oh so its not that the root password has changed its just I cannot use root privileges on this account.

---

### Post by dabang on 2008-01-19
> Oh so its not that the root password has changed its just I cannot use root privileges on this account.
Yepp. I guess you created another user after installing Ubuntu? If you want this user to run commands with "sudo" you could modify /etc/sudoers directly (which I'd not recommend) or add the user to the "admin" group by
```
sudo usermod -G admin <username>
```
Of course, either way - you'll need a user who may run "sudo"... :)

---

### Post by Antexter on 2008-01-19
THANK YOU!!!
I've been able to use the sudo command before but it just suddenly stopped working today.

I loaded it up in recovery mode and put in the command, so thanks for your help. :D

---

