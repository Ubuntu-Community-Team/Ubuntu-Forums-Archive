---
title: "[SOLVED] how do i fix this (login)"
date: 2008-06-30
forum: General Help
---

### Post by dellboy on 2008-06-30
for some reson when i login to ubuntu on the login screen where you put your username and password its comes up with a boxe saying:
user $home.dnrc files is bening ignored the session and language will  be stop form being saved 

this file should be owned and be set to 666 


well it says somthing like this dose anyone know to fix that as it would be nice to not have this box not  show it all seems to work but then i can not be sure. thank you this happen some how 

thank you for your help

---

### Post by Claus7 on 2008-06-30
Hello,

if you act like it sais then look carefully about the file and its location and go there and change its ownership like that : 

chmod 666 "name of the file", without the " "

Regards!

---

### Post by dellboy on 2008-06-30
that is the thing i can not find this file i have also check for hidden files and login as root :(

---

### Post by Claus7 on 2008-06-30
Hello,

in order to find where that file is, type :

```
cd /
find -name "name of the file" , with the  " "
```

Regards!

---

### Post by dellboy on 2008-06-30
```
sudo cd /
find -name "dnrc"
```

bring up other files but not the one i am looking for eg the one it says it cant find when i try to login

---

### Post by Claus7 on 2008-07-01
Hello,

I cannot find such a file in my system. Not even a similar one with the string of characters you provide. Are you sure that the string you provide is the one you get in the message? Because even if one character is wrong then there is no way to find the file you are looking for. It would be better to post the entire message either here in the forums or google it out. 

So I decided to google it out myself and this is where I stepped upon :
[http://ubuntuforums.org/showthread.php?t=479950](http://ubuntuforums.org/showthread.php?t=479950)
[http://ubuntuforums.org/showthread.php?t=503335](http://ubuntuforums.org/showthread.php?t=503335)
[http://ubuntuforums.org/showthread.php?t=845186](http://ubuntuforums.org/showthread.php?t=845186)

A quick glance tells me that the file might be .dmrc and not .dnrc.
Searching that file and seeing its contents :
[Desktop]
Session=default

and with ls -al
-rw-------  1 username username   26 2008-06-30 12:43 .dmrc

this is what I get.

Judging quickly from the other posts the first thing I would do would be to check that file's permissions and change them accordingly. After that as root I would try to change my home directory permissions. Also check these posts yourself. Hope this helped.

Regards!

---

### Post by drs305 on 2008-07-01
Are you sure the message isn't about .dmrc and 644 permissions? If so, run these commands. If you can't sudo, you will have to boot from grub to the recovery mode to a command line to run them:

This will change permissions and then reboot. Substitute your username:
```

sudo chmod 644 /home/*username*/.dmrc
sudo chown *username*: /home/*username*/.dmrc
sudo chmod 755 /home/*username*
sudo chown *username*: /home/*username*
sudo shutdown -r now

```

---

### Post by dellboy on 2008-07-02
yes it comes up saying dmrc its not set to 664

>  
when i try to run
sudo chmod 644 /home/username/.dmrc
i get this 
No such file or directory

anyone else have any ideas

---

### Post by plucky on 2008-07-02
> **dellboy said:**
> yes it comes up saying dmrc its not set to 664

anyone else have any ideas

**username** has to be the username you log in with unless you actually log in with username.
So the command becomes **chmod 644 /home/Name-you-login-with/.dmrc**

Good Luck

---

### Post by dellboy on 2008-07-02
how silly of me not to put my username that i am login in with lol 

ok for anyone that is reading this as they have the same problem.

run them all at once 

but not this one

shutdown -r now
when you have done all the other comands run this one after with 
gksudo shutdown -r now

then when you boot up again it will all work great again 

also thank you everyone how help me fix this you :guitar:
> **plucky said:**
> **username** has to be the username you log in with unless you actually log in with username.
So the command becomes **chmod 644 /home/Name-you-login-with/.dmrc**

Good Luck

---

