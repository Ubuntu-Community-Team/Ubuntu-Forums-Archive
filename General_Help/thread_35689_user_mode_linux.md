---
title: "user mode linux"
date: 2005-05-19
forum: General Help
---

### Post by kmohanas on 2005-05-19
hi everyone,

i am trying to install user-mode-linux (uml) on hoary. Has anyone installed UML before or is UML available in the repositories ? 

I am new to debain based systems and still learning to use apt-get. I have to look up the command to search the repositories for packages. If someone could just spit out the command it would be helpful

thanks
karthik

---

### Post by JonahRowley on 2005-05-20
To search:
```
apt-cache search user-mode-linux
```
To see more info about the package:
```
apt-cache show user-mode-linux
```
To install it:
```
sudo apt-get install user-mode-linux
```

---

### Post by Ejunkie on 2005-05-20
i tryed to but it didnt worked

what repository's do i need.

---

### Post by JonahRowley on 2005-05-20
Hmm..  that's strange.  I could have sworn I saw it when I searched, but it looks like I saw user-mode-linux-doc.  Sorry, it doesn't look like it's in there, I have both universe and multiverse, though I don't see why it would be in multiverse.  I wonder why it's not in universe?

---

### Post by kmohanas on 2005-05-20
Thanks for the tips jonahrowley. 

I read from the UML docs that it is included by default in the 2.6.x kernels. Does this mean that I dont have to download the UML patch and can just compile any downloaded kernel source using the UML flags provided in their documentation ?

It would be helpful if anyone who has installed UML on Hoary could shed some light on this ?

TIA
karthik

---

### Post by shmk on 2005-06-01
[QUOTE=kmohanas]Thanks for the tips jonahrowley. 

I read from the UML docs that it is included by default in the 2.6.x kernels. Does this mean that I dont have to download the UML patch and can just compile any downloaded kernel source using the UML flags provided in their documentation ?

It would be helpful if anyone who has installed UML on Hoary could shed some light on this ?

TIA
karthik[/QUOTE]
 I have this problem too,
someone give us a hand ! :)

---

### Post by hewhocutsdown on 2006-04-27
Did anyone ever figure out stuff regarding UML? I'm running Dapper and looking for some docs to help me play with this...

---

