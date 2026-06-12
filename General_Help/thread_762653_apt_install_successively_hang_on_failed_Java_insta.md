---
title: "apt install successively hang on failed Java installation"
date: 2008-04-22
forum: General Help
---

### Post by tefflox on 2008-04-22
[FONT=Arial][SIZE=3]**[COLOR=black][FONT=Fixedsys]I'm prompted to type 'no' to abort a javadoc install at each system update, twice per instance.  See screenshot.[/FONT]  [/COLOR]**[/SIZE][/FONT]

[[IMG]http://listenlight.net/media/java-install-error-sm.jpg[/IMG]]("http://listenlight.net/media/java-install-error.jpg")

---

### Post by tvtech on 2008-11-19
it appears that for some reason your update is not being given the correct permissions. try doing an update via terminal 
sudo -i 
aptitude update

sudo -i will give you a temporary lease of root until you close the terminal window or exit the lease.  mind you opening up root while online is ... umm well not recommended.

---

### Post by dcstar on 2008-11-19
> **tefflox said:**
> I'm prompted to type 'no' to abort a javadoc install at each system update, twice per instance.
........
Java installations require a manual licence acknowledgement, you should do this to ensure that you are prompted for it:
```
sudo dpkg-reconfigure debconf
```

---

### Post by ju2wheels on 2008-11-19
In order to install java doc you have to manually download the zip file and place it in the /temp folder when the installer stops at that point.

Have you done that?

---

### Post by anurgo on 2008-12-08
Check the following thread:

[http://ubuntuforums.org/showthread.php?t=840746&highlight=java+doc](http://ubuntuforums.org/showthread.php?t=840746&highlight=java+doc)

---

