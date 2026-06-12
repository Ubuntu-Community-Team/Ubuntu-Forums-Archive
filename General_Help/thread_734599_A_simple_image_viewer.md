---
title: "A simple image viewer"
date: 2008-03-24
forum: General Help
---

### Post by satimis on 2008-03-24
Hi folks,


Ubuntu 7.04 server amd 64
Flux desktop


I'm looking for a simple image viewer to read .jpg, tiff, etc. files with only magnifying feature.  Because this is a server I don't expect pulling too many dependencies.  TIA


B.R.
satimis

---

### Post by kerry_s on 2008-03-24
feh or gpicview

i use gpicview on mine.

---

### Post by satimis on 2008-03-24
> **kerry_s said:**
> feh or gpicview

i use gpicview on mine.
Thanks for your advice.


Just visited their websites.  I like gpicview.  But I can't find it on repo.  I found feh on rep.  Do you know which repo provides gpicview?  Thanks


satimis

---

### Post by kerry_s on 2008-03-24
> **satimis said:**
> Thanks for your advice.


Just visited their websites.  I like gpicview.  But I can't find it on repo.  I found feh on rep.  Do you know which repo provides gpicview?  Thanks


satimis

it should be in the repo, do you have them all on?
in synaptic> settings> repositories

---

### Post by satimis on 2008-03-24
> **kerry_s said:**
> it should be in the repo, do you have them all on?
in synaptic> settings> repositories
I'm running Flux, a simple desktop, on server.


$ apt-cache search gpicview
No printout

$ apt-cache search feh
feh - imlib2 based image viewer


satimis

---

### Post by kerry_s on 2008-03-25
yeah, so you should install synaptic, it's the best way to manage whats installed or removed. i run a custom install built from the base as well, but i use debian, it's faster, more stable. i use jwm for my wm, it's smaller and faster than any of the *box's.

anyways, the file is /etc/apt/sources.list, so->
sudo xedit /etc/apt/sources.list
or
sudo nano /etc/apt/sources.list
or if you use mc
sudo mcedit /etc/apt/sources.list

uncomment any repo that's commented out.
and make sure if you use xedit, click save 2x to save.

ps:
you should add some alias's to your ~/.bashrc so you don't have to type out the whole thing.

alias su="sudo -i"
alias install="sudo apt-get install"
alias remove="sudo apt-get remove --purge"
alias find="apt-cache search"
alias update="sudo apt-get update"
alias upgrade="sudo apt-get upgrade"

---

### Post by sujoy on 2008-03-25
also try ristretto , its extremely light wieght

---

### Post by satimis on 2008-03-25
> **kerry_s said:**
> yeah, so you should install synaptic, it's the best way to manage whats installed or removed. i run a custom install built from the base as well, but i use debian, it's faster, more stable. i use jwm for my wm, it's smaller and faster than any of the *box's.

anyways, the file is /etc/apt/sources.list, so->
sudo xedit /etc/apt/sources.list
or
sudo nano /etc/apt/sources.list
or if you use mc
sudo mcedit /etc/apt/sources.list

uncomment any repo that's commented out.
and make sure if you use xedit, click save 2x to save.

I already uncomment almost all repo on /etc/apt/source.list```

# 
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://apt.debian.org.tw/ unstable main/ttf-arphic-newsung
deb http://download.webmin.com/download/repository sarge contrib

```
I think I have to download "gpicview" on its website if I need it.


> 
ps:
you should add some alias's to your ~/.bashrc so you don't have to type out the whole thing.

alias su="sudo -i"
alias install="sudo apt-get install"
alias remove="sudo apt-get remove --purge"
alias find="apt-cache search"
alias update="sudo apt-get update"
alias upgrade="sudo apt-get upgrade"
I'll create ~/.bashrc and put all above lines on the file.

Whether I need to type 'alias install' for "sudo apt-get install' NOT only 'install'?

Thanks


B.R.
satimis

---

### Post by satimis on 2008-03-25
> **sujoy said:**
> also try ristretto , its extremely light wieght
$ apt-cache search ristretto
No printout.


It is NOT on repo


B.R.
satimis

---

### Post by Therion on 2008-03-25
Just a thought:  [gThumb](http://gthumb.sourceforge.net/screenshots.html)??  Should definitely be in the repo.

---

### Post by kerry_s on 2008-03-25
uncomment back ports.

man, i can't believe it you got all those repo's yet you still got stuff missing.

ps: i changed some of the commands i use, like "find" there is already a find in use by the system, i usually use "whereis" or "locate" so i forgot all about it. i don't use commands that much, i prefer synaptic. my new->

alias su="sudo -i"
alias get="sudo apt-get install"
alias remove="sudo apt-get remove --purge"
alias view="apt-cache search"
alias update="sudo apt-get update"
alias upgrade="sudo apt-get dist-upgrade"  <--you should stick with "upgrade" in yours, don't want to end up in hardy by mistake. 


in debian i'm only using 5 repo's. pic->

---

### Post by satimis on 2008-03-25
> **Therion said:**
> Just a thought:  [gThumb](http://gthumb.sourceforge.net/screenshots.html)??  Should definitely be in the repo.
I got it installed.  Thanks


satimis

---

