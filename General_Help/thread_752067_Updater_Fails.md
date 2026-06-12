---
title: "Updater Fails"
date: 2008-04-11
forum: General Help
---

### Post by gavinjb on 2008-04-11
Hi,

I am having problems with Ubuntu Updater, when I try to install the updates I am informed that not all updates can be installed and I am given the option to perform a partial update, if I opt to go for this, I get the following error:

```

Error authenticating some packages

```

I have had a look at some of the packages that have updates and they seem to come from the following repository

```

http://ubuntu.org.ua/getdeb/

```

Only problem is I dont have an authentication key for this repository, does anyone know if I require one.

I have also posted my sources.list incase anyone can see a problem

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu gutsy universe
# deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://ppa.launchpad.net/dell-team/ubuntu gutsy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu gutsy main
deb http://www.virtualbox.org/debian gutsy non-free
deb http://dl.google.com/linux/deb/ stable non-free
deb http://eric.lavar.de/comp/linux/debian/ unstable/
deb http://dl.google.com/linux/deb/ testing non-free
deb http://ubuntu.org.ua/ getdeb/

```

Thanks,


Gavin,

---

### Post by kesman on 2008-04-11
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) unstable/
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

These are for debian right? I don't suggest you to use Debian mirrors for ubuntu packages, since there may occur dependency problems.

---

### Post by gavinjb on 2008-04-11
They shouldn't be a problem as they are for ubuntu and debian (or thats what it the webpages tell me)

---

### Post by PmDematagoda on 2008-04-11
> **gavinjb said:**
> They shouldn't be a problem as they are for ubuntu and debian (or thats what it the webpages tell me)

Regardless of their compatibility they can be causing the error you are seeing right now concerning the unathenticated packages.

But anyway, according to the error message, the real culprit is:-
```
deb http://ubuntu.org.ua/ getdeb/
```

You can continue using this repo but keep in mind that you cannot be sure of the packages you install through this repo and it may contain some harmful software. If you want to get rid of the error message then all you need to do is to remove the repository in question.

---

### Post by gali98 on 2008-04-11
Okay I like getdeb, but I would not put it in as a repo.
They make good packages, but the are usually fresh from the slaughter and you don't want updates coming in from there. Basically, if you want one of their packages, go online and download it.
Kory

---

