---
title: "Unable to cd /home/user"
date: 2006-07-19
forum: General Help
---

### Post by leonardox on 2006-07-19
I was installing e17 when I tried to do su - user and I get this message Unable to cd /home/user. Login with  root I can't run some services like dhcpd,tor logs says permission denied. 

TIA

---

### Post by mlind on 2006-07-20
> **leonardox said:**
> I was installing e17 when I tried to do su - user and I get this message Unable to cd /home/user. Login with  root I can't run some services like dhcpd,tor logs says permission denied. 

TIA

What are you trying to accomplish by invoking "su - user" ?
Have you tried with actually existing username, like "su - leonardox" ?

---

### Post by Christmas on 2006-07-20
I'm not sure I understood your problem, however the root account is disabled by default in Ubuntu, you can read how to use sudo here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") and also a discussion about sudo vs. gksudo (GNOME) or kdesu (KDE) here: [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo"). Sorry if this is not what you were looking for.

---

### Post by leonardox on 2006-07-25
My english is very bad sorry.
I cannot login with my account because I get this message  Unable to cd leonardox but I can get in only with root but I still have problems, with root I can't execute sudo or dhcpcd3 I get permission denied.
I would like to now what to do to resolve this problem, thanks.

---

### Post by leonardox on 2006-08-02
my problem was fixed 8)

---

