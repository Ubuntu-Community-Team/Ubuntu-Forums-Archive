---
title: "big problem with automatix"
date: 2007-09-04
forum: General Help
---

### Post by yousufinternet on 2007-09-04
hi every body 
i am facing a serious problem with ubuntu just after i installed automatix 
now i can't remove it or install any new package 
when i try to install a package i get this error messege (attached)

---

### Post by confused57 on 2007-09-04
What you might do is open Automatix, then click on "file"...I think there is an option to remove any extra repositories added by Automatix.  May not work, but worth a try.

If you can't open Automatix, you could remove any extra repositores in your sources.list:
```
cd /etc/apt
sudo cp sources.list sources.list_backup
gksudo gedit sources.list
```

delete the extra repositories added by Automatix, except maybe the "...getautomatix.." repository, quit & save

---

### Post by yousufinternet on 2007-09-04
i already tried to do this but the same problem still appears

---

### Post by ryno519 on 2007-09-04
> **yousufinternet said:**
> i already tried to do this but the same problem still appears

Looks like there is another package manager open already. When you try to run automatix do you have Synaptics Package Manager, Update Manager or an installer running? You can't run multiple package managers at the same time. Think Highlander... there can be only one.

---

### Post by yousufinternet on 2007-09-04
thanks but i am not running any package manager with automatix and i know that i have not to run two package managers at the same time :)
the problem appears when i try to install any package or remove it even from the terminal
thanks anyway

---

### Post by Vadi on 2007-09-04
That's one of the reasons I didn't bother with Automatix... read too many posts that it'll fsck up your system.

---

### Post by kellemes on 2007-09-04
> **Vadi said:**
> That's one of the reasons I didn't bother with Automatix... read too many posts that it'll fsck up your system.

Agree..
And installing stuff without Automatix isn't like rocket science either.

---

### Post by por100pre1 on 2007-09-04
I remember when Automatix messed up my /etc/apt/sources.list and I ended up fixing it manually. Do yourself a favor: stay away from it!

---

### Post by yousufinternet on 2007-09-04
i will never install it again 
but the problem that i can't remove it!!!!
:(

---

### Post by yousufinternet on 2007-09-04
up

---

### Post by por100pre1 on 2007-09-04
```
sudo aptitude update && sudo aptitude upgrade
```

```
sudo apt-get remove --purge automatix
```

Post the results if it doesn't work... :-k

---

### Post by kelvin spratt on 2007-09-04
just go to their forum if you have a problem thousands of people use it without problems, some people do get problems, i've never had a problem with it on this or any other distro.

---

### Post by por100pre1 on 2007-09-04
> **kelvin spratt said:**
> just go to their forum if you have a problem thousands of people use it without problems, some people do get problems, i've never had a problem with it on this or any other distro.

Glad to know Automatix works for you, but the problem here is that the OP is *actually* having problems with it.

---

### Post by yousufinternet on 2007-09-04
> **por100pre1 said:**
> ```
sudo aptitude update && sudo aptitude upgrade
```

```
sudo apt-get remove --purge automatix
```

Post the results if it doesn't work... :-k

thanks very much for help 
the result of the first command 
E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Couldn't lock list directory..are you root?

the result of the seconed command (sudo apt-get remove --purge automatix2)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgdk-pixbuf2 libuninameslist0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  automatix2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by por100pre1 on 2007-09-04
The partial folder is missing, lets create it:

```
sudo mkdir /var/lib/apt/lists/partial
```

Try again and post the results... :-k

---

### Post by yousufinternet on 2007-09-05
here is the results :(
mkdir: cannot create directory `/var/lib/apt/lists/partial': No such file or directory

---

### Post by yousufinternet on 2007-09-05
up
now what should i do????
re install ubuntu 
i have a lot of games and programs installed and i can't download and install them again !!!!

---

### Post by yousufinternet on 2007-09-05
up

---

### Post by yousufinternet on 2007-09-05
up
any help??? 
:(

---

### Post by por100pre1 on 2007-09-05
Let's see what you got there
```
cd /var/lib/apt/lists/
```

```
ls
```

post the results... :-k

---

### Post by yousufinternet on 2007-09-05
bash: cd: /var/lib/apt/lists/: No such file or directory
:(

---

### Post by yousufinternet on 2007-09-05
ok can anybody attach his sources.list file :)

---

### Post by por100pre1 on 2007-09-05
Here's mine:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://pr.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://pr.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pr.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://pr.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pr.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://pr.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pr.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://pr.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://pr.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://packages.medibuntu.org/ feisty free non-free
```

Hope it helps. :)

---

### Post by yousufinternet on 2007-09-05
i replaced my sources.list with yours but the problem still appear so i will reinstall ubuntu again 
but before i do this i want to ask if i have downloaded the debian cds can i use them as reposetories and install packages from them :)

