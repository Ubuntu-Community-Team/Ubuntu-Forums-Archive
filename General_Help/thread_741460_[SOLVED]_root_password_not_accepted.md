---
title: "[SOLVED] root password not accepted"
date: 2008-03-31
forum: General Help
---

### Post by Kevin Jones on 2008-03-31
HI all,
My KDE4.x does not recognize the root password. I am able to log in and out of the desktop. I can shut down and restart, but I cannot install new programs becuase the password is not recognized.
Can anyone help?

KEvin Jones

---

### Post by pointone on 2008-03-31
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Slushdoot on 2008-03-31
Did you set a real root password, or are you using sudo?

---

### Post by 65 mustang on 2008-03-31
you can set the root password by doing
```
sudo passwd
```
untill you do this you cannnot login as root

---

### Post by aysiu on 2008-03-31
> **65 mustang said:**
> you can set the root password by doing
```
sudo passwd
```
untill you do this you cannnot login as root
What you're saying is true, but it's a little misleading, as you also do not need to log in as root... or set a root password.

---

### Post by Kevin Jones on 2008-03-31
Dear all,
I did not realize that the root password and the sudo password were not the same thing.
As it happens I have installed a package with the terminal. So I do know my sudo root password.
I cannot remember setting a 'root' password. I have a default choice of password that I use for all my linux stuff. If I had been given the choice of choosing a 'root' password I would have used it.
I am not sure of the nomenclature here
"Run as root -KDE su
The action you requested needs ROOT PRIVILEGES please enter ROOT'S password below or ignore to continue with your current privileges.
Command: /usr/sbin/synaptic.
If I had pressed ignore I guess I could have downloaded the package to my user accounts and not the the pc as a whole. I guess.
any way...Thanks everyone, Problem solved. and I learned something more today


Kevin

---

### Post by Slushdoot on 2008-03-31
I think you've figured it out, but just to reiterate: to run a command with root privileges preface it with sudo for command-line utilities, or gksudo for GUI utilities.  Provide it with your user password and it will work.

:)

---

### Post by aysiu on 2008-04-01
If you're using Synaptic, the command is ```
gksudo synaptic
``` If you're using Adept, the command is ```
kdesu adept
``` Honestly, though, you shouldn't need to know the command. Just click the menu item for the package manager and enter your *user* password when prompted.

---

