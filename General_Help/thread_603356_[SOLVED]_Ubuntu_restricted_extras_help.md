---
title: "[SOLVED] Ubuntu restricted extras help"
date: 2007-11-05
forum: General Help
---

### Post by the lemming on 2007-11-05
Hello

I just installed ubuntu 7.10 last night and I'm having trouble playing my MP3s.  I was able to play them with the live disc after following the instructions however I can not do this with the installed OS.

When I try to play a MP3 I am told to install GStreame extra plugins.  The pop-up screen says that I need to refresh my list, which I do and then tells me that I need an internet connection to re-load.  And from there I am in a never ending loop.

I then tried the Wiki on Ubuntu restricted extras and got the following message

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working Internet connection. 

When I press refresh I get  the same list and when I try again to select the extras I get the exact same message.

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working Internet connection. 

Am I doing something wrong?

Cheers

---

### Post by Soarer on 2007-11-05
Do you have a working Internet connection?

If so, it is likely you cannot get to the mirrors for some reason. In System>>administration>>Software Sources try changing to another server, perhaps the UK or US one as both seem fast to me here in the UK. On the same (first) page, make sure all the sources have a tick in them. Reload then try Synaptic again.

---

### Post by shad0w_walker on 2007-11-05
You need a working internet connection to get the list. Check to make sure its working and if it is, try changing your servers as mentioned in the last post. If it isn't thats your problem right there.

---

### Post by the lemming on 2007-11-05
> **Soarer said:**
> Do you have a working Internet connection?

If so, it is likely you cannot get to the mirrors for some reason. In System>>administration>>Software Sources try changing to another server, perhaps the UK or US one as both seem fast to me here in the UK. On the same (first) page, make sure all the sources have a tick in them. Reload then try Synaptic again.

Hello I have tried to change the server to the UK but every time I highlight the UK and then close the screen everything reverts to the Main Server.

How can I make my change to the UK server perminant?

cheers

---

### Post by Soarer on 2007-11-05
That sounds wrong to me. When I change (which I have just done) it will offer to reload all the repositories. It does this and then closes.

AFAIK you haven't answered question number 1 - do you have a working Internet connection?

---

### Post by the lemming on 2007-11-05
> **Soarer said:**
> That sounds wrong to me. When I change (which I have just done) it will offer to reload all the repositories. It does this and then closes.

AFAIK you haven't answered question number 1 - do you have a working Internet connection?


Yes, I have a working internet connection.

Cheers

---

### Post by Maestro23 on 2007-11-05
> **the lemming said:**
> Yes, I have a working internet connection.

Cheers

Post your /etc/apt/sources.list

> cat /etc/apt/sources.list

Copy/Paste the file here.

---

### Post by the lemming on 2007-11-05
> **Maestro23 said:**
> Post your /etc/apt/sources.list



Copy/Paste the file here.

I haven't played with a Linux OS for months so please excuse me if this is wrong so here goes








frank@frank-laptop:~$ cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
frank@frank-laptop:~$ 


Hope this helps

---

### Post by Maestro23 on 2007-11-05
All your sources are commented out(#).  That's why you're not able to update/install anything.
Need to uncomment them and then:

> sudo apt-get update && sudo apt-get upgrade

Here's mine for a reference:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by the lemming on 2007-11-05
> **Maestro23 said:**
> All your sources are commented out(#).  That's why you're not able to update/install anything.
Need to uncomment them and then:





Please excuse my ignorence but unfortunately I do not understand what you have asked me to do, sorry,

---

### Post by LowSky on 2007-11-05
in terminal type
```
 sudo gedit /etc/apt/sources.list

```

the take out the # marks on the files sugeested above

---

### Post by Maestro23 on 2007-11-05
> **the lemming said:**
> Please excuse my ignorence but unfortunately I do not understand what you have asked me to do, sorry,

You need to edit the **/etc/apt/sources.list** with an editor such as gedit.  You need to uncomment your sources (take out the #'s) in the appropriate lines.  Make your changes, save the file and run the commands I provided.  To edit the file:

> gksudo gedit /etc/apt/sources.list

You can use my list as an example.

---

### Post by NilsE on 2007-11-05
Go into System>Administration>Software Sources and put a check mark next to all repositories but not the CD option. 

Or

Edit the sources.lst with this command

sudo gedit /etc/apt/sources.list

and remove the # from in front of every line that starts with deb

---

### Post by the lemming on 2007-11-05
> **NilsE said:**
> Go into System>Administration>Software Sources and put a check mark next to all repositories but not the CD option. 




Thanks for the advice to tick all the boxes, that worked a treat.

Thanks everybody for your help and advice.

Cheers

---

### Post by Maestro23 on 2007-11-05
> **the lemming said:**
> Thanks for the advice to tick all the boxes, that worked a treat.

Thanks everybody for your help and advice.

Cheers

Good deal.  Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

