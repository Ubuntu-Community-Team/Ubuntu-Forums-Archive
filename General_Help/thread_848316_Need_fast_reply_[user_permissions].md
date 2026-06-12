---
title: "Need fast reply [user permissions]"
date: 2008-07-03
forum: General Help
---

### Post by Aloush on 2008-07-03
so i am following a tutorial and i need to install a file manualy as the other way didnt work this is what i am foloowing

To compile your own kernel:

    * Download 2.6.25 sources from kernel.org (click the "F" letter - you need the full source)
    * Ensure you have these packages installed: build-essential module-assistant kernel-package libncurses5-dev
    * Extract the kernel source into /usr/src/linux-2.6.25. To make sure you will be able to build as non-root, do this: 

sudo adduser your_user_name src
sudo chown -R root:src /usr/src
sudo chmod -R g+w /usr/src


but when i am trying to extract the file it says i do not have the permsions i have type those 3 setence into terminal somethign happened on the first one but not the second.
please help

---

### Post by drs305 on 2008-07-03
> **Aloush said:**
> 
sudo adduser **your_user_name** src
sudo chown -R root:src /usr/src
sudo chmod -R g+w /usr/src

but when i am trying to extract the file it says i do not have the permsions i have type those 3 setence into terminal somethign happened on the first one 

Was it an error message? Did you type **YOUR** username instead of *your_user_name* ?

Example: sudo adduser myname src

If this wasn't the problem, please give us the error message of the first command or a link to the site you are using.

---

### Post by Aloush on 2008-07-03
[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100)

thats the site and no error message just when i put into terminal it just went onto the next line

---

### Post by drs305 on 2008-07-03
Please run the commands again and see if they are any different than when I ran it. Replace "drs00" with your username.

```

~:
~: sudo adduser drs00 src
[sudo] password for drs00: 
Adding user `drs00' to group `src' ...
Adding user drs00 to group src
Done.
~: sudo chown -R root:src /usr/src
~: sudo chmod -R g+w /usr/src
~:

```

---

### Post by Aloush on 2008-07-03
In my terminal 

aloush@aloush-tablet:~$ sudo adduser aloush src
The user `aloush' is already a member of `src'.
aloush@aloush-tablet:~$ sudo chown -R root:src /usr/src
aloush@aloush-tablet:~$ sudo chmod -R g+w /usr/src
aloush@aloush-tablet:~$ 

when i tried and copy the file over

The folder "linux-2.6.25" cannot be copied because you do not have permissions to create it in the destination.

---

### Post by Aloush on 2008-07-03
still not working can i do in as root some now

---

### Post by sisco311 on 2008-07-03
Try to log out and log in.

---

### Post by Aloush on 2008-07-03
thanks got it working now :D

---

