---
title: "Help ubuntu update"
date: 2017-05-25
forum: General Help
---

### Post by kiloeras on 2017-05-25
HELLO
i was trying to install mongodb and doing what was recommended on a webpage I broke my ubuntu terminal


```

# deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted
 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
 
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main

```


I get this error when put aptitude -f

[IMG]http://i.imgur.com/8b9uCn1.png[/IMG]

Can you help me please?
thanks you

---

### Post by QIII on 2017-05-25
Hello and welcome to the forums.

Please use code tags to enclose commands and their results.  They preserve terminal formatting and make your posts easier to read.

To use code tags, you may:

1.  Click the # symbol above the text entry box, move your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by kiloeras on 2017-05-25
Ok, thanks for the advice

---

### Post by deadflowr on 2017-05-25
The error(s) is coming from a different source file.
look at the file /etc/apt/sources.list.d/mongodb.list.
post what that file says.

---

### Post by kiloeras on 2017-05-25
Hi i've done cat to the file.
I created that file to try to install mongo
should i remove it?

I was trying the things that was posted in links like this:
[http://www.mongodbspain.com/es/2014/08/30/install-mongodb-on-ubuntu-14-04/](http://www.mongodbspain.com/es/2014/08/30/install-mongodb-on-ubuntu-14-04/)
[https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)
[https://www.digitalocean.com/community/tutorials/como-instalar-mongodb-en-ubuntu-16-04-es](https://www.digitalocean.com/community/tutorials/como-instalar-mongodb-en-ubuntu-16-04-es)
[IMG]http://i.imgur.com/HQ9eoav.png[/IMG]

---

### Post by deadflowr on 2017-05-25
Seems you followed this guide in particular:
[http://www.mongodbspain.com/es/2014/08/30/install-mongodb-on-ubuntu-14-04/]("http://www.mongodbspain.com/es/2014/08/30/install-mongodb-on-ubuntu-14-04/")
Erase the entry and re-run the command to add it again:
```
echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
```
See those spaces are important to have between the words upstart dist and 10gen
and not just making it one long continuous line.
After you do that run
```
sudo apt update
sudo apt upgrade
```
Then try installing mongodb.

good luck

---

### Post by kiloeras on 2017-05-27
Hey.
Hi erased the entry and then did
sudo fuser -vki  /var/lib/apt/lists/lock and the terminal worked again
Also I was able to install mongodb and do my homework
thank you

---

### Post by deadflowr on 2017-05-27
Cool
Feel free to mark this thread as solved, so others may find it and hopefully help them fix similar issues:
[How to mark a thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

