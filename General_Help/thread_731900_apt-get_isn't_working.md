---
title: "apt-get isn't working"
date: 2008-03-22
forum: General Help
---

### Post by skydiver|goose on 2008-03-22
not sure what to say aside from that my sudo apt-get install isn't working..

screenshot attached:

---

### Post by TheLions on 2008-03-22
try ```
sudo apt-get update
```

---

### Post by Tomatz on 2008-03-22
Try:

sudo apt-get update

---

### Post by skydiver|goose on 2008-03-22
same error

screenshot again:

---

### Post by forestpixie on 2008-03-22
I wouldn't I'd edit it - you've an error on line . If you don't know what to do post it here

```
cat /etc/apt/sources.list
```

---

### Post by ibuclaw on 2008-03-22
I think that your sources list may of overloaded with packages...?
Not sure on the concept of it, but I remember the same thing happening when I once had both Debian Etch and Sid "Main, Contrib & Non-Free" repositories in my sources list.
As soon as I removed Sid from my sources list, everything seemed to go well.
So maybe temporary disabling some package sources may help for the moment.

[EDIT]
OR perhaps its what he said (above)

---

### Post by skydiver|goose on 2008-03-22
forestpixie, I have no idea how to edit it. Here's the copy/paste of what I get when I run your code:

goose@goose-laptop:~$ sudo apt-get install gparted
E: Malformed line 48 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
goose@goose-laptop:~$ sudo apt-get update
E: Malformed line 48 in source list /etc/apt/sources.list (URI parse)
goose@goose-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free


[edit]
tinivole

I have no idea what you just said

I barely understand linux ;]

---

### Post by forestpixie on 2008-03-22
there is an error in line 48 of the sources list :)

---

### Post by forestpixie on 2008-03-22
do these in a terminal - you will need you're password

```
sudo nano /etc/apt/sources.list
```

 go to the bottom line and delete one of the 'deb' where it says deb deb-src
then to save and escape 

ctrl+O , enter, ctrl +X

then ```
sudo apt-get update && sudo apt-get install gparted
```

---

### Post by forestpixie on 2008-03-22
A bit of explanation -> I have no idea what you just said
the sources list in /etc/apt is where the system gets the information it needs to know where to get and install software.

cat  /etc/apt/sources.list as you saw listed what was in the file 
apt-get update  updates the list to the newest one

---

### Post by ibuclaw on 2008-03-22
> **skydiver|goose said:**
> 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free


I can't see anything wrong with that general area. All locations and actions to call them seem legit.

Oops, didn't look down far enough 8)

"deb deb-src" yep thats it.

---

### Post by skydiver|goose on 2008-03-22
thanks! worked like a charm

---

