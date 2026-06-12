---
title: "Folder ownership and permissions"
date: 2016-04-15
forum: General Help
---

### Post by fbdonaldson on 2016-04-15
I have this problem. 
 
 
 As you can see below, 'MY FILES DATA' is locked away from me, accidently I think,
 containing quite a few files that are not showing up I suspect.
 
 
 I am now using Ubuntu 15.10 so how can I change the ownership and recombine the two  
 'DATA' folders?
 
 
 I have a SSD for the root directory and HDD for the data storage.
 
 
 /media/barry$ ls -l
 
 
 dr-x------  2 barry root  4096 Oct 26  2014 IRENE
 drwxr-xr-x  2 root  root  4096 Mar 12 16:58 MOVIE 1
 drwx------  2 root  root  4096 Mar 10 19:34 MY FILES DATA
 drwx------ 18 barry barry 4096 Apr  2 08:21 MY FILES DATA1

---

### Post by yancek on 2016-04-15
```
sudo chown -R barry "/media/barry/MY FILES DATA1" 		
```

The command above should do it.  Generally it is a bad idea to have spaces in directory names so in this case you will need quotes as shown.  How did you come to have two directories with almost identical names and have you checked them to see if the data is actually different in each of them?

---

### Post by Bucky Ball on 2016-04-15
Sorry to jump in here, but just double checking. Should your command be this, yancek?

> **yancek said:**
> ```
sudo chown -R barry:barry "/media/barry/MY FILES DATA1" 		
```

[QUOTE=yancek;13470928]Generally it is a bad idea to have spaces in directory names ...

Agreed. Avoid spaces. If you must use them, use_underscores_like_this. MY_FILES_DATA. ;)

---

### Post by bab1 on 2016-04-15
> **Bucky Ball said:**
> Sorry to jump in here, but just double checking. Should your command be this, yancek?

[QUOTE=yancek;13470928]```
sudo chown -R barry:barry "/media/barry/MY FILES DATA1" 		
```
[/QUOTE]
If you only have 1 argument (e.g. chown -R barry) then only the user is changed.  If you use 2 arguments (e.g. chown -R barry:barry) you change the owner and the user-group.  Either one will change the user.  If you need to change the user-group only you can use chgrp (chgrp <user-group>.I use chgrp all the time when I have multiple users that need to access the same directory.  I will set the user-group to something like this: *sudo chgrp sambashare /srv/share/public*

---

### Post by fbdonaldson on 2016-04-15
Good question.

I think it goes back a month or so when I was attempting to move a folder from the SSD that was filling up to the HDD. 

I tried to alter the T bird initiation file and then I noticed files not sighted and an additional MY DATA FILES (1). Point taken on the spaces thankyou.
AS I cannot access the original MDF, I don't what is in there but suspect it is the non-sighted files.

---

### Post by mc4man on 2016-04-16
I think he /she had the issue with My Files Data 
Anyway, slightly off topic  
My Files Data  is just the volume label given,  if it's 'bad'   why doesn't the System  use underscores for the created mountpoint?

---

### Post by fbdonaldson on 2016-04-16
It is the ownership of MY FILES DATA that I am after; you're pointing to MY FILES DATA1?

I will certainly be doing some name reappraisals when I get this sorted.

---

### Post by oldfred on 2016-04-16
Windows systems often have spaces, so auto mount automatically handles the spaces.
But if you are manually mounting you have to manage the spaces with either quoted or \040 escape code. Makes it complicated, or easier just to not use spaces.

---

### Post by fbdonaldson on 2016-04-16
I have removed the '1' from the name in the command and it worked so thanks for that.

---

### Post by ajgreeny on 2016-04-16
Just out of interest, and as I no longer use Windows, how does the command terminal (or whetever it's called in Windows) deal with spaces in file or folder names; do you have to use escape characters or quotation marks in that?

---

### Post by mcduck on 2016-04-16
> **ajgreeny said:**
> Just out of interest, and as I no longer use Windows, how does the command terminal (or whetever it's called in Windows) deal with spaces in file or folder names; do you have to use escape characters or quotation marks in that?

Depends on command, some of them are fine with spaces (for example "cd", since you can only move to one directory at a time). Others need escaping spaces or using quotes. Using Tab to autocomplete will always quote the path for you.

---

