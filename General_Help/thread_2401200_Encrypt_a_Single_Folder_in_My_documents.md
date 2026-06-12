---
title: "Encrypt a Single Folder in My documents"
date: 2018-09-14
forum: General Help
---

### Post by mountainman70 on 2018-09-14
What is the best way to Encrypt a Single Folder in My documents?

---

### Post by hrsetrdr on 2018-09-14
> **mountainman70 said:**
> What is the best way to Encrypt a Single Folder in My documents?

Compress it, create a tar file, most Ubuntu DEs have a right click compress feature.    In terminal "cd" to the parent directory that the folder you want to encrypt resides.    Using [ccrypt]("http://ccrypt.sourceforge.net/ccrypt.html") you can then type:
```
 ccrypt your folder.tar.gz
```
 [enter]
....then type a password, press enter, and re-type password to confirm.

Edit:  you can use other encryption tools of course, I just used ccrypt as an example, you would have to install it, it's in the repos.   I used to use bcrypt, but I think all Debian based distros have disabled the ability to create a new encrypted file, but left decryption enabled for an existing file.

---

### Post by Dennis N on 2018-09-15
> **mountainman70 said:**
> What is the best way to Encrypt a Single Folder in My documents?

Files (nautilus) can encrypt a folder by right-click and selecting encrypt from the context menu. You need to have have a gpg public/private key pair in the gpg keyring and it will use those keys. For a folder, you have the option to create an archive of the folder and encrypt, or to encrypt files individually.

To get this option in Files context menu, install **seahorse-nautilus**.

---

### Post by HermanAB on 2018-09-15
Note that while that will protect you against your little brother, it will not do much to a determined adversary.  There are many reasons why 'full disk encryption' is the only way that is really worth the effort.

---

### Post by mountainman70 on 2018-09-15
Been away for a while. Thanks for the replies.

---

