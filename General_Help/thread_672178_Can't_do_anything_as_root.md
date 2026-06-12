---
title: "Can't do anything as root"
date: 2008-01-19
forum: General Help
---

### Post by freaxxxter on 2008-01-19
I installed Ubuntu 7.10 a couple of weeks ago, and am almost ready to throw the computer out of the window!

I can't do anything as root, because it asks for a password I never entered at installation. I can't install certain applications and drivers, and of course I can't use the free space in the root partition, because I don't have the rights to do so!:-( 

P-L-E-A-S-E someone tell me what to do, because I'm just about ready to tear my last strands of hear off my scalp here. I've googled for information several times, and ran into some "solutions" that weren't solutions in the end after all.

HELP!

---

### Post by skulda on 2008-01-19
Try sudo
Being root is discouraged, "sudo command" is a good alternative.
If you insist working as root, you can get a root shell by 'sudo -s' or set a root password by 'sudo passwd'
Skulda

---

### Post by sumguy231 on 2008-01-19
Just to be sure, you are aware it's asking for your password and not a root password, right? 
[https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29)
I made the same mistake when I was new to Ubuntu. Spent 5 minutes yelling naughty words at the computer before I went and looked it up on the Internet. Of course they've tried to clarify that point in some places.

Other than that, did you do an OEM install or a regular install?

Edit: Beaten, sorta.

---

### Post by freaxxxter on 2008-01-19
Tnx for your replies.

1. I can't do SUDO because it asks for the root password, and when I try to write a password, it doesn't respond at all to my keypresses.

2. Yes I know that in most cases I'll get away with my personal password, like when I install from synaptic and stuff, but certain tasks that require to install as root is impossible for me..

---

### Post by jleaker01z on 2008-01-19
You can change the root password by going to System>Administration>Users & Groups

Click on root, select properties, enter password in the appropriate field.

---

### Post by aysiu on 2008-01-19
> **freaxxxter said:**
> Tnx for your replies.

1. I can't do SUDO because it asks for the root password, and when I try to write a password, it doesn't respond at all to my keypresses.

2. Yes I know that in most cases I'll get away with my personal password, like when I install from synaptic and stuff, but certain tasks that require to install as root is impossible for me..
These two links will help you:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aysiu on 2008-01-19
> **jleaker01z said:**
> You can change the root password by going to System>Administration>Users & Groups

Click on root, select properties, enter password in the appropriate field.
This is also completely unnecessary and is a workaround that doesn't solve the real problem.

---

### Post by sisco311 on 2008-01-19
please post the output of the **id **command:
```
id
```

---

### Post by kellemes on 2008-01-19
> **freaxxxter said:**
> Tnx for your replies.

1. I can't do SUDO because it asks for the root password, and when I try to write a password, it doesn't respond at all to my keypresses.

2. Yes I know that in most cases I'll get away with my personal password, like when I install from synaptic and stuff, but certain tasks that require to install as root is impossible for me..


Can you give an example of tasks you can't do without entering (the non existent) root-password.

---

### Post by jleaker01z on 2008-01-19
> **aysiu said:**
> This is also completely unnecessary and is a workaround that doesn't solve the real problem.


How so?  Ubuntu doesnt have a default root password, and that is his only problem.   He needs to change the root password to something he knows what it is, then he can enter it as needed.  This is the much simpler way of doing it, not from a command line.  Its also the way a Windows user can understand.  Windows users arent accustomed to a command line.

---

### Post by aysiu on 2008-01-19
> **jleaker01z said:**
> How so?  Ubuntu doesnt have a default root password, and that is his only problem. No. The OP's problems are: not understanding that the terminal does not display visual feedback when you enter your password *and* not understanding that you do not need to enable the root account in order to accomplish root tasks in Ubuntu.

---

### Post by kellemes on 2008-01-19
> **jleaker01z said:**
> How so?  Ubuntu doesn't have a default root password, and that is his only problem.   He needs to change the root password to something he knows what it is, then he can enter it as needed.  This is the much simpler way of doing it, not from a command line.  Its also the way a Windows user can understand.  Windows users arent accustomed to a command line.


There is no need for a root account.. You can get root-permissions without it.
Sudo handles that very well..

Edit: sorry.. didn't read the hole thread.. AYSIU explained it very well..

---

