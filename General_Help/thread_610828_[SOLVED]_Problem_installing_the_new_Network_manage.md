---
title: "[SOLVED] Problem installing the new Network manager"
date: 2007-11-12
forum: General Help
---

### Post by cl_audio on 2007-11-12
Alright, well I am not very aware of the whole tar extraction/compiling. This here is giving me problems, and I'm not experienced enough to figure this out.


I am running Feisty Fawn...

I downloaded the updated version of the Network Manager 0.6.5 ( I have included the tar)

I just don't know how to install it.

I go into terminal, change into the extracted folder, I run the ./configure

Once that runs I type make and it just fails.... any ideas?



Thanks in advanced!

---

### Post by zvacet on 2007-11-12
Let say that you downloaded that package in home folder.Right click on it and you will see **unpack here** option.Select it and folder will be created.You have to go inside of that folder with command 

```
cd /foldername
```

Once you are inside 

1. ./configure
2. make
3. sudo make install

To be able to do all above you need to install (if you didn´t do it until now)

```
sudo aptitude install rar unrar p7zip p7zip-full
```

and for compiling
```
sudo aptitude install build-essential
```

---

### Post by luisromangz on 2007-11-12
You should provide the error that make shows, otherwise it would be difficult to help you.

---

### Post by cl_audio on 2007-11-12
I tried those steps, but make is still not working...

here is a snippet of what the terminal echos

checking whether byte ordering is bigendian... no
checking for /etc/redhat-release... no
checking for /etc/SuSE-release... no
checking for /etc/fedora-release... no
checking for /etc/gentoo-release... no
checking for /etc/debian_version... yes
checking for /etc/arch-release... no
checking for /etc/slackware-version... no
checking for wireless-tools >= 28pre9... no
*configure: error: wireless-tools >= 28pre9 not installed or not functional*
**local@local-laptopcscl:~/Desktop/NetworkManager-0.6.5$ make**
*make: *** No targets specified and no makefile found.  Stop.*
**local@local-laptopcscl:~/Desktop/NetworkManager-0.6.5$ sudo make install**
*make: *** No rule to make target `install'.  Stop.*
local@local-laptopcscl:~/Desktop/NetworkManager-0.6.5$ 

Thanks

---

### Post by MrFSL on 2007-11-12
looks like you are missing the source or development package for "wireless-tools" so ./configure is failing.

---

### Post by cl_audio on 2007-11-12
...

I understand that much... I'm looking for a solution...

---

### Post by MrFSL on 2007-11-12
> 
I understand that much... I'm looking for a solution...

Sorry, I figured if you understood this you wouldn't have tried to execute ***make*** after the failure of ***./configure***

---

### Post by zvacet on 2007-11-12
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Find there wireless-tools for your version.Don´t forget to download dependencies,and install them first.When you are done try to compile again.

---

### Post by cl_audio on 2007-11-12
> **MrFSL said:**
> Sorry, I figured if you understood this you wouldn't have tried to execute ***make*** after the failure of ***./configure***

I just continued to follow the steps even after failure so people don't come back and tell me to do this step and that....


I said in my first post that it failed....


Anyways... SOLVED THANKS FOR YOU HELP

---

