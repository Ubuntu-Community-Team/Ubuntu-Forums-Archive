---
title: "Startup error says something about a file being ignored."
date: 2008-06-25
forum: General Help
---

### Post by JaxJagsfan on 2008-06-25
Here is my startup error everytime Ubuntu loads...

"User's $HOME/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Has anyone seen this problem and how do I fix it? :confused:

---

### Post by John.Klockenkemper on 2008-06-25
[http://ubuntuforums.org/showthread.php?p=479186#post479186](http://ubuntuforums.org/showthread.php?p=479186#post479186)

---

### Post by drs305 on 2008-06-25
I'd try the 644 first. I think the post above starts with 700.

```
chmod 644 /home/**username**/.dmrc 
```

If your home permissions are messed up:
```
sudo chown -R **username:username** /home/**username**
chmod -R 755 /home/**username**
chmod 644 /home/**username**/.dmrc 

```

reboot

---

### Post by JaxJagsfan on 2008-06-25
```
 sudo chown -R **username:username** /home/**username**
chmod -R 755 /home/**username**
chmod 644 /home/**username**/.dmrc 

```

I tried that in terminal and here's what it said below,

username@username-desktop:~$ sudo chown -R username:username /home/username
chown: cannot access `/home/username/.gvfs': Permission denied
username@username-desktop:~$

:confused:

---

### Post by drs305 on 2008-06-25
> **JaxJagsfan said:**
> ```
 sudo chown -R **username:username** /home/**username**
chmod -R 755 /home/**username**
chmod 644 /home/**username**/.dmrc 

```

I tried that in terminal and here's what it said below,

username@username-desktop:~$ sudo chown -R username:username /home/username
chown: cannot access `/home/username/.gvfs': Permission denied
username@username-desktop:~$

:confused:

Did you replace **username** with YOUR username? Sorry if it wasn't clear.

---

### Post by JaxJagsfan on 2008-06-25
Yes I did replace username with my own username.

---

### Post by drs305 on 2008-06-25
If you were able to run the first command successfully, you probably have to reboot your machine:
```
chmod 644 /home/username/.dmrc
```

---

### Post by JaxJagsfan on 2008-06-25
Obviously this terminal error is the problem.

chown: cannot access `/home/username/.gvfs': Permission denied

For some reason .gvfs is locked.

---

### Post by JaxJagsfan on 2008-06-25
I went back and retyped the first command chmod 644 /home/username/.dmrc then rebooted.  My error is now gone! :-D

I did not know I had to reboot the computer immediately after doing the command.  Thanks for your assistance, drs305! 8)

---

