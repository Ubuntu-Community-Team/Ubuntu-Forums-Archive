---
title: "Samba - User added to smbpasswd on login"
date: 2013-08-05
forum: General Help
---

### Post by wayne2 on 2013-08-05
Hi,

I have set up samba on my home network and want to have no username/password prompt issued to the windows pc's that connect to the shares. 

I have got this working apart from one small detail, each time i login with my username "wayne"  to the server, then "wayne" is added to the samba users list as verified with a "pdbedit -L" and i will then be required to enter a username and password to access the shares.

a "pdbedit -x -u wayne" will remove my user name from samba and hence fix my issue. but i'm not sure what triggers the automatic addition of my username so that i can stop it. Can anybody help?

Thanks,
Wayne

---

### Post by wayne2 on 2013-08-06
Ok, managed to fix this myself (go me!)

incase any other beginners struggle with this -

it is pam that is responsible for the account generation and to disable i had to comment out the line:

#auth   optional                        pam_smbpass.so migrate

in /etc/pam.d/common-auth

---

### Post by mghorcik on 2013-08-08
how to  easily install and config samba server please help me.  i am absolutly beginer with terminal working.:)

---

### Post by slickymaster on 2013-08-08
> **mghorcik said:**
> how to  easily install and config samba server please help me.  i am absolutly beginer with terminal working.:)

[Install Samba Server on Ubuntu]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")
[Share Ubuntu Home Directories using Samba]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/")

---

### Post by mghorcik on 2013-08-08
thank you verry much

---

### Post by Morbius1 on 2013-08-08
> **wayne2 said:**
> Ok, managed to fix this myself (go me!)

incase any other beginners struggle with this -

it is pam that is responsible for the account generation and to disable i had to comment out the line:

#auth   optional                        pam_smbpass.so migrate

in /etc/pam.d/common-auth
The other way to accomplish this is to remove one package:
```
sudo apt-get remove libpam-smbpass
```
It's an insane little utility that has only one function in life: It takes the list of local login users, adds then to the samba password database and makes their samba password match their local login password. It does one other thing ( which nearly drove me insane before I figured out what was happening ): If you change the samba password for a user it's good for that session. When you reboot the server the samba password is overridden by libpam-smbpass with the users login password again.

If you were the administrator of the box you might want that to happen but it should be something the administrator consciously decides to do not something that's the default.

---

