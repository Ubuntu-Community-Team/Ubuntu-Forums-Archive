---
title: "[SOLVED] System becoming Unuasable please take the time to help."
date: 2008-06-14
forum: General Help
---

### Post by natman3400 on 2008-06-14
When i try to install soft ware in add/remove or when i try to launch synaptic i get this error:
Quote:
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
I am not new or anything, its just this has never happened to me.
It wont even let me install updates.
Please help me. This Ubuntu 8.04 dell c600 is all i have.
Read the whole thing and please no random guesses.

---

### Post by Fingel on 2008-06-14
try typing "sudo apt-get install virtualbox" in a terminal and tell us what happens.

---

### Post by natman3400 on 2008-06-14
root@natman3400-laptop:~# sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
root@natman3400-laptop:~# 
 is what it said

---

### Post by PmDematagoda on 2008-06-14
Do:-
```
sudo apt-get remove virtualbox
```
once that finishes reinstall Virtualbox using the deb file you downloaded from the web site.

---

### Post by natman3400 on 2008-06-14
it says 
root@natman3400-laptop:~# sudo apt-get remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by ikki_72 on 2008-06-14
how about
```
sudo apt-get clean
```

then
```
sudo apt-get update
```

---

### Post by natman3400 on 2008-06-14
synaptic still says
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by natman3400 on 2008-06-14
could i remove the files from disk my self?

---

### Post by kalesh7 on 2008-06-14
just remove virtualbox but do not reinstall and see if problem persists

```
sudo apt-get remove virtualbox
``` 

you probably could remove files and edit whatever file has the data for installed programs but it would need a real expert to tell you how to do that. I wouldn't be messing with those really.

---

### Post by kalesh7 on 2008-06-14
[SIZE="4"][COLOR="Red"]
WARNING
use the following at your own risk. I am not sure what will happen and I am only giving an option that could be used if the only other option is a reinstall, so make sure to have all backups just as you were doing a reinstall, and this may reduce system stability, even upto making your os unusuable (or it may do nothing) 
[/COLOR][/SIZE]
type this in terminal
```

sudo gedit /var/lib/dpkg/status 

```
find the section with virtualbox and delete it
save file
check for problem

once again this is a dangerous and potentially disastrous action. do NOT do it unless you have no other option, and if you do it make sure to have all backups.

---

### Post by PmDematagoda on 2008-06-14
You don't have to do that, just execute:-
```
sudo dpkg -remove-reinstreq virtualbox
```
and that should do it.

---

### Post by natman3400 on 2008-06-14
that didn't work:confused::( Mr.Admin person

---

### Post by natman3400 on 2008-06-14
kalesh7 you are a genius that worked perfectly

---

