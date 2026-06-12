---
title: "Keeps asking me for 7.10 disk"
date: 2007-10-23
forum: General Help
---

### Post by CoryMathews on 2007-10-23
Every time i try to install something new it keeps asking me to insert my ubuntu 7.10 disk that i installed the os with. It never did this in 7.04 and i actually dont have the cd for a few days because i let a buddy of mine borrow it so he wouldnt have to wait to dl. 

Anyways why  does it keep asking for the cd? Should'nt all the files have already been installed and stored somewhere?

---

### Post by por100pre1 on 2007-10-23
That behavior in Gutsy is by design.

```
gksudo software-properties-gtk
```

and uncheck the Ubuntu CD.

---

### Post by wolanIT on 2007-10-23
You have to insert** #** in **/etc/apt/sources.lis**t at begin of first  line:  ```
 #deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted   
```

Than```
 sudo apt-get update
```
And thats all.

---

### Post by rudeboyskunk on 2007-10-23
Or if you prefer a graphical, easy way, go to System>Administration>Software Sources and uncheck the cdrom from the list.  Click "Close" and then "Reload" when the window pops up, and voila!

---

### Post by CoryMathews on 2007-10-23
> **por100pre1 said:**
> That behavior in Gutsy is by design.

for security(the password isn't enough?) or annoyance? 

But thanks for the help. Other then this 7.10 has been great. thanks.

---

### Post by por100pre1 on 2007-10-23
> **CoryMathews said:**
> for security(the password isn't enough?) or annoyance? 

But thanks for the help. Other then this 7.10 has been great. thanks.

I think it is for saving some bandwidth using the disk as a local repository, not sure about it.

---

### Post by julep on 2007-10-23
This kind of behavior is not a feature in my book, but one of the top 10 reasons for hating Windows. "Now where the hell did I put that CD?"

./J

---

### Post by CoryMathews on 2007-10-23
> **julep said:**
> This kind of behavior is not a feature in my book, but one of the top 10 reasons for hating Windows. "Now where the hell did I put that CD?"

./J

lol agreed.

---

