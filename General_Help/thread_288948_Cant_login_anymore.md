---
title: "Cant login anymore"
date: 2006-10-30
forum: General Help
---

### Post by klep on 2006-10-30
Hello, 

I camr to login to ubuntu edgy today and cant. I type in my login and password, it begins to login (the screen goes brown and the icon turns to busy) but then it brings up the login screen again. 

ive done the whole rename ICEauthoity and try logging in again, no dice. Same with adding a new user.

~/.xsession-errors spouts loads of errors about Azureus. Last night before I shut off the PC (the last time it was working) all my azureus downloads stopped due to lack of disk space. I assume this is no coincidence. Thing is, Azureus shouldnt be starting up when i bott up the pc so i dont know why it is stopping me from logging in.

I really want to start using ubuntu more but this is pretty ridiculous.

Anyone know what to do?

Cheers

---

### Post by Kateikyoushi on 2006-10-30
Isn't the partition still full ?

---

### Post by dbott67 on 2006-10-30
Try booting into failsafe mode (or failsafe terminal) and deleting / moving some files (not system files, either... :) --- just some large mutli-media files or ISOs if you can).  Try and free up a few hundred megabytes and then try again.

-Dave

---

### Post by dentaku65 on 2006-10-30
try to boot in recovery mode and free up space:

```
apt-get clean
```

---

### Post by klep on 2006-10-30
Hello everyone. Thank you all for your speedy replies. I ctrl-alt-f1'ed and deleted a large directory that I had begun downloading using Azureus. Luckily they had not got very far but because Azureus pre-allocates they took up a lot of space.

My quesytion is this: Where does the blame lie for this? I really want to start using ubuntu heavily but I think that locking you out of the desktop environment when your disk gets full to be completely ridiculous. Is this GNOME's fault? Azureus? Is there any way to protect against this sort of thing short of keeping a constant eye on disk space?


Thank you all very much for your helpful replies. 

Cheers

---

### Post by Kateikyoushi on 2006-10-30
Happened to me once as well and learned from it, then I also wondered about the same thing, the best would be to save a few MB where users can't write so this couldn't happen, or at least a warning about the partition being full. 

Windows doesn't behave well either on a full partition.
I do not know whom to blame but file a bug maybe they recommend something.

---

### Post by k5787 on 2007-05-13
hello day everyone..my question is how do you access your home folder when you aren't able to log in because it says you are at a 100% usage. how can you get in and delete the necessary files

---

### Post by dbott67 on 2007-05-16
Can you login in safe mode (terminal)?

---

