---
title: "[SOLVED] Big trouble with my home folder"
date: 2007-11-23
forum: General Help
---

### Post by endless_dark on 2007-11-23
I downloaded an install sh script,it asked me to set a folder for installation and I typed my local folder. Then things gone very bad...
After rebooting I couldnt login with my user account, it was something like a file permissions, after a while I solved the problem and retry, but there was a similar permission problem with another file. 
So I did sudo chmod -R 644 /home/user and I think that was my second big mistake. Now I cant enter with my user account and if i browse that local folder as another user it says its full of unknown kind of files :frown:

I really need to save at least one folder I had there




PD. Sorry for my english:oops:

---

### Post by volanin on 2007-11-23
Try this:
```
$ find /home/user -type d -exec chmod 755 {} \;
$ find /home/user -type f -exec chmod 644 {} \;
```

---

### Post by taurus on 2007-11-23
Boot into recovery mode from GRUB menu and run

```
chmod -R 755 /home/user
chmod 600 /home/user/.dmrc
shutdown -r now
```
Now, see if you can log in with your user username.

---

### Post by endless_dark on 2007-11-23
> **taurus said:**
> Boot into recovery mode from GRUB menu and run

```
chmod -R 755 /home/user
chmod 600 /home/user/.dmrc
shutdown -r now
```
Now, see if you can log in with your user username.

I made that the first time that I couldn't log in with my user. I solved that but I had problems with a lot more files

> **volanin said:**
> Try this:
```
$ find /home/user -type d -exec chmod 755 {} \;
$ find /home/user -type f -exec chmod 644 {} \;
```

That solved my problem. You are my new hero!
So, I think that what this commands do is to list all the executable files in /home/user and give them execution permission. And the other does the same but other kind of files and give them read/write permisson, right?

Obrigado!!!!

---

### Post by volanin on 2007-11-23
De nada!
:)

Indeed, you are ALMOST right.
The point is, unless you install programs yourself without using apt-get, there should be no EXECUTABLES
in your home folder. So you can, in practice, assume that all files are NORMAL, NON-EXECUTABLE files.

So these commands just restore the default permissions for all files *(-type f)* to the standard 644.
And also restore the default permissions for all directories *(-type d)* to the standard 755.
This should restore your home to a usable state. Glad it worked!
:)

---

### Post by theredspecial on 2007-11-24
this worked for my problem as well: gracias
(my post was at [http://ubuntuforums.org/showthread.php?p=3826495#post3826495](http://ubuntuforums.org/showthread.php?p=3826495#post3826495))

---

