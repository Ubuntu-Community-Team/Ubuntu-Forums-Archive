---
title: "Can't login into ubuntu - keeps coming back to login screen"
date: 2014-09-21
forum: General Help
---

### Post by goghvv on 2014-09-21
Hi.  
I'v been running dual boot on my machine (Windows 7 along side Ubuntu 14.04) for a couple of months now, and this morning, when I tried to login to my user in ubuntu, I find out that it keeps sending me back to the login screen whenever I enter my password, instead of sending me to the desktop.
I've searched Google for "Ubuntu can't login", and found many relevant results (including here in this forum) from people experiencing the same problem,
but I tried everything they've been suggested, and nothing seems to work!

Following the suggested solutions to others, this is what I tried to do, after hitting Ctrl+Alt+F2 and gaining access to the console:

[LIST]
[*]Setting the permissions on the home directory - even though I didn't have to, it was already rwxrwxrwx - it seems to work for some. 
[*]Reinstalling ubuntu-desktop package with *sudo apt-get install --reinstall ubuntu-desktop* 
[*]Setting the premissions on the /tmp directory to 777 
[*]*sudo apt-get install ubuntu-session* - but it says that it's already the newest version 
[*]*rm ~/.Xauthority ~/.ICEauthority* to remove these both files 
[/LIST]


Unfortunately, none of the above suggested solutions solved the problem.
Doe's anyone have more suggestions?
If not, can Ubuntu be completely reinstalled through the console?

---

### Post by blnl on 2014-09-21
What was the last thing that you did before this problem occurred?

---

### Post by goghvv on 2014-09-21
I remember installing GDebi Package Installer from the Ubuntu Software Center, and then installing teamviewer9 (downloaded the .deb file from their site, and then used GDebi to install it).
I also remember installing MySql server for both the client and server side: *sudo apt-get install mysql-server* and *sudo apt-get install mysql-client*,
then downloading Apache Tomcat 7 (downloaded the tar.gz file from [here]("http://tomcat.apache.org/download-70.cgi")), no installation needed for it, I just ran the server through the console after downloading it.
This was all the day before it happened. 
Do you think it has something to do with my problem?

---

### Post by blnl on 2014-09-21
I'm not 100% sure, but it might have to do something with your problem.
What I usually do when a sudden problem surfaces, is back-trace my steps and remove all suspect packages.

You can search the apt history [COLOR="#0000FF"]/var/log/apt/history.log[/COLOR] to find which packages that are installed with apt-get. Also look at [COLOR="#0000FF"]/var/log/dpkg.log[/COLOR] to find the packages installed with dpkg.
Then remove all suspect packages (or packages installed after a certain date)
```
sudo apt-get purge <package-name>
```

---

### Post by goghvv on 2014-09-21
I don't mind removing these packages. In fact, I don't need them anymore (I used them to test a once-off thing).
I'll try to remove them as you suggested and will post back.
Thank you so much for the help!

---

### Post by goghvv on 2014-09-21
Nope. :(
I removed *mysql-server* and *mysql-client* packages, but it didn't help...

---

### Post by blnl on 2014-09-21
Then create a new user and try to log-in as another user.
```
sudo adduser <newuser>
```
[LIST]
[*]If you are able to log-in as another user then something is wrong with you user configuration.
[*]If another user experiences same issue then something is wrong with the system.
[*]
[/LIST]

Let me know which one it is, then we can plan next step...

---

### Post by Impavidus on 2014-09-21
Before creating a new user, check whether you can login with the guest account. If you can, the problem is with your user files.
> **goghvv said:**
> Hi.  
I'v been running dual boot on my machine (Windows 7 along side Ubuntu 14.04) for a couple of months now, and this morning, when I tried to login to my user in ubuntu, I find out that it keeps sending me back to the login screen whenever I enter my password, instead of sending me to the desktop.
I've searched Google for "Ubuntu can't login", and found many relevant results (including here in this forum) from people experiencing the same problem,
but I tried everything they've been suggested, and nothing seems to work!

Following the suggested solutions to others, this is what I tried to do, after hitting Ctrl+Alt+F2 and gaining access to the console:

[LIST=1]
[*]Setting the permissions on the home directory - even though I didn't have to, it was already rwxrwxrwx - it seems to work for some. 
[*]Reinstalling ubuntu-desktop package with *sudo apt-get install --reinstall ubuntu-desktop* 
[*]Setting the premissions on the /tmp directory to 777 
[*]*sudo apt-get install ubuntu-session* - but it says that it's already the newest version 
[*]*rm ~/.Xauthority ~/.ICEauthority* to remove these both files 
[/LIST]


Unfortunately, none of the above suggested solutions solved the problem.
Doe's anyone have more suggestions?
If not, can Ubuntu be completely reinstalled through the console?
(Modified to get numbers instead of bullets).
1: Permissions should start with rwx (full permissions for the user), other permissions don't matter too much. In fact it's better is permissions don't end in rwx (full permissions for all), but if you're the only user of your computer it doesn't matter too much.
2: **ubuntu-desktop** is a metapackage to do nothing more than pull in some standard application. Reinstalling shouldn't do anything.
3: Indeed everyone should have full permissions on /tmp, but its permissions shouldn't be 777. Instead they should be 1777, with the sticky bit set. But I don't think that causes your problem.
4: That was to be expected, but I think that theoretically reinstalling that package could sometimes help.
5: These is by far the most common cause of your problem. They may be owned by root after improper use of sudo, and it seems you used sudo a lot last time. Common beginner's error. Did it remove those files?

Check your home directory for files (including hidden files) that are not owned by you. Also check subdirectories. As a quick way to make sure all files are owned by you, use```
sudo chown -R yourusername /home/yourusername
```

---

### Post by goghvv on 2014-09-21
Hey.
I appreciate your efforts to help, unfortunately, I found out I have worst things to worry about...
My whole damn system crashed, and suddenly I couldn't get access to neither windows nor Ubuntu.
Had to recover Windows from the Lenovo designated recovery partition.
I don't know if it's related or not to the original problem, but nevertheless, I need to install a fresh copy of ubuntu.
Thanks again for the help.

---

### Post by blnl on 2014-09-22
This normally should not happen. Check your HDD for failures!

Before you reinstall Ubuntu, make a copy of your /home/(user) directory (if your system is inoperable you can allays use a live CD to boot), that is unless your /home is on a different partition. It will save you time configuring Ubuntu...

---

