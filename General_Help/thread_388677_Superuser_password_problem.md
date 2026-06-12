---
title: "Superuser password problem"
date: 2007-03-19
forum: General Help
---

### Post by songamericadj on 2007-03-19
What is the superuser password?

---

### Post by llamakc on 2007-03-19
Your password.

---

### Post by songamericadj on 2007-03-19
no its not, it is something different, i tried my password and it didn't work.

---

### Post by newlinux on 2007-03-19
Are you using su or sudo?

if su, then it doesn't have one until you set it, but there is no need to if you use sudo. You can use sudo to set the su password if you'd like.

---

### Post by songamericadj on 2007-03-19
sorry, i'm stupid. how do i do that in terminal?

---

### Post by newlinux on 2007-03-19
How do you do what? give the root account a password? Instead of doing that I'd recommend you do ```
sudo -i
``` if you want a root console. you defeat the purpose of sudo if you enable the root password.

If you just want to execute a few commands as super user just use sudo command paramaters...

---

### Post by 23meg on 2007-03-19
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Kamikaze Wardriver on 2007-03-19
From the command line type sudo and then the command. When it asks for the password try your password. If that doesn't work then you will have to assign root a password. Ubuntu by default creates a random password and does not tell you what it is. You can go into user manager and manually change the password though. If you want log on using root you also have to click on the security tab and select the box to allow system adminstrator to login locally. Hope this helps.

---

### Post by ardchoille42 on 2007-03-20
> **Kamikaze Wardriver said:**
> From the command line type sudo and then the command. When it asks for the password try your password. If that doesn't work then you will have to assign root a password. Ubuntu by default creates a random password and does not tell you what it is. You can go into user manager and manually change the password though. If you want log on using root you also have to click on the security tab and select the box to allow system adminstrator to login locally. Hope this helps.

There is no need to ever set a root password. I have been using Ubuntu since Warty on 11 computers (5 are servers) and I have never had to set a root password, this is why we use sudo. Enabling the root account makes your system less secure.

---

### Post by Kamikaze Wardriver on 2007-03-21
> **ardchoille42 said:**
> There is no need to ever set a root password. I have been using Ubuntu since Warty on 11 computers (5 are servers) and I have never had to set a root password, this is why we use sudo. Enabling the root account makes your system less secure.

I know, I don't set set a password for root either. The poster was asking what the root password is, so I gave him the step to do so. I agree though you are better of not doing it though. I have never needed it. Sudo works best.

---

