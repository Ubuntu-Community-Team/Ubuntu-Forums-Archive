---
title: "Move home directory to another directory"
date: 2013-01-11
forum: General Help
---

### Post by yacob_1 on 2013-01-11
Dear All,

I want to move my present home directory to another directory in my virtual-box ubuntu 12.04 distro. Here is what I want:

Right now my present home directory is  located at:

/home/jhon

but I want to change it to 

/home/users/jhon 

How do I do that ?  so that when I type $HOME, it should point to 
/home/users/jhon

---

### Post by dino99 on 2013-01-11
why doing complicated while you have it simple ?

---

### Post by yacob_1 on 2013-01-11
> **dino99 said:**
> why doing complicated while you have it simple ?
Thank you for your reply. 
But I want to mimic the directory structure of a server which I do not have a root access to it.

---

### Post by oldfred on 2013-01-11
I thought all user were under /home?

fred@A105-Precise:~$ echo $HOME
/home/fred

---

### Post by LewisTM on 2013-01-11
You can try the 'usermod -d' command
>  **usermod** [options] LOGIN
-d, --home HOME_DIR
The user´s new login directory. If the -m option is given the contents of the current home directory will be moved to the new home directory, which is created if it does not already exist.

Cheers!

---

### Post by Morbius1 on 2013-01-11
> **oldfred said:**
> I thought all user were under /home?
> but I want to change it to 

/home/users/jhon   .....

But I want to mimic the directory structure of a server which I do not have a root access to it.      Maybe it's just me but if you remove home from that path ( /users/jhon ) you have the directory structure of Win7. Am I making too many assumptions ?

---

