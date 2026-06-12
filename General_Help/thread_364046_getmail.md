---
title: "getmail"
date: 2007-02-17
forum: General Help
---

### Post by Orfeus on 2007-02-17
Hey!

I m trying to install getmail but when i enter the command

```
 python setup.py install 
```

i have to enter the root password. Where can i find it?

Any suggestions?

---

### Post by solar george on 2007-02-17
In ubuntu the root password is not used. You use sudo to access the root account.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Are you sure that getmail is not in the repos;
```
apt-cache search getmail
ax25mail-utils - hamradio utilities for fbb
getmail4 - mail retriever with support for POP3, IMAP4 and SDPS

sudo apt-get install getmail4
```

This should sort it out.

If you just need to read your own mail just use thunderbird or evolution.

---

### Post by Orfeus on 2007-02-18
i still get this error

```
Error: configuration file /home/tziny/.getmail/getmailrc does not exist
```

about the root password:

If i put my password is going to work?
Because i've tried it and it says that it is wrong

---

### Post by solar george on 2007-02-18
Have you tried installing from the repos - this would save a lot of effort.


> If i put my password is going to work?
Because i've tried it and it says that it is wrong


No it won't - you have to run the command using sudo:
```
sudo python setup.py install
```
This will run the program as if you were logged in as root - it shouldn't ask for a password.

If it still asks for a password then you can set the root password by 
```
$ sudo passwd root
```
Make sure that the password is a good one and don't log in as root. Root has absolute power on your system. From that account you can destroy all of your data, or mearly make your computer go very wrong.

---

### Post by Orfeus on 2007-02-18
it works now! thanks!

---

