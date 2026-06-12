---
title: "Trouble with updates/synaptic package"
date: 2008-01-01
forum: General Help
---

### Post by tylerdurden15 on 2008-01-01
I tried to update to version 7.04 then to 7.10 and when i did that through the update manager i got an error message that it could not update for what ever reason.  Now since then everytime i open the update manager it starts to load and then the program just shutdown before anything can be done.  Also i am getting an error message when ever i start the synaptic package manager i get this message: E: Dynamic MMap ran out of room
E: Error occurred while processing language-pack-nb (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


i dont know whats going on but how do i fix this?  

Thanks

---

### Post by taurus on 2008-01-01
You said you tried to upgrade from Feisty to Gutsy but how come the error message has edgy in it?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by tylerdurden15 on 2008-01-01
sorry i ment edgy to fiesty then fiesty to gutsy

heres what you asked for:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
brendan@brendan-desktop:~$

---

### Post by taurus on 2008-01-01
I am not sure why you have all these edgy repos in there since you are running fiesty!

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted


You may want to replace the word **edgy** with **feisty** in /etc/apt/sources.list and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tylerdurden15 on 2008-01-01
im running 6.10 right now and was trying to upgrade to 7.10, but again i am currently running 6.10

thanks agian for any help

---

### Post by tylerdurden15 on 2008-01-01
i ran that first code and i got this message agian

Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing language-pack-nb (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by taurus on 2008-01-01
If you are running Edgy, then you need to replace feisty with edgy in /etc/apt/sources.list.  So, all the repos in /etc/apt/sources.list would be from edgy, not feisty.

```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Mixing releases in /etc/apt/sources.list is never a good thing.  It can and will break your box.

---

### Post by tylerdurden15 on 2008-01-01
well can you tell me how to get the fiesta updates off my machine please?

---

### Post by tylerdurden15 on 2008-01-01
when i type in etc/apt/sources.list it tells me permission denied

---

### Post by tylerdurden15 on 2008-01-01
can anyone help me?

---

### Post by taurus on 2008-01-01
```
gksudo gedit /etc/apt/sources.list
```

---

