---
title: "Password Lock a folder"
date: 2007-03-21
forum: General Help
---

### Post by RudolfMDLT on 2007-03-21
Hi there,

I have certain files and folders that need to be locked away - In windows I zipped the folder with a password. How do I do the same in Linux? If there is an alternative to zipping the folder I'll be all for it!

Thanks,

Rudolf

---

### Post by pebo on 2007-03-21
Couldn't you do that by changing the permissions? eg
```
chmod 700 <your_dir>
```That way only you as user would have access to the folder.
HTH

---

### Post by RudolfMDLT on 2007-03-21
I thought about that but I sometimes borrow people my Laptop at varsity and then they use my login. I just need 2 or 3 folders to be private.

---

### Post by yopnono on 2007-03-21
There is no way to password protect a folder (that I know of). However you can like in windows, password protect a compressed file (zip,rar,etc,etc).

Or use encryption like gpg ccrypt, etc, etc.

---

### Post by nikhilk on 2007-03-21
The latest 7zip beta version (4.44) supports WinZip compatible AES-256 encryption for ZIP archives, you can try that.

---

### Post by nsilva on 2008-06-28
I wanted to do exactly the same things, what I ended up doing was creating a different user, lets say Secured. 

A change ownership of the folder to that user, then changing permission with SUDO is piece of cake...

Let me know if you ended up doing something different..

---

### Post by nsilva on 2008-06-28
Or even easier, depending on how savvy are your intruders, you can just take off you "read" access to the folder, so when u click on it, it gives u an error... then when u need it, just change the permissions...

I'm just trying to combat my Windows retarded friends

---

