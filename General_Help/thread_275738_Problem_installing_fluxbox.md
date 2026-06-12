---
title: "Problem installing fluxbox"
date: 2006-10-11
forum: General Help
---

### Post by zoidburg016 on 2006-10-11
I was following a tutorial that I found on these forums to install fluxbox without using apt-get install fluxbox. That tutorial said to install something with the command sudo apt-get install checkinstall, I typed that in to the terminal, put in my password, it built the dependancy tree's or whatever, then it said that it couldn't find the application. so I tried to just use sudo apt-get install fluxbox and it did the same thing. does any one know why it isn't working.

---

### Post by catlett on 2006-10-11
If you only want a fluxbox/ubuntu system, nubuntu is a choice. It is a distro made up of fluxbox on ubuntu server. [http://www.nubuntu.org/about.php](http://www.nubuntu.org/about.php)
If you want to install it alongside gnome, kde etc you should be able to install it through synaptic package manager or for that matter with ```
sudo apt-get install fluxbox
```
What error did you get when you ran apt-get install fluxbox? If it said it couldn't find it, it is a repository issue. Are you online? If you are online and getting that error, it may be a source list error. Post the output of ```
sudo gedit /etc/apt/sources.list
``` (be careful when you open it, that file will be opened as root and you can delete anything on it. just copy paste it to a reply and then close it)

---

### Post by zoidburg016 on 2006-10-11
antoneln@Grays-desktop:~$ sudo su
root@Grays-desktop:/home/antoneln# gedit /etc/apt/sources.list

(gedit:9639): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
root@Grays-desktop:/home/antoneln#
that's what it said. Yes I am connected to the internet.

---

### Post by taurus on 2006-10-11
Why not do

```

gksudo gedit /etc/apt/sources.list

```

---

### Post by zoidburg016 on 2006-10-11
sory, wrong thing I think 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2006-10-11
Remove the # sign in front of lines that contain universe & multiverse.  Save it and then run

```

sudo aptitude update
sudo aptitude install fluxbox

```

---