---

### Post by por100pre1 on 2007-09-05
> **yousufinternet said:**
> i replaced my sources.list with yours but the problem still appear so i will reinstall ubuntu again 
but before i do this i want to ask if i have downloaded the debian cds can i use them as reposetories and install packages from them :)

You can face issues with those repos. Use APTonCD (if you have it already installed) to back up your packages, or use the [Ubuntu DVD]("http://nginyang.uvt.nl/"). Backup your whole home folder before proceeding

---

### Post by yousufinternet on 2007-09-05
i have aptoncd installed but how i can backup my current installed packaged on cd :)
and thank you very much for your help

---

### Post by yousufinternet on 2007-09-05
the problem when i open the program and select create aptoncd 
he opens a window (attached) and no packages inside it

---

### Post by por100pre1 on 2007-09-05
It seems there are not any packages to save, very bad! By the way, can you use sudo command? Does it work well otherwise?

---

### Post by yousufinternet on 2007-09-05
yes i can use it 
i have installed a program called apt-mirror 
[http://www.linux.com/feature/115226](http://www.linux.com/feature/115226)

---

### Post by JimmyJazz on 2007-09-05
have you  tried googling your problem?
```
sudo apt-get clean
cd /var/lib/dpkg
ls -la | grep lock
mv lock lock.old
```

---

### Post by yousufinternet on 2007-09-06
when i type 
sudo apt-get clean
i get 
E: Lists directory /var/lib/apt/lists/partial is missing

---

### Post by JimmyJazz on 2007-09-06
```
cd /cd /var/lib/apt/lists/
sudo rm ./partial -R
sudo mkdir /var/lib/apt/lists/partial
```

---

### Post by JimmyJazz on 2007-09-06
if that last one doesn't work do...

```
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
```

---

### Post by afonic on 2007-09-06
Why don't you ask in Automatix forum?

[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

Not saying that you are not welcomed here but there you may get help from the creators of Automatix as well. :)

---

### Post by yousufinternet on 2007-09-06
> **JimmyJazz said:**
> ```
cd /cd /var/lib/apt/lists/
sudo rm ./partial -R
sudo mkdir /var/lib/apt/lists/partial
```
the first one : bash: cd: /cd: No such file or directory
the seconed : rm: cannot remove `./partial': No such file or directory
and thanks for help

---

### Post by yousufinternet on 2007-09-06
> **JimmyJazz said:**
> if that last one doesn't work do...

```
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
```

wow it worked 
all i have to do is to run this command while the add/remove dialog is open
thanks you very much

---

### Post by kelvin spratt on 2007-09-06
AS i Said Earlier Go To The Automatix forum and get Arnie to help you. much easier than reinstalling Feisty.

---

### Post by yousufinternet on 2007-09-06
> **kelvin spratt said:**
> AS i Said Earlier Go To The Automatix forum and get Arnie to help you. much easier than reinstalling Feisty.

i have already done this sir :)

---

### Post by kelvin spratt on 2007-09-06
I was only trying to help I'm glad you got it sorted hopefully without having to reinstall. some programs work for some and not for others ive also had my share of problems with some programs and its frustrating to say the least.

---

### Post by Vadi on 2007-09-06
I've *never* had a problem installing *any* program with the add/remove tool.

I think I'm onto something...

Anyway, glad everything's sorted out now.

---

### Post by JimmyJazz on 2007-09-06
> **yousufinternet said:**
> i have already done this sir :)

I am an Automatix dev. I followed your post from the AX forum to here.
glad it helped.

---

### Post by TrashmanL on 2007-09-09
Hey, I finally found a thread about Automatix issues. JimmyJazz... you're an automatix dev... just the person I need to talk to. I can't get to getautomatix.com either in my browser or in my sources.list file. For the last couple days, it says it can't find it. Is the site down? Or is it possible my ISP has blocked it? Everything else seems to be working for me.

---

### Post by dirtblack on 2007-09-09
I have the same problem, I'd say it's down.

---

### Post by whittle261270 on 2007-09-09
> **confused57 said:**
> What you might do is open Automatix, then click on "file"...I think there is an option to remove any extra repositories added by Automatix.  May not work, but worth a try.

If you can't open Automatix, you could remove any extra repositores in your sources.list:
```
cd /etc/apt
sudo cp sources.list sources.list_backup
gksudo gedit sources.list
```

delete the extra repositories added by Automatix, except maybe the "...getautomatix.." repository, quit & save

Thanks for the tip, similar problem with synaptics, sources.list had an error, I could not work out how to edit it as I am a recent MS refugee, the tip was very useful and saved much stress.

---

