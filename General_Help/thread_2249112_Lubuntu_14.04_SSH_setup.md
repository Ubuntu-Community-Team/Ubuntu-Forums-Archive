---
title: "Lubuntu 14.04 SSH setup"
date: 2014-10-19
forum: General Help
---

### Post by Shamik_Biswas on 2014-10-19
Hi all,

I am using Lubuntu 14.04. I want to configure Hadoop on it. In order to do that, I was configuring "ssh". Now the problem is like following :

- I used the command "ssh localhost"
- Error: connect to host localhost port 22: Connection refused

- To get rid of the error I went on to install Openssh using the command : sudo apt-get install openssh-server
- Prompt : [sudo]password for hduser:
- I provided my HDUSER password correctly.
- However, still errror : hduser is not in the sudoers file.  This incident will be reported.

- In order to add HDUSER in SUDOERS file, I want to log into root using: su -
- prompt: Password:
- I don't know the root password. I provided the hduser password.
- Error : su: Authentication failure (quite obvious)

Questions :

- How to get rid of the port 22 error??
- How to know the root password ??
- How to log into Root correctly ??
- How to remove the error : hduser is not in the sudoers file.  This incident will be reported ??

Please provide detailed (step-by-step) solution. [Note: Myself an absolute beginner in Linux env] 

Heartiest thanks.

---

### Post by coffeecat on 2014-10-19
Welcome to the forum.

Lubuntu is an official flavour of Ubuntu and this thread doesn't need to be in Any Other OS, so...

*Thread moved to **General Help**.*

With regard to the root account, you don't need to log into root or know the root password. Have a read through of this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by O9aIevckc0 on 2014-10-19
use sudo not su
and the password will be whatever your password is
that should fix the three authentication problems

as for getting ssh working try this guide 
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

if this solves your question please mark this thread as solved

---

### Post by nerdtron on 2014-10-19
> - How to get rid of the port 22 error??
You already installed openssh-server.
> - How to know the root password ??
You don't have to know the root password? Who is the main user account on this computer? Use that user/password combination to do root things.
> - How to log into Root correctly ??
You don't. But you can be root after you login as a normal user.
Use "sudo su -" when you are logged-in as normal user then you'll be root.
> - How to remove the error : hduser is not in the sudoers file.  This incident will be reported ??
So this user is not a sudoer? The main user account must have created this user, so you need to login as the main user account and add this user to sudoers.

Can you show you terminal (screenshot) to us while you do your ssh commands and sudo commands so that we can have a better idea on what you are doing.

---

### Post by Shamik_Biswas on 2014-10-19
- logged in as normal user: now: -> shamik@shamik-HP-Pav-PC:~$
- log as hduser using: su - hduser // Now: hduser@shamik-HP-Pav-PC
- sudo su -
- Prompt: [sudo] Password for hduser : <provided the hduser password> hit enter
- Error: hduser not in sudoers file. This incident will be reported

------

- Tried : sudo - (as suggested)
- Still same error.

Bottomline : Issue still not fixed. Please help.

---

### Post by nerdtron on 2014-10-20
shamik user should add hduser to the sudoers:

```
shamik@shamik-HP-Pav-PC:~$ echo 'hduser ALL=(ALL) ALL' | sudo tee -a /etc/sudoers
 Password for shamik:
shamik@shamik-HP-Pav-PC:~$
```

Now try login as hduser, you should be able to "sudo su -"

BTW: why do you need to log in as hduser? shamik user can also "sudo su -" and be the root, so why need to login as hduser and then be root?

---

### Post by Shamik_Biswas on 2014-10-20
The above solutions worked :D :D :D 

Thanks all for your support / help.

---

