---
title: "Can I retrieve serial key from unbootable XP?"
date: 2007-06-22
forum: General Help
---

### Post by bronze on 2007-06-22
The thing is,
I have a partition, with the file structure of a normal windows XP install, but I didn't really INSTALL it, so I can't boot it. I just copied the files onto the partition, and now I'm going to install it, but I can't find the key any longer. What I'm asking is if I can retrieve the key from those files. Can I somehow access the registry and look in there?

Any suggestions are greatly appreciated.

-bronze

---

### Post by CrispyFried on 2007-06-22
if you peel xp off one computer and drop it into another it almost certainly wont work - different hardware and such. it needs to be installed on the computer it runs on.

I think the key can be found, at least ive heard of programs that will find it, but I cant recall what they are.

---

### Post by abn91c on 2007-06-22
find the windows registry file, the key is there, not sure how to review with ohter OS, probably with the linux note pad equivalent??

---

### Post by Motoxrdude on 2007-06-22
You can open windows registrys with wine.
Then just go ```
HKEY_LOCALMACHINE\ SOFTWARE\ Microsoft\ WindowsNT\ CurrentVersion.
```  then select 'ProductId' and the key is from digit 6-15

---

### Post by bronze on 2007-06-22
I know where in the registry to look, but I don't know how to import the registry into regedit. Do you know?

---

