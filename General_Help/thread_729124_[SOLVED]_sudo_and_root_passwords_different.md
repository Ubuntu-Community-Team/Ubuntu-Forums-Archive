---
title: "[SOLVED] sudo and root passwords different?"
date: 2008-03-19
forum: General Help
---

### Post by tmillic on 2008-03-19
I'm using Ubuntu 7.04, trying to install the printer driver using the following as a non-root user: 
sh hplip-2.8.2.run
At some point in the installation, I'm asked to "Please enter the root/superuser password".
I enter the root password, and I'm informed that it's incorrect. I've tried the user's password as well with the same result.
I can sill log in as root with the same password I set originally, but any attempt to use sudo results in failed password attempts. 
I had thought that the password for sudo actions was the same as the password for root. This doesn't seem to be the case. Is there a remedy for this so that I can use sudo?
Thanks.

---

### Post by Rocket2DMn on 2008-03-19
The password used for sudo is the password you use in your user login.  root password can be different if you specify it to be - sudo is not really the same as being root.  Does that clear up the confusion?

---

### Post by Steveway on 2008-03-19
Those drivers are in the repositories, afaik.
You can install them with Synaptic.

---

### Post by tmillic on 2008-03-19
The user and root passwords are set to be different, and neither work. That's why I'm stumped. I can't figure out how or where sudo stopped working with the passwords I'd been using.
Maybe I just need a coffee break? :-)

---

### Post by tmillic on 2008-03-19
It's embarrassing to post a question after hours of being stuck, only to realize something obvious that you were doing wrong. 
I was logged in as a user that didn't have sudo privileges. 
Thanks.

---

### Post by bodhi.zazen on 2008-03-19
> **tmillic said:**
> Maybe I just need a coffee break? :-)

Looks like the coffee worked :twisted:

[img]http://tbn0.google.com/images?q=tbn:SLYFLawKvWZd9M:http://www.javalavacoffeeshops.com/images/coffee.jpg[/img]

---

### Post by dfreer on 2008-05-08
> **tmillic said:**
> I'm using Ubuntu 7.04, trying to install the printer driver using the following as a non-root user: 
sh hplip-2.8.2.run
At some point in the installation, I'm asked to "Please enter the root/superuser password".
I enter the root password, and I'm informed that it's incorrect. I've tried the user's password as well with the same result.
I can sill log in as root with the same password I set originally, but any attempt to use sudo results in failed password attempts. 
I had thought that the password for sudo actions was the same as the password for root. This doesn't seem to be the case. Is there a remedy for this so that I can use sudo?
Thanks.

Glad you solved your problem. Some things I would also have attempted:
If the program requires root access, then launch the program initially with sudo like so:
```
sudo sh hplip-2.8.2.run
```
Given root a password just for the install, then lock it up again:
```
sudo passwd root
*<Enter your password for sudo>*
*<Enter the new root password twice>*

sudo passwd -l root
```
Logged in temporarily as root:
```
sudo su
```

Just ideas for future readers :D

---

### Post by bodhi.zazen on 2008-05-08
If you really want to do this, use the option "targetpassword" in /etc/sudoers

Edit with visudo

See this thread for how I do it :

[http://ubuntuforums.org/showpost.php?p=4281283&postcount=36](http://ubuntuforums.org/showpost.php?p=4281283&postcount=36)

Basically I set a root PW, but then set the root shell to /bin/false

For a root shell sudo bash ...

---

