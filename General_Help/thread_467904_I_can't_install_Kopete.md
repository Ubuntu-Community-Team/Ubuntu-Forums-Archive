---
title: "I can't install Kopete"
date: 2007-06-08
forum: General Help
---

### Post by miLl3niUm on 2007-06-08
I get this error:
[img]http://www.uploadyour.info/uploads/images/synaptic74997.png[/img]

---

### Post by carolinason on 2007-06-08
This happens when apt has the cdrom as a repository.

If you prefer to download the software, then you'll need to comment this out in the /etc/apt/sources.list file.

If you need to install form the cdrom then you'll put the cdrom in the drive and_it_should install from the drive.

---

### Post by miLl3niUm on 2007-06-08
> **carolinason said:**
> This happens when apt has the cdrom as a repository.

If you prefer to download the software, then you'll need to comment this out in the /etc/apt/sources.list file.

If you need to install form the cdrom then you'll put the cdrom in the drive and_it_should install from the drive.

I inserted text installation and LiveCD CDs in my both drives but doesn't work.

---

### Post by carolinason on 2007-06-08
Doesn't work? 
The cd-rom doesn't work or installing the software doesn't work.

You can try in a command line

$> sudo apt-get install kopete

follow the prompts.

---

### Post by miLl3niUm on 2007-06-10
> **carolinason said:**
> Doesn't work? 
The cd-rom doesn't work or installing the software doesn't work.

You can try in a command line

$> sudo apt-get install kopete

follow the prompts.

When I go from Add/Remove in Ubuntu menu, I tick Kopete. Then click OK, it asks me for password. I type it, it starts downloading some files and then I get that error.

When I go from terminal:
```
alter@millenium:~$ sudo apt-get install kopete
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdelibs4c2a libarts1c2a libavahi-qt3-1 libjasper-runtime liblua50
  liblualib50 libmeanwhile1 libopenexr2c2a libpcre3
Suggested packages:
  fam kdeartwork-emoticons khelpcenter imagemagick ekiga
Recommended packages:
  perl-suid qca-tls libarts1-akode
The following NEW packages will be installed:
  kdelibs4c2a kopete libarts1c2a libavahi-qt3-1 libjasper-runtime liblua50
  liblualib50 libmeanwhile1 libopenexr2c2a libpcre3
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.3MB/18.9MB of archives.
After unpacking 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com feisty/main kdelibs4c2a 4:3.5.6-0ubuntu14 [9972kB]
Media change: please insert the disc labeled                                   
 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter
(So I get the same error)
```

---

### Post by enchesss on 2007-06-10
have you enabled repositories?

what happens after you put the cd in (after apt get tells you to)?

---

### Post by miLl3niUm on 2007-06-12
I press OK but the error/window pops up again (it's like it doesn't recognize the cd)
Anyway, never mind, I use Gaim and aMSN now but thanks for your help :P

---

### Post by dfreer on 2007-06-16
type:
```
sudo gedit /etc/apt/sources.list
```
put a # sign in front of any line that refers to the cdrom (comment it out) Should only by 1-2 of them.
then:
```
sudo apt-get update
sudo apt-get install *yourprogramhere*
```

---

### Post by miLl3niUm on 2007-06-16
Thanks a lot dfreer

---

### Post by dfreer on 2007-06-16
I'm guessing that means this worked? phew... now for your other problems... whew

---

### Post by miLl3niUm on 2007-06-17
Yes, problem solved. There was only 1 line which referred to the cdrom

---

