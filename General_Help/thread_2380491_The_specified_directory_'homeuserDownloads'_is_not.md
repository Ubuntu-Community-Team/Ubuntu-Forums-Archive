---
title: "The specified directory '/home/user/Downloads' is not valid-please help"
date: 2017-12-18
forum: General Help
---

### Post by hoboy on 2017-12-18
Hi
I was installing Hadoop on ubuntu 17.10
that required that one should create another user, I did that.
I am not sure if that is causing my problem.
But 
I can view the contain of the following folders
The specified directory '/home/user/Documents' is not valid
The specified directory '/home/user/Music' is not valid
The specified directory '/home/user/Pictures' is not valid
The specified directory '/home/user/Downloads' is not valid
The specified directory '/home/user/Videos' is not valid
Thanks

---

### Post by howefield on 2017-12-18
Might help to post the full input and output of the terminal.

Are you following a tutorial ?

PS. Thread moved to the "*General Help*" forum.

---

### Post by hoboy on 2017-12-18
Hi 
I just i open the folders  with file manager when I click on the folders mentioned I get the errors
tks

Hi

when I use the console the output

 cd /home/user/Downloads
-su: cd: /home/user/Downloads: No such file or directory
Tks

I have just tried 

user@user-Lenovo-Z50-75:~$ ls -l
total 0

---

### Post by dragonfly41 on 2017-12-18
What is output from
```
whoami
```

---

### Post by hoboy on 2017-12-18
$ whoami
user

---

### Post by howefield on 2017-12-18
Seems that you have created a new user without a ~/ folder, how did you create it ?

---

### Post by hoboy on 2017-12-18
here is what I have used:
-----------------------------------------
---> add hduser to sudo
sudo adduser hduser sudo
sudo su hduser


------------------------------------------
Download hadoop

wget [http://mirrors.dotsrc.org/apache/hadoop/common/hadoop-3.0.0/hadoop-3.0.0.tar.gz](http://mirrors.dotsrc.org/apache/hadoop/common/hadoop-3.0.0/hadoop-3.0.0.tar.gz)


tar xvzf hadoop-3.0.0.tar.gz
--------------------------------------

Move hadoop installation to local file system /usr/local

sudo mv * /usr/local/hadoop
 sudo chown -R hduser:hadoop /usr/local/hadoop

---

### Post by steeldriver on 2017-12-18
AFAIK the ~/Downloads, ~/Documents etc directories are created the first  time a user logs in *graphically *(by invoking `xdg-user-dirs-update`)

OTOH if they *were *created, then running

```

sudo mv * /usr/local/hadoop

```

from the user's home directory would have moved them to /usr/local/hadoop

---

### Post by hoboy on 2017-12-18
how to I move them back ?

you are right they are there

Yes you are right there there how can I move them back in there respective places ?

Thanks very much 
I have restored everything except the Desktop when I click on Desktop I get the following .The specified directory '/home/user/ck' is not valid

---

### Post by steeldriver on 2017-12-18
Please check the xdg-user-dir setting for your desktop by running the following command

```

xdg-user-dir DESKTOP

```

(note the capitalization of DESKTOP)

---

### Post by hoboy on 2017-12-18
Tks 
/home/user/

How can I use /home/user/  this to solve the Desktop error
when I click on the Desktop I get the following error

The specified directory '/home/luc/ck' is not valid

---

### Post by hoboy on 2017-12-18
Please somebody help

---

### Post by QIII on 2017-12-18
Please be patient.  If you have received no response in 12 hours, you may bump your thread.  

Also please remember that everyone here is a volunteer.  We have our own lives, jobs, families, hobbies, activities, the need to sleep and eat, etc.  There may simply be nobody with the requisite knowledge of your issue on line at any given time.

Thanks.

---

### Post by ajgreeny on 2017-12-18
What is the output of command ```
ls -lR /home/ | grep Downloads
```which will show the pathway of all files in the Download directories of all users.

---

### Post by hoboy on 2017-12-19
ls -lR /home/ | grep Downloads
drwxrwxrwx 18 user  user     16384 Dec 18 10:51 Downloads

---

### Post by ajgreeny on 2017-12-19
The Downloads folder is sitting in /home itself as **/home/Downloads** and not as it should be as **/home/user/Downloads** so the question has to go back to you, how could that have happened? You do not have any user folders at all in **/home** so this is rather baffling as I did not think you could install without at least one user being created by default in the installation process.

Do you believe you have created a user actually named **user**?  That command output does not show that as it should if such a username exists.

When you boot the system as whom do you login to get to the GUI; do you actually have and use a GUI, or is this a command-line system only such as a server?

EDIT:
I see you have marked this as SOLVED.
If this is so, please let us know what you did and how it was solved.

---

### Post by hoboy on 2017-12-20
Hi I 
sudo gedit /etc/xdg/user-dirs.defaults
then set 
DESKTOP=/home/user/Desktop
I have to confirmed that I have changed the real user to user, so "user" is not correct one 
Tks

---

