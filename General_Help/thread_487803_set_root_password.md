---
title: "set root password?"
date: 2007-06-29
forum: General Help
---

### Post by netwrkengeer on 2007-06-29
I have done several searches and have not found anything that has helped.

I have an Ubuntu server my administrator has left and I now have to get into and rest the root password. My user account has limited access and I can not use Sudo for some reason.

I have booted into recovery mode and still no luck. I'm not sure where I'm going wrong any help would be appreciated.

Thanks.

---

### Post by jfinkels on 2007-06-29
> **netwrkengeer said:**
> I have done several searches and have not found anything that has helped.

I have an Ubuntu server my administrator has left and I now have to get into and rest the root password. My user account has limited access and I can not use Sudo for some reason.

I have booted into recovery mode and still no luck. I'm not sure where I'm going wrong any help would be appreciated.

Thanks.

Are you unable to use ```
sudo passwd
``` completely? What's the error message?

---

### Post by netwrkengeer on 2007-06-29
when I type Sudo passwd I get the following.

User@UbuntuServer:/$
User@UbuntuServer:/$ sudo passwd
Password:
Sorry, Try again
Password:
Sorry, Try again
Password:
Sorry, Try again
sudo: 2 incorrect password attempts
User@UbuntuServer:/$

---

### Post by jfinkels on 2007-06-29
> **netwrkengeer said:**
> when I type Sudo passwd I get the following.

User@UbuntuServer:/$
User@UbuntuServer:/$ sudo passwd
Password:
Sorry, Try again
Password:
Sorry, Try again
Password:
Sorry, Try again
sudo: 2 incorrect password attempts
User@UbuntuServer:/$

Type YOUR password there. The program "sudo" requires that you authenticate yourself with your own password. The program "su" (root terminal) requires that you authenticate yourself as the super user, i.e. with the root password.

I apologize in advance if I am mistaken here.

---

### Post by netwrkengeer on 2007-06-29
I tried that too. It doesn't seem to help.

For example I'm trying to change the rights on my php.ini file when I type 

sudo chmod 777 php.ini

it looks like it works but then I do ls -l and I still see the old settings.

Also I can not su root.?

Any ideas?

---

