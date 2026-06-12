---
title: "passing options to automount"
date: 2007-05-30
forum: General Help
---

### Post by fourbissime on 2007-05-30
Hi there.

Because of an incompatibility problem between fat32 and ext3, I want to add an option when my nifty mp3 player is mounted.

I found that there is an interface to do that by right clicking on my drive's icon. So I added my option.

Alas, I put the wrong option and now the system doesn't want to mount my drive anymore - thus, the drive icon doesn't appear anymore, and the GUI where I set up the option in the first place is not accessible either.

the error message is very clear :
```
FAT: Unrecognized mount option "codepage=mixed" or missing value
```

(I should have put "shortname=mixed")

So my question is : where is this damn option stored in my system so I can get rid of it manually ? I didn't find much grepping around ...

---

### Post by fourbissime on 2007-05-30
OK, found it.

it was in 
```
.gconf/system/
```

---

