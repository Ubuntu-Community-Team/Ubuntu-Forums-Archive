---
title: "Partition format?"
date: 2008-05-13
forum: General Help
---

### Post by -fedexer- on 2008-05-13
Hello again,

I was wondering what format the partition linux is to be installed in is to be, or whether or not it is to be formatted at all?

Thanks
-fedexer-

---

### Post by loserboy on 2008-05-13
this should explain it pretty well [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

are you using the whole HD for linux or do you have windows as well

---

### Post by Kevbert on 2008-05-13
ext3 normally.

---

### Post by Oldsoldier2003 on 2008-05-13
nvm wrong tab!

---

### Post by -fedexer- on 2008-05-13
> are you using the whole HD for linux or do you have windows as well 

I created a 40gb patition for linux, i primarily have windows installed.

---

### Post by crtlbreak on 2008-05-13
Format is 
#mkfs 
in linux - you will also need to specify the type (ext2/3, msdos, riserfs?) check
#man mkfs 
[COLOR="Red"]Remember[/COLOR] this step is normally followed by a whole lot of 
[COLOR="Red"]**(*^"%£)*^$"£_&%¬!_% **[/COLOR]and then realising the data is lost forever.
regards

---

### Post by -fedexer- on 2008-05-13
> **crtlbreak said:**
> Format is 
#mkfs 
in linux - you will also need to specify the type (ext2/3, msdos, riserfs?) check
#man mkfs 
[COLOR="Red"]Remember[/COLOR] this step is normally followed by a whole lot of 
[COLOR="Red"]**(*^"%£)*^$"£_&%¬!_% **[/COLOR]and then realising the data is lost forever.
regards

ehh? rephrase that?

---

### Post by loserboy on 2008-05-13
> **-fedexer- said:**
> ehh? rephrase that?

lol, darn the cli lovers
j/k

---

### Post by loserboy on 2008-05-13
basically you are just gonna shrink the windows partition, and make 2 new ones (or 3 if you want a seperate /home)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

try this for a more graphical explanation

---

