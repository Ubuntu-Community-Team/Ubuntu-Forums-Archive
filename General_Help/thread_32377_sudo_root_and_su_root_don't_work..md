---
title: "sudo root and su root don't work."
date: 2005-05-07
forum: General Help
---

### Post by SlugO on 2005-05-07
I'm having problems with sudo and su. Here is an example what happens when I try to use them:
```
janne@mylly:~$ sudo root ls
Password:
sudo: root: command not found
janne@mylly:~$ su root
Password:
su: Authentication failure
Sorry.
```
In both of the cases the password is correct. Atleast synaptic accepts it...
The only way I can use root priviledges on command line is to open
the separate root terminal from the application menu.

So how can I get sudo root and/or su root to work?

---

### Post by SlugO on 2005-05-07
And for some reason I get this error when running programs from root terminal:


root@mylly:/home/janne # gedit

(gedit:23902): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Luckily it doesn't stop the programs from starting.
Any idea what's causing this message?

---

### Post by Fab on 2005-05-07
[QUOTE=SlugO]I'm having problems with sudo and su. Here is an example what happens when I try to use them:
```
janne@mylly:~$ sudo root ls
Password:
sudo: root: command not found
janne@mylly:~$ su root
Password:
su: Authentication failure
Sorry.
```
In both of the cases the password is correct. Atleast synaptic accepts it...
The only way I can use root priviledges on command line is to open
the separate root terminal from the application menu.

So how can I get sudo root and/or su root to work?[/QUOTE]
 its ```
sudo <commandhere>
```

---

### Post by Sam on 2005-05-07
Try (in your example)
```
$ sudo ls
```

If you want to use su root, you have to [enable root password](http://ubuntuguide.org/#setchangeenablerootpassword) (it's better to use sudo anyway).

---

### Post by jfdill_2 on 2005-05-07
[QUOTE=Sam]Try (in your example)
```
$ sudo ls
```

If you want to use su root, you have to [enable root password](http://ubuntuguide.org/#setchangeenablerootpassword) (it's better to use sudo anyway).[/QUOTE]
If you want a root shell, just do

sudo sh

Or whatever your favorite, installed shell happens to be.  Or you can go to Applications -> System -> Root Terminal

---

### Post by GoneWacko on 2005-05-07
[QUOTE=SlugO]And for some reason I get this error when running programs from root terminal:


root@mylly:/home/janne # gedit

(gedit:23902): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Luckily it doesn't stop the programs from starting.
Any idea what's causing this message?[/QUOTE]

Now THAT is something I am wondering about as well.

But I guess it's just got something to do with how root shouldn't be allowed to use the X server?

---

### Post by kosmic on 2005-05-07
[QUOTE=GoneWacko]Now THAT is something I am wondering about as well.

But I guess it's just got something to do with how root shouldn't be allowed to use the X server?[/QUOTE]

Yap, you are right

---

