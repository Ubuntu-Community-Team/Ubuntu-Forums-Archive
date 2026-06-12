---
title: "Major Failure regarding sources.list"
date: 2007-02-04
forum: General Help
---

### Post by Gibbs on 2007-02-04
Hey,

I'm new to Ubuntu and Linux so my knowledge isn't great. Anyway. I tried entering a command via the Terminal to get some drivers for my graphics card when I ran into this error: ```
E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

Line 36 is this (I think) ```
deb http://archive.ubuntu.com/ubuntu/ edgy multiverse
```

I have been using Add/Remove but I can not longer use it. It brings up this error:> Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

The permissions are set to "root" on the file. I know the root password but I have no idea what to do.

Please help and replies are very much appreciated.

Thanks!

---

### Post by joeilynn on 2007-02-04
Message deleted.

---

### Post by Gibbs on 2007-02-04
Ah deleted...

---

### Post by taurus on 2007-02-04
> **Gibbs said:**
> Ah deleted...

It (Post #2) was basically a spam so I deleted it!

---

### Post by taurus on 2007-02-04
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
``` 
and change line 36 from this

```
deb http://archive.ubuntu.com/ubuntu/ edgy multiverse
```
to this.

```
deb http://archive.ubuntu.com/ubuntu edgy multiverse
```
Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Gibbs on 2007-02-04
Thanks for the help. It will probably work but I have one problem. This is printed when trying to execute it in the Terminal (even under root):
> (gedit:4691): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I have manually located the file but it's set to read only. As I can't access it in the terminal with root i'm confused...

---

### Post by Sef on 2007-02-04
It always says that.  Nothing to worry about.   Not sure why it does.   Never had a problem because of it.

---

### Post by taurus on 2007-02-04
But did gedit came up at all?  Otherwise, use the old fashion text editor then.

```
sudo nano -w /etc/apt/sources.list
```
Hold down <Ctrl> and press x to exit.  Answer the question with Y and Enter.

---

### Post by Gibbs on 2007-02-04
I used the "old fasion" text editor (:P) and edited line 36. It now displays this:

> E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I'm going to paste the entire sources.list file just to be on the safe side:
> 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe


---

### Post by taurus on 2007-02-04
This line is the problem, third from last. 

```
deb http://archive.ubuntu.com/ubuntu/ edgy
```
Therefore, put a # sign in front of it to comment it out and also the one after it too, second to last.

---

### Post by Gibbs on 2007-02-04
Cheers!

Worked a treat. Thanks a lot! :)

---

