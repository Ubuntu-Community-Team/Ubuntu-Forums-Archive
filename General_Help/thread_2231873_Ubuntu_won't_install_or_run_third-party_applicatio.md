---
title: "Ubuntu won't install or run third-party applications"
date: 2014-06-28
forum: General Help
---

### Post by David_Max on 2014-06-28
Hey there!I want a help to troubleshoot this problem...Obviously ;)
I downloaded a demo version of Renoise(3.0.0-tar.bz archive),extracted it and when I double-click the executable file,nothing happens,and no error messages appears(Renoise isn't installed,and already have tried to run install.sh in terminal,and also nothing happens)
And this happens with another applications that I have tried to install manually...
e.g RetroCopy,also for linux...
But,with the apps that was installed using Software Center,it installs and run normally...
My Ubuntu is 12.10 (if I'm not mistaken)...
Well,if you answer me,I'll be grateful...:)
Sorry for bad english,I'm Brazilian :D

---

### Post by deadflowr on 2014-06-28
You need to mark the executable file as executable, first.
```
chmod +x filename
```

Also, 12.10 has reached end of life
[http://fridge.ubuntu.com/2014/05/01/ubuntu-12-10-quantal-quetzal-reaches-end-of-life-on-may-16-2014/](http://fridge.ubuntu.com/2014/05/01/ubuntu-12-10-quantal-quetzal-reaches-end-of-life-on-may-16-2014/)

I would suggest backing up what files you want, and installing a supported version.

---

### Post by David_Max on 2014-06-28
the file is already marked as executable...
but ok,i'll try installing a new linux^^

---

### Post by grahammechanical on 2014-06-28
I have been reading through this

[http://tutorials.renoise.com/wiki/Linux_FAQ](http://tutorials.renoise.com/wiki/Linux_FAQ)

Ubuntu will install third party programs but we have to get the commands right. Please confirm that you ran this command from the directory that Renoise was extracted to

```
sudo sh install.sh
```

I have downloaded Renoise but I am not about to install it to prove a point because I do not want to use this program. Besides one of the system requirements is a real-time kernel and Ubuntu does not have that But Ubuntu Studio does install with a real-time kernel.

Regards.

---

### Post by David_Max on 2014-06-28
There's a problem...
through terminal I cant go to Renoise's directory...
bash: cd: /home/davidmax/renoise: No such file or directory
And i have just created a folder named renoise in that exact directory...
I went to the Renoise's folder and double-clicked in install.sh,and i clicked in run in terminal...
I tried to run the windows version of renoise using wine,but didn't worked...

---

### Post by deadflowr on 2014-06-28
Is the folder Renoise, or renoise.
Capitaiization is important.
I would run the **ls** command on the top folder (the home folder)
to make sure.
Then I'd change into the listed directory(**cd** directory-name) and then run the install.sh.
sudo ./install.sh, or sudo sh install.sh

The problem with simply clicking on it is that if any problems are happening, it won't tell you.
Where as running the cli will.

---

### Post by David_Max on 2014-07-07
Now,I installed ubuntu 14.04,I can go to Renoise's directory through terminal,and the Renoise installation was successful :p,but now,when I run it on terminal,appears:
Renoise LOG> CrashLog: [0x20]
Segmentation fault (core dumped)

What it means?

---

### Post by David_Max on 2014-07-10
Hey!Thanks Deadflowr and Gra[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")hammechanical,for helping me!Now,I installed Renoise x64,and it run normally :D.
Again,thanks you two!XD

---

