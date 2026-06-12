---
title: "root password"
date: 2008-01-31
forum: General Help
---

### Post by pooria_pooria on 2008-01-31
I  have just installed ubuntu. When I was installing it, I was not asked to provide password for root account. Now that I want to install an application, I am asked for root account, but I dont have any password and I dont know how to find it. Practially I just used one password for my own account. How can I get the password for the root account please?

---

### Post by p_quarles on 2008-01-31
Ubuntu uses a locked root account by default, and gives the first user created full "sudo" admin privileges. That's the way it's supposed to work. You can create further users without sudo privileges.

If you wish to enable the root account, you just need to create a password for it.

---

### Post by hokiejp on 2008-01-31
For most things it's enough to to use 'sudo', which runs any application with root privileges.  So if you want to install something you just built, you run 

sudo make install

or 

sudo name_of_installer

When you use sudo (or run programs like Synaptic that need root priviliges), they will prompt you for YOUR password, so you should enter the password for your user account.

If you need to become root, you can do something like 'sudo su'.  I think you can also enable the root account by running  'sudo passwd root', which will let you set the root password.  I haven't found it necessary to do this, though.

If none of this solves your problem, maybe you could post more specifics about what you are trying to do.

---

### Post by aysiu on 2008-01-31
> **pooria_pooria said:**
> I  have just installed ubuntu. When I was installing it, I was not asked to provide password for root account. Now that I want to install an application, I am asked for root account, but I dont have any password and I dont know how to find it. Practially I just used one password for my own account. How can I get the password for the root account please?
What are you installing? It should be asking for your user password, not the root password? There is no root password set in Ubuntu, and it's not necessary to set one either.

---

### Post by ComputerHermit on 2008-01-31
yea what is it your asking?

---

### Post by overdrank on 2008-01-31
> **pooria_pooria said:**
> I  have just installed ubuntu. When I was installing it, I was not asked to provide password for root account. Now that I want to install an application, I am asked for root account, but I dont have any password and I dont know how to find it. Practially I just used one password for my own account. How can I get the password for the root account please?

Hi and welcome, maybe this link can help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

