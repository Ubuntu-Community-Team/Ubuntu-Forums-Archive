---
title: "Creating a new user"
date: 2007-07-19
forum: General Help
---

### Post by xoppaw on 2007-07-19
So here is the low down. I just got a VPS server online and it is running Ubuntu 6.06 LTS (x86).  The problem that I am having right now is probably very simple. I would like to create a user other then the root user.  This user doesn't really need to be locked down at all, but I am just very weary of using the root user all the time for just tinkering around on the server.  Also once I have a new user set up is there an easy way to set them up with ftp access in vsftpd. Also I will verify before i get the typical GUI responses, I am not a GUI user and do not plan to be on this service, so any and all command line help would be appreciated. 
Thanks, 
xoppaw

---

### Post by FunkyJack on 2007-07-19
Go to:

System -> Administration -> Users and Groups

---

### Post by xoppaw on 2007-07-19
> **xoppaw said:**
>  Also I will verify before i get the typical GUI responses, I am not a GUI user and do not plan to be on this service, so any and all command line help would be appreciated. 
Thanks, 
xoppaw

[QUOTE=FunkyJack]Go to:

System -> Administration -> Users and Groups[/QUOTE]

Thanks, but not really an option.

---

### Post by DirtDawg on 2007-07-19
You can use 'adduser' to add a user. I'm not hugely familiar with this command, but you can always 'man adduser' and check out  '/etc/adduser.conf' to adjust options. I'm not sure about ftp setup, sorry.

---

### Post by FunkyJack on 2007-07-19
Sorry :)
Didn't read carefully.

[http://linux.about.com/od/commands/l/blcmdl8_useradd.htm](http://linux.about.com/od/commands/l/blcmdl8_useradd.htm)

---

### Post by xoppaw on 2007-07-19
> **FunkyJack said:**
> Sorry :)
Didn't read carefully.

[http://linux.about.com/od/commands/l/blcmdl8_useradd.htm](http://linux.about.com/od/commands/l/blcmdl8_useradd.htm)

thanks, that will be a great resource in learning how to do this

---

### Post by DirtDawg on 2007-07-19
whoa, 'useradd'? Guess my reference book is outdated :D

EDIT: Nope, I just got it wrong. Sorry!

---

### Post by xoppaw on 2007-07-19
are you sure, b/c it looks like both commands are available, i don't know if there is a difference....i'm reading up on that currently

---

### Post by DirtDawg on 2007-07-20
> **xoppaw said:**
> are you sure, b/c it looks like both commands are available, i don't know if there is a difference....i'm reading up on that currently

Lol, no I'm not really sure. I just looked up "add user" in my Linux reference book. So did you find out if there's a difference?

---

### Post by FunkyJack on 2007-07-20
You  can use both commands and they work in the same way.
Only differences are the options for arguments.

---

### Post by xoppaw on 2007-07-20
so if i did something like that:

adduser --system  maddox

how do i set a password. i have tried --p --password in various places and it still doesn't set.  any more suggestions?

---

