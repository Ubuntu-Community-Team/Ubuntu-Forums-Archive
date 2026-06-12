---
title: "Command line help"
date: 2014-01-07
forum: General Help
---

### Post by t.williams.im on 2014-01-07
Hi,

I'm just learning how to use the command. A few easy questions:

1. How do I navigate from the "/" directory to the main directory which includes the Documents and Music directory? I use to cd .. command but that doesn't work.
2. Is there a directory for applications and how do I find it?

Thanks,

Tim

---

### Post by steeldriver on 2014-01-07
1. Just
```
cd
```
or
```
cd ~
```
will get you to your **home directory** from anywhere

2. not really - at least not in the sense that you may be familiar with from Windows (like C:\Program Files). Can you give us the bigger picture of what you are trying to do?

---

### Post by Iowan on 2014-01-07
Just **cd** will get you to your home directory.
(or **cd ~**)
/ is the root directory - it has no parent, so **cd ..** won't work.

---

### Post by t.williams.im on 2014-01-07
Awesome! Thanks.

With regards to the applications, I'm just finding it a little disorienting not having a folder for them.

---

### Post by ian-weisser on 2014-01-07
There are several directories for applications.
There are different directories for those applications' configs and settings, manuals, libraries, and more.
Generally, you don't need to know where they are. But if you're curious, browse through /bin and /usr
Most are owned by root. Don't mess with them. Some of those applications are vital to your system's operation.

Some people want to groups files by source (all files for Foo Application in one place)
Others want to to group files by function (all executables in one place, all settings in another)
Linux has traditionally used the latter approach. It aids collaboration and reduces duplication.

---

### Post by Lars Noodén on 2014-01-08
Most applications will be in /bin, /usr/bin, or /usr/local/bin, mostly the first two.   

System utilities will usually be in /sbin, /usr/sbin or /usr/local/sbin

A general overview of where things belong is explained in [hier](http://manpages.ubuntu.com/manpages/saucy/en/man7/hier.7.html).

---

### Post by mark65ak on 2014-01-08
> **t.williams.im said:**
> 
1. How do I navigate from the "/" directory to the main directory which includes the Documents and Music directory? I use to cd .. command but that doesn't work.

```

cd /home/USERNAME/Documents
```
and
```
cd /home/USERNAME/Music
```
respectively

Note you have to replace USERNAME with your own login name and be aware that directories and usernames are case sensitive.  Music, MUSIC and music would be 3 different directories.

pwd will show you the directory you are currently in  
ls will list the contents of the directory you are in.
cd.. move you to the parent directory of the directory you are in
  Good luck.

---

### Post by Alculete on 2014-01-08
if you installed through Ubuntu Software Center, via terminal or .deb files, all installed softwares will be on software center when you need to remove them

---

### Post by rnerwein2 on 2014-01-08
hi
if your "cd " don't works. 
give a "echo $HOME" a change to see where your installation is.
ciao

---

