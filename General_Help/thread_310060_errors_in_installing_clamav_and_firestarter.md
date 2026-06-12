---
title: "errors in installing clamav and firestarter"
date: 2006-11-30
forum: General Help
---

### Post by johnmxg12 on 2006-11-30
hey guys, i tried to follow these commands in the terminal: 

```
sudo apt-get install clamav
```

package clamav is not available

i also tried 

```
sudo apt-get install firestarter
```

couldn't find package firestarter 

are there any other ways i can install these programs?

---

### Post by milton1 on 2006-11-30
you may not have the right sources available. Try this:

sudo pico /etc/apt/sources.list

uncomment all the universe and multiverse deps

---

### Post by johnmxg12 on 2006-11-30
i hate to be a noob at this but......how do i go about uncomment all the universe and multiverse steps.

i entered that code and GNU nano came up but i'm a little lost.  i'm sorry for asking questions like this  :-k .  i appreciate your help

---

### Post by milton1 on 2006-11-30
remove the # characters in front of each address. when you are finished, save the file (alt-x) and run

sudo apt-get update

you should now have access to many more packages. No need to apologize for being a noob. We all started that way. :)

---

### Post by johnmxg12 on 2006-11-30
ok done, but still won't install.  cant find packages

---

### Post by milton1 on 2006-11-30
can you post your sources.list?

---

### Post by johnmxg12 on 2006-11-30
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restric$
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
                               [ Read 35 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell



thats weird i thought i had deleted those # before and saved it.

---

### Post by milton1 on 2006-11-30
try again, hopefully it will work this time. Also, clamav has several dependancies; it might be easier for you to get it with synaptic than with apt-get. synaptic (or adept, I don't know which one ubuntu is using now) will automatically select the dependancies.

---

### Post by johnmxg12 on 2006-11-30
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restric$
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

 Major bug fix updates produced after the final release of the
 distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

 Uncomment the following two lines to add software from the 'universe'
 repository.
 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 universe WILL NOT receive any review or updates from the Ubuntu security
 team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
 Uncomment the following two lines to add software from the 'backports'
 repository.
N.B. software from this repository may not have been tested as
 extensively as that contained in the main release, although it includes
 newer versions of some applications which may provide useful features.
 Also, please note that software in backports WILL NOT receive any review
 or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer$
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted un$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe



so i got rid of the #'s and i saved using alt-x.  clamav and firestarter aren't working, not available

---

### Post by milton1 on 2006-11-30
did you "sudo apt-get update"?

also, leave the # characters around the instruction text. Only the "deb http://..." lines should be uncommented.

---

### Post by johnmxg12 on 2006-11-30
yep, i went back and removed the # before the deb, and i did an update.  I tried to install clamav and this came up :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clamav is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package clamav has no installation candidate

and i also tried this with another application and it came up the same. perhaps i need to change something in sessions?

---

### Post by johnmxg12 on 2006-11-30
could this be a problem with package manager? because all the packages i try installing dont work at all.  is there something i need to get out of the xbuntu cd? or do i need to change other settings?

---

### Post by johnmxg12 on 2006-11-30
great, i found it, thanks for the help. have a nice day -john

---

