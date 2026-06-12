---
title: "lost places"
date: 2014-08-20
forum: General Help
---

### Post by harlie on 2014-08-20
I am using ubuntu 14.04 and accidently sent the pictures folder from the places menu to the trash, before I realised I  had erased it I had already emptied the trash folder. How can I reinstall the folder in places. I don't have a disk for 14.04, and if I did I would not know how to reinstall just the places menu. I have backups of the lost photos.
Can someone help this dummy?

Thanks
harlie

---

### Post by sudodus on 2014-08-20
I think you can simply re-create a folder in your home folder. With the terminal window it would be two command lines

```
cd
mkdir Pictures
```

---

### Post by harlie on 2014-08-21
thank you I will do this.

---

### Post by mcduck on 2014-08-21
If you already logged out after removng the directory, it might have also been removed from the XDG user directories file. In that case simply re-creating the directory might not add it to the Places. If this is the case, then check the *~/.config/user-dirs.dirs* file, and make sure it has the following line:
```
XDG_PICTURES_DIR="$HOME/Pictures"
```
If the line is missing or doesn't have the correct path, just fix it, save the file, and log out & back again and the directory should be recognised.

---

### Post by harlie on 2014-08-21
the fix suggested by sududus didn't work so I will try what mcduck reccomends.
with 
cd
mkdir
 it says the directory is already there but I am not able to access it in the terminal

---

### Post by sudodus on 2014-08-22
Please print a long list the content of your home directory and post it in a reply

```
ls -l ~
```

or if you can't find the tilde key

```
ls -l $HOME
```

It should show the ownership and permissions, and could help us solve the problem.

---

### Post by harlie on 2014-08-22
thanks to both of you for yous suggestions I just realised the pictures folder in places was not erased i somehow had changed the name of it. Once I renamed it pictures all is well. Again thanks for your time.

harlie

---

