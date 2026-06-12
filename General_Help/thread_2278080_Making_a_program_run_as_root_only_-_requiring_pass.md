---
title: "Making a program run as root only - requiring password"
date: 2015-05-13
forum: General Help
---

### Post by manuleka on 2015-05-13
how do i add an application to run only as root and requires password?

---

### Post by QIII on 2015-05-13
Hello!

What are you trying to do that can't be run under a sudoer's account with that user's password?

---

### Post by manuleka on 2015-05-13
> **QIII said:**
> Hello!

What are you trying to do that can't be run under a sudoer's account with that user's password?

hi Sir,

I have family computer in our living room running xubuntu 14.04 and everyone seems to mess about with menu editor (menulibre) and some other softwares which i don't want them to. 

So basically i want to set those programs to require password access

cheers

---

### Post by Tadaen_Sylvermane on 2015-05-13
The proper way is to have different user accounts for everyone. Then they can mess with whatever they like and it won't affect anyone else.

---

### Post by manuleka on 2015-05-13
yip i thought of that, but then out of curiosity how do i add an application to root user/group?

I would rather just add the applications to get password request upon initiation

---

### Post by Vladlenin5000 on 2015-05-13
> **Tadaen_Sylvermane said:**
> The proper way is to have different user accounts for everyone. Then they can mess with whatever they like and it won't affect anyone else.

^^^^
This. People often forget about this. Not surprisingly because they have years (decades?) of being dumbed down by a certain mainstream OS that, by default and by design, started with automatic login, in all but the recent releases. The same OS is multi-user as well but that feature was never advertised properly - and it should have been, advertised *and* recommended - therefore the most common scenario in a "family computer" is everybody using everything in a single user session, no different users/password, nothing...

---

### Post by matt_symes on 2015-05-13
Hi

> how do i add an application to run only as root 

This could change the edited configuration files ownership to root and cause you problems.

> and requires password?

The solution, as has been pointed out, is to give everybody their own login account with their own password. Unix and Linux were originally designed as multi user systems for this kind of reason.

You can have a shared partition for data files, that all users can access, if that is what you want.

This really is the best solution and is part of the design of Linux.

Kind regards

---

### Post by manuleka on 2015-05-13
> **matt_symes said:**
> Hi
This could change the edited configuration files ownership to root and cause you problems.

The solution, as has been pointed out, is to give everybody their own login account with their own password. Unix and Linux were originally designed as multi user systems for this kind of reason.

You can have a shared partition for data files, that all users can access, if that is what you want.

This really is the best solution and is part of the design of Linux.

Kind regards

ok thanks, i just thought it would be a simple task to get an application passworded

---

### Post by matt_symes on 2015-05-13
Hi

I'm interested: besides the menu and the settings panel, can you list all the applications that you don't want these users to use. You've been a bit vague with this area.

Kind regards

---

### Post by HermanAB on 2015-05-13
To answer the actual question:
$ sudo su -
# chown root: program
# chmod 755 program
# exit
$

---

### Post by manuleka on 2015-05-13
just menu editor (menulibre) and samba share but the later requires password access.

---

### Post by manuleka on 2015-05-13
> **matt_symes said:**
> Hi

I'm interested: besides the menu and the settings panel, can you list all the applications that you don't want these users to use. You've been a bit vague with this area.

Kind regards

just menu editor (menulibre) and samba share but realised the later requires password access

---

### Post by matt_symes on 2015-05-13
Hi

> **manuleka said:**
> just menu editor (menulibre) and samba share but the later requires password access.

If they don't know your superuser password, or if they do and you change it so they don't, then you could make menulibre non executable and when you actually need to use it make it executable again.

That's one workaround.

```
sudo chmod 644 /usr/bin/menulibre
```

```
sudo chmod 755 /usr/bin/menulibre
```

As has been pointed out though, It's not really in keeping with the Linux framework though.

I would not really want to run the menu editor under any user but you though in case it does cause you problems.

Kind regards

---

### Post by manuleka on 2015-05-14
> **matt_symes said:**
> Hi



If they don't know your superuser password, or if they do and you change it so they don't, then you could make menulibre non executable and when you actually need to use it make it executable again.

That's one workaround.

```
sudo chmod 644 /usr/bin/menulibre
```

```
sudo chmod 755 /usr/bin/menulibre
```

As has been pointed out though, It's not really in keeping with the Linux framework though.

I would not really want to run the menu editor under any user but you though in case it does cause you problems.

Kind regards

thanks :)

---

### Post by manuleka on 2015-05-14
> **HermanAB said:**
> To answer the actual question:
$ sudo su -
# chown root: program
# chmod 755 program
# exit
$

cheers :) i don't think any other part of the system would use menulibre, so shouldn't be a problem i hope

---

### Post by SeijiSensei on 2015-05-14
Those commands will still let anyone run the program.  Nearly all the software on the machine is owned by root, yet everyone can run it.  Why?  Because the 755 permission mask grants eXecute privileges to everyone:
```

ls -l /usr/bin/mplayer
-rwxr-xr-x 1 root root 15753176 Feb 17 12:26 /usr/bin/mplayer

```
That last "x" grants everyone execute privileges.

What you want is 700 privileges on a file owned by root ("sudo chmod 700 /path/to/some/program").  Then only root can run that program.

---

### Post by matt_symes on 2015-05-14
Hi

There is one final clarification i would like to make. A file can be owned by root but run as a user.

Take the file touch.

```
matthew-laptop:/home/matthew:1 % ls -l /bin/touch
-rwxr-xr-x 1 root root 60224 Jan 14 03:50 /bin/touch*
matthew-laptop:/home/matthew:1 %
```

Touch is owned by root but i can use touch to create file for my user.
```

matthew-laptop:/home/matthew:1 % touch my_touch
matthew-laptop:/home/matthew:1 % ls -l my_touch 
-rw-rw-r-- 1 matthew matthew 0 May 14 18:22 my_touch
matthew-laptop:/home/matthew:1 %
```

I can also use touch to create a file owned by root.

```
matthew-laptop:/home/matthew:1 % sudo touch root_touch
[sudo] password for matthew: 
matthew-laptop:/home/matthew:1 % ls -l root_touch 
-rw-r--r-- 1 root root 0 May 14 18:22 root_touch
matthew-laptop:/home/matthew:1 %
```

I was under the impression that you wanted to run menulibre as a root user. Your menu configuration files would then be owned by root. Not what you really want.

Kind regards

---

### Post by manuleka on 2015-05-14
thanks guys :) very insightful information... greatly appreciate it

---

