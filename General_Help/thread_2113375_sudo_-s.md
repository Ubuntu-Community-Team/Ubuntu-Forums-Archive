---
title: "sudo -s"
date: 2013-02-07
forum: General Help
---

### Post by bigbankclub on 2013-02-07
What is the benefit of:

```
[FONT=&quot]:~$ sudo -s[/FONT]
```Ok so it gives one quick access to the superuser? And what else? But access to the superuser is easily available. How can one password protect this?

:(

---

### Post by Cavsfan on 2013-02-07
> **bigbankclub said:**
> What is the benefit of:

```
[FONT=&quot]:~$ sudo -s[/FONT]
```Ok so it gives one quick access to the superuser? And what else? But access to the superuser is easily available. How can one password protect this?

:(

All it does is prevent the need to enter **sudo** before every command.
Then you enter exit when finished.

The alternative is to enter **sudo apt-get update**, **sudo apt-get upgrade**, etc.

---

### Post by PowerBarry43 on 2013-02-07
Hi

sudo -s basically logs you in as the root user so you're running a whole shell as root rather than just individual commands. Alternatives are:

```
su - 
```

(probably the other main one)

```
sudo /bin/bash
sudo bash 
```

(works but you'd probably never need)

all of these let you run commands as root, the differences are which environment variables you have and their values which can be viewed by running:

```
env
```

for example

```
echo $HOME
```

outputs the contents of the environment variable, HOME which is the path to your home directory. If you use su - this will return /root but if you run sudo -s this will output /home/$USER

hope this helps!!

Barry

---

### Post by coffeecat on 2013-02-07
> **PowerBarry43 said:**
> Alternatives are:

```
su - 
```

I think that will only work if you've enabled the root account, which is not a good idea.

@bigbankclub, you will find this useful:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There is much good information in there. In particular, near the end it describes why these:

```
sudo -s
sudo bash
sudo su
```

.... are inadvisable. If you really, really, really must run a root shell, then you would be better with:

```
sudo -i
```

---

### Post by grahammechanical on 2013-02-07
> How can one password protect this?

One password is all we ever have. Have you ever tried on-line banking? Do you think that we should have such a complicated system for just using a computer.

There comes a point when the security methods are so troublesome that it becomes too much trouble to use the computer. That's when people start sticking notes on the screen with their passwords on. And it is usually the boss that does this.

How much security does an ordinary user need?

---

### Post by surfer on 2013-02-07
> **bigbankclub said:**
> 
How can one password protect this?


not everyone is allowed to use sudo. you have to be in the [FONT="Courier New"]sudo[/FONT] group. that's how root access is protected. ...if that was your question.

---

