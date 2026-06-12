---
title: "[SOLVED] Google Desktop Install Issue"
date: 2008-02-26
forum: General Help
---

### Post by Flashgordon20 on 2008-02-26
I attempted to install google desktop through a .deb package. The installation hanged halfway through and I canceled it. This was a big mistake because now  every time I try to install updates I get an error message that states:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 I ran " dpkg --configure -a" and it begins to install google desktop again. It never finishes and the installation hangs the same way it did when I first tried to install it. Any suggestions would be helpful. I can't install any security updates until this is fixed because the update manager keeps giving me the same error message. Thank You

---

### Post by Flashgordon20 on 2008-02-26
Help? Anyone have any ideas?

---

### Post by y-lee on 2008-02-26
Try
```
sudo dpkg --configure -a
``` 

if that doesn't work post an errors here if you can.

---

### Post by Flashgordon20 on 2008-02-26
Thanks. I ran the command using sudo and I get the following in the terminal

> stephen@stephen-laptop:~$ sudo dpkg --configure -a
[sudo] password for stephen:
Setting up google-desktop-linux (1.1.1.0075) ...


That" setting up google desktop linux"  never goes away. I have let it run for over 30 minutes sometimes. Eventually I get tired of it and close the terminal window. I don't think it should be taking that long. It's like the installation is stuck somehow.

---

### Post by y-lee on 2008-02-26
Does synaptic package manager and the upgrade manager still work? 

how about doing this first 

```
sudo apt-get update
```

And where did you get this deb?

If synaptic is working try [gOS on Ubuntu]("http://zebardast.wordpress.com/2007/12/18/how-to-install-gos-on-ubuntu-gutsy-gibbon/")

---

### Post by y-lee on 2008-02-26
> That" setting up google desktop linux" never goes away. I have let it run for over 30 minutes sometimes. Eventually I get tired of it and close the terminal window. I don't think it should be taking that long. It's like the installation is stuck somehow.

Also note installing gOS is installing a complete desktop environment it would take me probably hrs at my net speed. It is like downloading ubuntus installation cd ISO.

---

### Post by Flashgordon20 on 2008-02-26
The update manage shows up like normal. When I type in my root password to install up dates I get the same error message
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I start synaptic. I get the same message. I think it believes I'm still trying to install Google desktop, so no other package manager can run at the same time. I got the .deb from the official google site. [http://desktop.google.com/linux/](http://desktop.google.com/linux/)

---

### Post by Flashgordon20 on 2008-02-26
> **y-lee said:**
> Also note installing gOS is installing a complete desktop environment it would take me probably hrs at my net speed. It is like downloading ubuntus installation cd ISO.

Synaptic wont start. I get a pop up window with the same error message.
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


---

### Post by y-lee on 2008-02-26
Ok sadly something is broke :(


Please post the output of

```
ls -la /var/lib/dpkg/triggers
```

---

### Post by Flashgordon20 on 2008-02-26
I think I'm doomed to do a reinstall but here is what I got:

> stephen@stephen-laptop:~$ ls -la /var/lib/dpkg/triggers
total 16
drwxr-xr-x 2 root root 4096 2008-02-16 12:11 .
drwxr-xr-x 8 root root 4096 2008-02-26 22:57 ..
-rw-r--r-- 1 root root    6 2007-11-05 23:37 ldconfig
-rw------- 1 root root    0 2008-02-26 22:57 Lock
-rw-r--r-- 1 root root    0 2008-02-16 12:11 Unincorp
-rw-r--r-- 1 root root   16 2007-10-06 09:03 update-initramfs
stephen@stephen-laptop:~$ 

---

### Post by y-lee on 2008-02-26
Hmm, what is the output of

```
cat /var/lib/dpkg/triggers/Unincorp
```

---

### Post by Flashgordon20 on 2008-02-26
Nothing comes up. 
> stephen@stephen-laptop:~$ cat /var/lib/dpkg/triggers/Unincorp
stephen@stephen-laptop:~$ 


---

### Post by y-lee on 2008-02-26
> Nothing comes up.

Well that is good because it is supposed to be empty. Sometimes [it is not ]("http://ubuntuforums.org/showthread.php?t=681675&page=2")in cases like yours and you have you have to edit it and make it empty.

Sadly I got to go to bed. If no one helps ya by tomorrow I'll do some more research and see what i can come up with. It doesn't help much but this problem has been reported as a bug several times :(

---

### Post by Flashgordon20 on 2008-02-26
I Appreciate any help. Thank you

---

### Post by Flashgordon20 on 2008-03-03
Guess there is no solution to this one except to do a complete reinstall?

---

### Post by Flashgordon20 on 2008-03-07
Removed Google Desktop Files from the /opt directory.
Then reran sudo dpkg --configure -a

got the following output

> stephen@stephen-laptop:~$ sudo dpkg --configure -a
[sudo] password for stephen:
Setting up google-desktop-linux (1.1.1.0075) ...
File /opt/google/desktop/.gdl_installed_files is missing!
dpkg: error processing google-desktop-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 google-desktop-linux



It's no longer stuck trying to install the .deb package.

All better now.

---

### Post by luvit on 2008-03-14
That software is awesome! I use it everyday!
concise instructions for installing [_[COLOR=RoyalBlue]Google Toolbar[/COLOR]_]("http://www.yay4u.com/2008/03/installing-google-toolbar-on-ubuntu.html")
concise instructions for installing [_[COLOR=RoyalBlue]Google Desktop[/COLOR]_]("http://www.yay4u.com/2008/03/google-desktop-for-linux-firefox.html")
for real beginners ...I hope it's useful!;)

---

