---
title: "Unable to install R software packages"
date: 2006-11-10
forum: General Help
---

### Post by PsychStats on 2006-11-10
I have successfully installed R on several computers that are running Ubuntu 6.06. This past computer is a mystery to me. When I run the command:

sudo R CMD INSTALL  /home/user/Desktop/chron_2.3-9.tar.gz

I get the following error message.

* Installing *source* package 'chron' ...
** libs
/usr/lib/R/bin/SHLIB: line 122: make: command not found
ERROR: compilation failed for package 'chron'
** Removing '/usr/local/lib/R/site-library/chron'

I have searched everywhere for some help on this and I even checked the reference given. The make command is there and I found no help online.

Could be I am not looking in the right place or I just don't understand the error. Every other computer has not had a problem with installing packages.

Any help would be great.

---

### Post by dcstar on 2006-11-10
> **PsychStats said:**
> I have successfully installed R on several computers that are running Ubuntu 6.06. This past computer is a mystery to me. When I run the command:

sudo R CMD INSTALL  /home/user/Desktop/chron_2.3-9.tar.gz

I get the following error message.

* Installing *source* package 'chron' ...
** libs
/usr/lib/R/bin/SHLIB: line 122: make: command not found
ERROR: compilation failed for package 'chron'
** Removing '/usr/local/lib/R/site-library/chron'

I have searched everywhere for some help on this and I even checked the reference given. The make command is there and I found no help online.

Could be I am not looking in the right place or I just don't understand the error. Every other computer has not had a problem with installing packages.

Any help would be great.

This looks like it is compiling, are all the packages necessary for building installed on this system?

---

### Post by PsychStats on 2006-11-10
As best as I can tell, yes everything is in order. I have several programs that I already run on the system. I need this addon package to compute the time values. Everything else works just fine, until I try to install this package or any other. After doing a check using apt-get I don't see any dependencies left out.

---

### Post by taurus on 2006-11-10
Looks like it couldn't find make!!!

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by PsychStats on 2006-11-10
oh man, case closed. I miss the simplest things sometimes. 

Thank you. All is well in my land for now.

---

### Post by taurus on 2006-11-10
> **PsychStats said:**
> oh man, case closed. I miss the simplest things sometimes. 

Thank you. All is well in my land for now.
So it was build-essential!!!

---

### Post by PsychStats on 2006-11-10
Yes, it was just the build-essential that fixed my problem.

---

