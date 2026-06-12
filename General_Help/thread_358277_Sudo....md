---
title: "Sudo..."
date: 2007-02-10
forum: General Help
---

### Post by dmsn on 2007-02-10
Evening all!
I wonder if there is some way to fix this really crappy sudo thing before all admin related stuff.
Please tell me if you know, thanks in advanced.

---

### Post by Gibbs on 2007-02-10
You can start a session in the shell terminal with **su**. That will stop you from having to "sudo" everything. Alternatively you can enable root login at System > Administration > Login Window

---

### Post by dmsn on 2007-02-10
dmsn@laptop:~$ su
Password: 
su: Authentication failure
Sorry.
dmsn@laptop:~$ 

Wierd.

---

### Post by ardchoille42 on 2007-02-10
> **Gibbs said:**
> You can start a session in the shell terminal with **su**. That will stop you from having to "sudo" everything. Alternatively you can enable root login at System > Administration > Login Window

You can't do this on a default Ubuntu system because you don't have the root password. You have to use "sudo su" and even that is not recommended. The recommended way to get a root shell is:

```

sudo -i

```

Enabling the root account is not recommended for several security reasons. The main of which is thus:

If I wanted to break into your computer, I would start with the root account.. since I know you have a root account. I can't break into your user account(s) because I don't know the user name(s). I also can't break into the root account if it is disabled. Having the root account disabled, and using sudo, is a good security measure.

---

### Post by Gibbs on 2007-02-10
> **ardchoille42 said:**
> You can't do this on a default Ubuntu system because you don't have the root password. You have to use "sudo su" and even that is not recommended. The recommended way to get a root shell is:

```

sudo -i

```

Really? Well I'm pretty sure my setup is default as I haven't changed it...

---

### Post by rabid emu on 2007-02-10
You never want to run as root.  A password before everything important is a good thing because it stops you from screwing up your system inadvertantly.  If you do want to work as root for longer, you can use 'sudo su'.  If you want to remove sudo and enable the root account like most linux distros, you can check here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#User_Administration](http://ubuntuguide.org/wiki/Ubuntu_Edgy#User_Administration)

---

### Post by Rab22 on 2007-02-10
> **ardchoille42 said:**
> You can't do this on a default Ubuntu system because you don't have the root password. You have to use "sudo su" and even that is not recommended. The recommended way to get a root shell is:

```

sudo -i

```

Enabling the root account is not recommended for several security reasons. The main of which is thus:

If I wanted to break into your computer, I would start with the root account.. since I know you have a root account. I can't break into your user account(s) because I don't know the user name(s). I also can't break into the root account if it is disabled. Having the root account disabled, and using sudo, is a good security measure.


What's the real difference between 

```
 sudo -i 
```
&
```
 sudo -s 
```

?

---

### Post by aysiu on 2007-02-10
Fix it?

If it's broken, you can follow these instructions to fix it:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

