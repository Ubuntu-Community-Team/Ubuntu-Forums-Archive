---
title: "delete a folder"
date: 2006-08-12
forum: General Help
---

### Post by Alie on 2006-08-12
hi,

i have a problem when delete a folder in ubuntu.

i show an error message "Error while moving.", "Cannot move "/new folder" to the trash because you do not have permissions to change it or its parent folder."

thanks in advance

---

### Post by s6dalane on 2006-08-12
Use the terminal:
> sudo rm -dr <folder>

---

### Post by njzillest on 2006-08-12
You have to change the user. MOst the time, it sunder root. TO change user try 

```
su root
```

if you dont know the password, do this FIRST

```
sudo passwd root ----
```

when you su as root, use 

```
sudo rm -dr <folder>  
```

---

### Post by s6dalane on 2006-08-12
No, you don't need to switch to root. In fact, it is recommended not to!
You can delete the folder(s) with only one command.

---

### Post by Ramses de Norre on 2006-08-12
Use sudo instead of logging in as root, just ```
sudo rm -rf "new folder"
```

---

### Post by Alie on 2006-08-12
how to delete a folder with white space.

for example ->  "my documents"

---

### Post by Ramses de Norre on 2006-08-12
Set it between " ("my documents") or use a backslash to escape the space function (my\ documents).

---

### Post by ifokkema on 2006-08-12
> **njzillest said:**
> 
```
su root
```

if you dont know the password, do this FIRST

```
sudo passwd root ----
```

As mentioned by others, don't enable root like that.
If you're really really tired of having to use sudo all the time, you can always use
```
sudo su -
```
and be 'root' temporarely. Root still doesn't have a password then, leaving your system as secure as Ubuntu means to.

---

