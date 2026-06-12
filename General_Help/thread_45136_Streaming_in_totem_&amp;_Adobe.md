---
title: "Streaming in totem &amp; Adobe"
date: 2005-06-28
forum: General Help
---

### Post by greenwom on 2005-06-28
I've searched and searched ---- I'm lost.


I followed the instructions to stream in mozilla w/ totem in this [thread](http://www.ubuntuforums.org/showthread.php?t=17727) 

it removed acroread plugin for firefox (like some others had problems with)
I followed the instructions to fix it but got no where.

When I try
sudo apt-get install acroread I get

[COLOR=Red]mike1@mikesubuntu:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages[/COLOR]

Can anyone clue me in -- If I need to post any other info I'll be on this thread like white on rice

Thanks in advance

---

### Post by arnieboy on 2005-06-28
please paste the contents of ur /etc/apt/sources.list file

---

### Post by greenwom on 2005-06-29
[QUOTE=arnieboy]please paste the contents of ur /etc/apt/sources.list file[/QUOTE]

I'll paste it when I get back to the house today, thanks for interest. (I'm at work right now)

---

### Post by greenwom on 2005-06-29
Here's my sources.list

[COLOR=Red]deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/COLOR]

---

### Post by gil-galad on 2005-06-29
Delete all the ftp.nerim.net repositories.  Those are for debian and do not work well with ubuntu, I wish the guide had not recomended to use them.  Backports should have the packages you need.

---

### Post by arnieboy on 2005-06-29
Copy the following 2 lines at the end of the sources file and save it.
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

Also as galad pointed out, please delete/comment out all ur "nerim" repositories.
 
Now run sudo apt-get update
and try to install acroread

---

### Post by greenwom on 2005-06-29
I killed the lines as instructed and it worked.... sweeeet.

I also added those two lines to the source.list after the fact.


Thanks you'll rock

---

