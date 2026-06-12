---
title: "Looking for ins and outs of Synaptic"
date: 2005-03-19
forum: General Help
---

### Post by kkathman on 2005-03-19
Im struggling with how the Synaptic Package manager works, as I've been trying to install Kubuntu or KDE, and I cant seem to get the right combination of things for it to show up on the packages list.

Im not necessarily looking for how to download KDE just how Synaptic works, how to set it up to get packages from ubuntu and Debian, etc.  There is a file manager I'd like to try allegedly on debian, but again Im not educated enough yet on how to set up Synaptic to do this.

I searched the Ubuntu Documentation for "Synaptic" and came back with no hits.

Thanks for your help in advance.

Kork

---

### Post by Buffalo Soldier on 2005-03-19
[Introduction to Apt-get](http://www.newsforge.com/article.pl?sid=04/12/02/1710208) - the main method of installing, updating and uninstalling in Ubuntu. (Synaptic is a front-end of Apt)

One from many list of informative website that I have compiled at [HowTo: For People New to Ubuntu](http://ubuntuforums.org/showthread.php?t=13042)

---

### Post by kkathman on 2005-03-19
Thanks very much for your link. It was definitely worth reading! It answered several questions, especially about the various terminlogy I've been hearing about such as woody, sid, sarge, stable, unstable and testing.

Now, I wonder if you or someone could bring this all together with regard to Ubuntu. It looks as if there are two major archives for ubuntu...warty and hoary.  Within these there are sources main, restricted and universe.

Now this is what is confusing me. As I go into the Synaptic Package manager, there are types (I assume these are all debian since they all seem to be labeled as "deb" or deb-src). They all point to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu).  In the lower portion of the screen, it mentions URI (which is the above), Distribution (I assume to be warty or hoary) and sections (which I assume to be main, restricted and universe).

Now all that being said, could you please explain these? For instance, I'm still looking to get KDE or Kubuntu installed, but have yet to see it in any repository, so I must not be getting the right combinations.  When do I want to use these various combinations?

Thanks again for your help on this, and my thanks to those who will constructively respond !

Regards,
Kork

---

### Post by Buffalo Soldier on 2005-03-20
You're more than welcome sir and glad that it was what you were looking for.

Here's a link that describes main, universe and restricted -> [http://www.ubuntulinux.org/ubuntu/components/](http://www.ubuntulinux.org/ubuntu/components/)

About getting Kubuntu I haven't tried it myself and not very sure. Wouldn't want to point you in the wrong direction. But someone with better answer will usually show up and point you the right way.

---

### Post by kkathman on 2005-03-20
Again, Buffalo, outstanding! Exactly what the doctor ordered. With this I was able to get an excellent understanding of the distributions!

I was finally able to see all the K-Desktop components, and there are so many! I will do a bit more snooping around to find out what I need exactly. The computer I am working with right now is a bit old and limited. It can only go to 256 MB memory, and currently it has only 96. Now, it runs fine, and stable, but it is a little slow in bringing up things. With that said, I am wondering if KDE or Kubuntu (not sure of the difference here), would be more resource intensive than the Gnome I have now. If so, then I wont worry. 

Thanks again very much!  I appreciate all the help I have received and Ubuntu has alot to be proud of!

Regards,
Kork

---

### Post by kkathman on 2005-03-20
One other thing I just noticed.

In my /etc/apt/sources.list file, it looks as if I am set to get updates from hoary and not warty, but I thought I installed warty. Here the content:

> 
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted  
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main-restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 


Is there something wrong here?

Thanks,
Kork

---

### Post by Buffalo Soldier on 2005-03-20
Before doing anything I would suggest you back-up the original file. Type at the console:```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```And then to edit your file type:```
sudo gedit /etc/apt/sources.list
```Replace with this new list```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

# deb http://archive.ubuntu.com/ubuntu/ warty multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

# deb ftp://ftp.nerim.net/debian-marillat/ stable main
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main
# deb ftp://ftp.nerim.net/debian-marillat/ testing main

# deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe

```When and if you're ready and interested to run or install application from the Multiverse, Marillat, and Warty-Backports repositories... just uncomment (delete the # sign) the respective lines.

---

### Post by kkathman on 2005-03-20
AHA so it was as I suspected!  I surmise that when I played around with the Synaptic Package Manager and did updates, it changes that file. Thanks very much for the great response!.

I'm off to read more about apt-get, and also how I can change these annoying HUGE icons in Gnome to something that is more tasteful :)

Regards,
Kork

---

### Post by kkathman on 2005-03-21
Buffalo,

I did edit that sources.list file as you indicated. you have a couple of lines that are causing errors now when I open Synaptic;

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe


For some reason, when I open Synaptic, the following error message appears:

> 
Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)


When I go into the /etc/apt/sources.list file and comment those two lines out, the errors go away. I went to that directory, and sure enough that file (and Im assuming the other corresponding file) doesnt exist.

Question:  What are those files and how would I assure those get on my system?

Thanks,
Kork

---

### Post by Buffalo Soldier on 2005-03-21
Haven't had that problem before, so I'm just guessing here. Go to the console and try```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```I think that should clean out any errors cause by previous cache and give you all the latest updates.

---

### Post by kkathman on 2005-03-21
I did the apt-get clean and the apt-get update. 

That being said, if I do the apt-get upgrade and the apt-get dist-upgrade, as I understand from readings, wont this cause some dependency problems?

Here is the result of running the apt-get update:

> 
kkathman@ubuntu:~ $ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [102B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources [174kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [108B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [110B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release [81B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources [1024B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release [87B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages [2580kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release [83B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources [1053kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release [85B]
Fetched 3808kB in 28s (133kB/s)
Reading Package Lists... Done


And now here is the content of the /etc/apt/sources.list:

> 
## Uncomment the following two lines to fetch updated software from the network
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

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

# deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe


Finally here is the contents of /var/lib/apt/lists:

[quote]
kkathman@ubuntu:/var/lib/apt/lists $ ls
archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Release
archive.ubuntu.com_ubuntu_dists_warty_main_source_Release
archive.ubuntu.com_ubuntu_dists_warty_main_source_Sources
archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Release
archive.ubuntu.com_ubuntu_dists_warty_restricted_source_Release
archive.ubuntu.com_ubuntu_dists_warty_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Release
archive.ubuntu.com_ubuntu_dists_warty_universe_source_Release
archive.ubuntu.com_ubuntu_dists_warty_universe_source_Sources
lock
partial
security.ubuntu.com_ubuntu_dists_warty-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_warty-security_main_binary-i386_Release
security.ubuntu.com_ubuntu_dists_warty-security_main_source_Release
security.ubuntu.com_ubuntu_dists_warty-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_warty-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_warty-security_restricted_binary-i386_Release
security.ubuntu.com_ubuntu_dists_warty-security_restricted_source_Release
security.ubuntu.com_ubuntu_dists_warty-security_restricted_source_Sources
kkathman@ubuntu:/var/lib/apt/lists $

What are the chances the the apt-get upgrade is going to un-synchronize things?

Thanks,
Kork

---

### Post by kkathman on 2005-03-21
I did go ahead and run all these and they all ran without error, so I guess everything is ok for the moment.

Thanks,
Kork

---

### Post by Buffalo Soldier on 2005-03-22
[QUOTE=kkathman]I did go ahead and run all these and they all ran without error, so I guess everything is ok for the moment.

Thanks,
Kork[/QUOTE]
 Sorry I didn't get back to you in time. Glad everything's working out fine for you :)

---

