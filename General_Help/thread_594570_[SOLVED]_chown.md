---
title: "[SOLVED] chown"
date: 2007-10-28
forum: General Help
---

### Post by gishaust on 2007-10-28
Hi everyone


I have just installed, formated and mount a new hard drive so that i cam backup data. My problem is that I created a folder call datahome that is owner by root. and the current permissions on it are 666 it looks like this 

drwxr -xr -x 2 666 root 4096 (date time) datahome

As a newbie to permissions  I think it allows me to read write and execute
The command I used was sudo chown 666 /data/datahome.

But it will not let me copy data that I have in my home folder all I get is you do not have permission to write to this folder.

What am I doing wrong

thanks gishaust

---

### Post by PmDematagoda on 2007-10-28
You are supposed to issue "chown" like this:-
```

sudo chown username:usergroup /place/to/own
```

---

### Post by gishaust on 2007-10-28
Thanks for the rely

So as an example  i would do this
```
sudo chown root:root 666 /data/datahome 
```
Is that what you mean

---

### Post by PmDematagoda on 2007-10-28
If you want to read and write to the drive, then you need:-

```
sudo chown yourusername:yourgroup /place/to/own
```

The 666 is not needed.

---

### Post by gishaust on 2007-10-28
thankyou it works great

---

### Post by PmDematagoda on 2007-10-28
Glad to help:).

---

### Post by gishaust on 2007-10-28
Sorry
It works great but I cant create a new folder inside datahome. But  I create it on the desktop and then copy it works fine. What permission do I have to change

gishaust

---

### Post by PmDematagoda on 2007-10-28
You can't make folders in the drive, yet you can copy one to it?

---

### Post by gishaust on 2007-10-28
PmDematagoda's Avatar  	

Yes if I right click into the datahome folder it won't allow me to make a new folder. But  on the desktop I can right click make a folder and copy it into the new drive.

I wrote this and then decided to give it one more try. I gave it three goes and on the third guess what.!!!!! It worked. 

Let me try it again!!!! Yep it works. Is this where I walk away quitely and say, i don't know.

thanks for  your help again

---

### Post by PmDematagoda on 2007-10-28
Ok, glad to see that problem was finally and officially solved:). Could you mark this thread solved using Thread Tools so that it could benefit others?

---

