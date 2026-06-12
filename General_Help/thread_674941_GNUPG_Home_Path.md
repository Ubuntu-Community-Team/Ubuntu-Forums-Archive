---
title: "GNUPG Home Path"
date: 2008-01-22
forum: General Help
---

### Post by bjr149 on 2008-01-22
I can't seem to get the directory to change where gpg looks for the keyring files. 

I ran the following 

C:\GNUPG>gpg --homedir C:\GNUPG\ 
gpg: keyring `C:/GNUPG/\secring.gpg' created 
gpg: keyring `C:/GNUPG/\pubring.gpg' created 
gpg: Go ahead and type your message ... 

Then when I run --list-keys its still points to the original directory. 

C:\GNUPG>gpg --list-keys 
C:/Documents and Settings/webmethods/Application Data/gnupg\pubring.gpg 
-------------------------------------------------------------------------------- 


What am I doing wrong? 

Thanks.

---

### Post by kevdog on 2008-01-22
Are you using gnupg on windows or on ubuntu?

---

