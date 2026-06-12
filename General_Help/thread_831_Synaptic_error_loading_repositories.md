---
title: "Synaptic error loading repositories"
date: 2004-10-15
forum: General Help
---

### Post by wondering_jew on 2004-10-15
Bare in mind that I'm almost a complete newbie to Linux in general but I after a fresh install of ubuntu I followed the directions to get access to all the packages on synaptic "the universe" and when ever i start synaptic i get the message
"Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)"

and therefor i do not have access to all the packages avaliable on synaptic , Im sure this cant be too hard fix if i had a better idea f what i was doing...
Thanks

---

### Post by ubuntu-geek on 2004-10-15
See if this helps..

sudo nano -w /etc/apt/sources.list

Remove everything in the file and then copy and paste the following and save. then run:

sudo apt-get update
> 
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041007)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

---

### Post by wondering_jew on 2004-10-16
Got it  fixed thanks alot, my next mission is dri on a s3 savage vid card...

---

