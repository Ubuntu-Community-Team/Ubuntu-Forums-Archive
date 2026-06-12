---
title: "First-Time Ubuntu user - need to login as root"
date: 2005-10-20
forum: General Help
---

### Post by khyberkitsune on 2005-10-20
I realized that Ubuntu never prompted me for a root password. How can I set one or at least login to root so I can install programs?

---

### Post by dbott67 on 2005-10-20
You don't need one.

Ubuntu, by default, disables the root account.  During installation, the first user account created is placed in the 'admin' group and can 'sudo' (super-user do) any administrative task.

So, if you want to edit a system config file, such as you sources.list file, you would open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```
When prompted for a password, you enter YOUR password.

BTW, any secondary user accounts that are created are NOT put in the 'admin' group unless explicity assigned there (so they cannot install software, make changes, etc.)

Hope this helps.

-Dave

---

### Post by ymmotrojam on 2005-10-20
Is it possible to enable the root account, regardless of whether it is necessary or not? :)

---

### Post by DRF on 2005-10-20
Ubuntu doesn't setup a root account by default (but it is possible to create a root account if you want) the main reason I understand is so people don't forget that they are logged on as root and get into bad habbits. It does make sense and I find that I now prefer this method.

To run commands as root you can add 'sudo' before any command to run it as root from the terminal. The first user account you created is setup as an administrator and can use sudo and the graphical version of sudo using the same password as you use to login as that user. (set during the install)

So to install programs via synaptic in the System menu you click on synaptics icon and then when it asks you for a password just use the password you setup for the first user account. (assuming you are logged on as this user at the time)
To run apt-get in a terminal console instead of logging on as root and typing:
apt-get update
you replace that with
sudo apt-get update
and you will get asked for the password. (I find that the ubuntu remembers the password for a limited amount of time so you won't have to constantly be typing it  in but you will still have to add sudo to the start of the console commands)

Hope this helps a little,

Daniel

---

### Post by dbott67 on 2005-10-20
[QUOTE=ymmotrojam]Is it possible to enable the root account, regardless of whether it is necessary or not? :)[/QUOTE]

Yes. To enable, type:
```
sudo passwd root
```

To disable, type:
```
sudo passwd -l root
```

-Dave

---

### Post by aysiu on 2005-10-20
For more on root and sudo, read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

