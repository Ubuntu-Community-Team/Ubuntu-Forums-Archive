---
title: "help found etc"
date: 2013-03-09
forum: General Help
---

### Post by bario22 on 2013-03-09
hi,
i install ubuntu 12.04
when i go to var , i dont find etc, i dont see this folder ( etc )
home<< file system<<< var<< but not found etc :(
i try to creat one but its not possible.
is there way to get back this etc folder

---

### Post by ManamiVixen on 2013-03-09
Everything was merged into "~/etc/" on the root partition starting in 12.04 for conviniance. Anything to do with etc should be put there instead.

---

### Post by bario22 on 2013-03-09
im new to linux :)
possible help me to creat this folder etc,
i mean when i open var i found etc
thanks for reply

---

### Post by claracc on 2013-03-09
etc folder is directly under / . Under var/ folder there is not an /etc/ folder.

Read this link: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview) to learn more about filesystem in ubuntu.

For creating a folder in ubuntu system with command line you will have to learn about mkdir command in xterm (you will have to run it with sudo because you will need root permissions.), you can use man mkdir order to know more.

Also, you can create a folder with nautilus file manager, for creating a folder under /var/ you need to run nautilus as root user. [http://linux.about.com/library/gnome/blgnome6n6g.htm](http://linux.about.com/library/gnome/blgnome6n6g.htm)

I do not recommend to touch filesystem since you can mess your ubuntu system. what for do you need a /var/etc/ folder?

---

### Post by bario22 on 2013-03-09
befor i use ubuntu 11.04 
i can see /var/etc
so when i made update to 12.o4
i dont see anymore etc.
possible get it back ?
thanks

---

### Post by Cheesemill on 2013-03-09
There isn't a /var/etc folder and never has been.

---

### Post by Impavidus on 2013-03-09
There is /var, there is /etc, there even is /usr/local/etc, but there's no /var/etc and there is no need for it either. It has been like that since the early days of Unix, over 30 years ago. And please, don't use sudo except for some standard maintenance tools until you are familiar enough with linux to know what you are doing. You can easely break your system.

---

### Post by Cheesemill on 2013-03-09
If you can explain what it is you are actually trying to achieve we can probably be more help :)

---

### Post by bario22 on 2013-03-09
before i go to home, file system, var then etc
so after update i dont see etc
what is the probleme ?

---

### Post by scbingham on 2013-03-09
READ the replies already given. There is no problem.

Maybe, previously, you created a directory called /home/var/etc for some unknown reason.

Users' directories live under /home
var lives under /
etc lives under /

There is no problem & never has been.

---

### Post by bario22 on 2013-03-10
[I]i tried to
create etc directory inside var directory
it say permission denied 
[/I]

---

### Post by Impavidus on 2013-03-10
If you want to modify things in system directories use sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But read the previous replies. *W**hy* do you want to create an etc directory in your var directory? Only because you remember there used to be one? You don't need one and if there was one on a previous installation it was an error. It's best to not change anything outside your home directory, unless you know what you're doing. Making an /var/etc directory because you remember there used to be one on 11.04 is not reason enough. Systems change and there could be errors in your previous installation.

The only problem there was, was that your 11.04 had a directory it shouldn't have had.

---

### Post by claracc on 2013-03-10
> **Impavidus said:**
> If you want to modify things in system directories use sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But read the previous replies. *W**hy* do you want to create an etc directory in your var directory? Only because you remember there used to be one? You don't need one and if there was one on a previous installation it was an error. It's best to not change anything outside your home directory, unless you know what you're doing. Making an /var/etc directory because you remember there used to be one on 11.04 is not reason enough. Systems change and there could be errors in your previous installation.

The only problem there was, was that your 11.04 had a directory it shouldn't have had.

+1.
Completely agree.

---

### Post by bario22 on 2013-03-10
i have hp proliant 110 G5
 freinds ask me *W**hy* do i want to create an etc directory in my var directory?
im using ubuntu for Cccam shairing with familly freinds ( football, movies...)
and i really need /var/etc back, without it, i cant install cccam.cfg and it will not work 
if possible how to creat an etcdirectory in var directory.
thanks

---

### Post by Cheesemill on 2013-03-10
Well, if you're absolutely sure you want that directory then just create it with...
```
sudo mkdir /var/etc
```

---

### Post by bario22 on 2013-03-10
thanks

---

