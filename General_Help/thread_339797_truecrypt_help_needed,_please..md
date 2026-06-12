---
title: "truecrypt help needed, please."
date: 2007-01-16
forum: General Help
---

### Post by ice60 on 2007-01-16
hi, does anyone know how to encrypt one directory on my desktop using truecrypt? all the tutorials i've ever found show how to encrypted things like thumb drives.

i've wanted to do this for ages and have spent hours searching for help. i've even said to my self afew times that i'd try setting it up in Vmware as it's not so bad if i make a mistake there, but just never even typed one command because i just don't understand what to do ](*,)

---

### Post by majoridiot on 2007-01-16
you need to first create a truecrypt folder:

```
cd ~/Desktop
truecrypt -d
```

you will be prompted for the various attributes for the folder.  once the truecrypt folder is 
created, you can copy your sensistive data into it and use it from there.

for full info:

```
man truecrypt
```

---

### Post by ice60 on 2007-01-17
> **majoridiot said:**
> you need to first create a truecrypt folder:

```
cd ~/Desktop
truecrypt -d
```

you will be prompted for the various attributes for the folder.  once the truecrypt folder is 
created, you can copy your sensistive data into it and use it from there.

for full info:

```
man truecrypt
```
thanks, majoridiot. so that's pretty much it?? i think i have some kind of odd reaction when it comes to working with truecrypt. i have no idea why, but what you've shown me should be enough to get me started, thanks for the help :)

---

### Post by majoridiot on 2007-01-17
like an idiot, i gave you the wrong command.  what i told you is the command to unmount
truecrypt volumes. duh.

what you want is:

```
truecrypt -c  <path> 
```

it will prompt your for options, so be sure to have the man page up or printed to make sure 
you get exactly what you want.  if you want it to be a hidden volume, be sure to read the
man page. as a suggestion, start with a small (5-20MB) test directory first, as it does take some
time to encrypt.  once you get the right settings sussed and written down, then you can go
for a much larger truecrypt directory creation.

the nice thing about directories, is that if you mess it up, all you need to do is delete it.  when
you do entire partitions, undoing/redoing a 2-4+ hour encryption gets old...  ;)

---

### Post by dimeotane on 2007-02-12
I made a truecrypt file in my home directory.  But when I mount it the program makes me use sudo to mount it as root, and then I can only copy files into at as root.

How do I set this up so that once I've mounted it, i can copy files to it without being root?

---

