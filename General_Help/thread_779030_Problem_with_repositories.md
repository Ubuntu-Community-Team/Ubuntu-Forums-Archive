---
title: "Problem with repositories"
date: 2008-05-02
forum: General Help
---

### Post by Foxxor on 2008-05-02
I've been using ubuntu without problem for the last 3 weeks since I Installed it, but this week I think I changed something, maybe a problem with a package, actually I don't know what I did or moved.
The problem is I cant download programs with the Add/Remove Tool, I cant download any update, and when I try to change configuration in the synaptic>Repositories the changes don't save :S, I mean I choose something and close and click reload, but when I enter again to the repositories window the options I activated before disappear :(.
need help because I cant download packages with the synaptic or programs with the add/remove or any update!
thanks ;)

---

### Post by retrow on 2008-05-02
In terminal run
```
sudo apt-get update
```
If it updates the repositories successfully, there is nothing wrong with your sources.list (i.e. your repositories).

---

### Post by Foxxor on 2008-05-02
its ok, but then I dont know what's the problem, because The changes in the repositories windows dont save :S

---

### Post by karuptdata on 2008-05-02
Anytime you wish to make changes to your sources.list you must be running as root. In terminal type the following command.

```
sudo gedit /etc/apt/sources.list
```

This will launch gedit with root privilages so that you can edit it to your liking.

---

### Post by retrow on 2008-05-02
Are you updating your repositories with the "Software Sources" option in menu?

Try to manually edit the sources.list file with the new repositories that you want to add.

```
sudo gedit /etc/apt/sources.list
```
Add the new repositories at the bottom of the exiting list. Save it. And then run,
```
sudo apt-get update
```again.

Another reason why you can't download from repositories could be that the server you are connecting to is overloaded, or offline for the time being. You can wait for a few minutes or hours and try again.

---

### Post by Foxxor on 2008-05-02
Im kinda new with ubuntu, yea it opens a text document, and its empty what should I write ?


---> When I tried to modify the file, it says the file doesnt exist what should I do? X_x

---

### Post by retrow on 2008-05-02
Thats unusual. If your sources.list is empty, you can copy-paste this into that file and save it:

```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://es.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://es.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://es.archive.ubuntu.com/ubuntu/ hardy universe
deb http://es.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://es.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

##Bibus
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./

deb http://ppa.launchpad.net/bzr/ubuntu hardy main
deb-src http://ppa.launchpad.net/bzr/ubuntu hardy main
```

Then run ```
sudo apt-get update
```

Then you should be able to add-remove stuff.

P.S: This list connects to server in Spain and its usually available when most of the servers around the world are overloaded.

---

### Post by Foxxor on 2008-05-02
I tried to save it, and apparently even the folder apt doesnt exist o.o
should I create the folder and the document and move it with console?

---

### Post by retrow on 2008-05-02
Thats really strange. Even if the sources.list is missing, there usually is a /etc/apt folder.

I guess someone with a better understanding than me can help you out.

---

### Post by Foxxor on 2008-05-02
ok, I created the folder and the file, and used:

sudo apt-get update 

and it started to work correctly but after 2 minutes:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-updates Release: Couldn't access keyring: 'No such file or directory'
W: You may want to run apt-get update to correct these problems

this appeared, thanks :)

---

