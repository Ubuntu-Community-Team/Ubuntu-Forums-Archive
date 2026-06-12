---
title: "Error fixing broken packages"
date: 2013-06-04
forum: General Help
---

### Post by sports fan Matt on 2013-06-04
Here is the error I get when trying to fix broken packages..any advice?

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by sports fan Matt on 2013-06-04
I think it's fixed.   Had to see which package was causing the error

---

### Post by sports fan Matt on 2013-06-04
Going to try and reinstall the entire Ubuntu desktop, since it completely erased all my packages.  Will post and see if I have any errors, but it may take a bit since I can only get in through the recovery

---

### Post by sports fan Matt on 2013-06-04
is there anyway to reinstall the entire system?  I tried a sudo altogether install Ubuntu desktop and was met with w:not using locking for read only lock file /var/lib/ dpkg/lock. e: unable to write to var/cache / apt  
E: package lists or status file could not be parsed  or opened. is it to late to save my ubuntu 1304 install?

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]sox fan Matt; Hi !

You must have some idea of how many thousands of versions and desk tops there are out there, so which one is yours ?
Can not help if I do not know what I am doing.
[/COLOR][INDENT][COLOR=#000000]
just a thought
 [/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-04
Hi bashing,

I am trying to run Ubuntu 13.04.  I had broken packages which I was able to remove trying to update the system, in which I got the error which is above.  I attempted a Sudo apt-get install Ubuntu-desktop, in which I had the error above.  All my packages were basically wiped off the map in trying to fix is one issue.  w:not using locking for read only lock file /var/lib/ dpkg/lock. e: unable to write to var/cache / apt
E: package lists or status file could not be parsed or opened. This is the error I received.

---

### Post by sports fan Matt on 2013-06-04
I dualboot this with W7 if it helps.

---

### Post by sports fan Matt on 2013-06-04
Can't find much help with google as I've tried to Suso-apt-get install ntu-desktop and tried to reconfigure -a without luck as well.

---

### Post by sports fan Matt on 2013-06-04
I'm just going to go ahead and re install.  I have a fast connection so it should only take a few hours. :)

---

### Post by sports fan Matt on 2013-06-04
I'll wait for a few hours to see if anyone has any advice. Didn't make any changes yet :)

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt; 

OK, Before you (re-)install the system. Have you tried this EXACT terminal command ?
[/COLOR]```
sudo apt-get install --reinstall ubuntu-desktop
```

see if that restores the desktop.[INDENT=2]
I be try'n to help

[/INDENT]

---

### Post by sports fan Matt on 2013-06-05
I know and thanks!  :)  Havent tried that.  Will in a few (have to get into recovery console) but first need to copy the command into my gmail.  Will report back.

---

### Post by sports fan Matt on 2013-06-05
No dice.  tried it both with spaces and without.  Same error was given as before.  Have no idea why.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

Well...might prove real helpful to know what the held packages are:
```
sudo apt-get update
sudo apt-get upgrade
```
[/COLOR][INDENT][COLOR=#000000]
just a thought

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
Ok, will try that as well :)

---

### Post by sports fan Matt on 2013-06-05
I tried the first command and got failed to fetch the archives of all the repository with - 11 system error

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

Best to post the exact error message the system is generating... recon ya got no internet connection ? 
```
ping -c 3 google.com
```
[/COLOR][INDENT][COLOR=#000000]
back to basics

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
W: failed to fetch http //us archive  ubuntu. Com/ubuntu dists raring-backporrs main binaries I386 /packages.  So basically it can't download any of the repositories and updates with all the errors (-11 system error).  And I have a connection but only in Windows. Typing on my phone so didn't want to post all the errors. Ping -c 3 Google. Communication gives me unknown host Google. Com

---

### Post by sports fan Matt on 2013-06-05
I do have a full connection in Windows 7.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt; 

well, ya got no connection in ubuntu... 

are you trying to connect WIFI ?? or is your internet connect wired (cable or DSL ) ??
[/COLOR][INDENT][COLOR=#000000]
recon we will get to the bottom in a bit

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
Sure don't.  The goal is to try and reinstall ubuntu without A).  destroying my windows partition and B).  Being able to boot into Ubuntu.  Not sure why all my packages went away. Internet is through Verizon Fios

---

### Post by sports fan Matt on 2013-06-05
It's fiber optic

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

WOW .. I can not imagine /// anyway ...
I am running 13.04 on a build-my-own, XFCE for a desk top and no network manager.... as I can not relate to your desktop... all I can presently advise you is to look into what you have for a network manager and it's settings and check your "host" file to see if your isp DNS is listed.
At the least DNS is not functioning on your system. Thus not able to resolve IP addresses.
[/COLOR][INDENT][COLOR=#000000]
might be a lot quicker at this stage just to (re-)install and be done with it

[/COLOR][/INDENT]
[INDENT=3][COLOR=#000000]just my thought

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
Think I will reinstall. If my parents

---

### Post by sports fan Matt on 2013-06-05
Crud,  hit the button too early.  If swap is on EXT 5, how can I delete it from my 9.04 live cd?

---

### Post by sports fan Matt on 2013-06-05
Scratch that.  Swap is on EXT 6 and SDA 5 is ext 4

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

woah... swap has no file system imposed on it ! It is formated as "swap" ...If I might suggest,,, in the liveDVD
```
sudo fdisk -lu
``` so you KNOW what partition is what...
with GParted in the liveDVD, delete the ubuntu partitions ....
in the install session , choose "something else" and tell the installer where you want to install ubuntu ...or simply make sure you choose the option to "install along side" if you are not real particular about the partitioning... just make doubly sure the installer is not going to overwrite Windows.
[/COLOR][INDENT=3][COLOR=#000000]
my thoughts

[/COLOR][/INDENT]

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

It is late, I am some kind of tired and my think'n has become difficult and cloudy...so I am going to retire for the spell...

lemme know how ya get on...[/COLOR][INDENT=2][COLOR=#000000]catch up with you later

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
Good to know.  I'd like to delete my 13.04 partition on dev/sda5 and start with 9.04 and run and upgrade from there  I can manually specify them but would rather start fresh.  Is there a way to delete Sda5 which has 13.04 and then allocate space for my new install?

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;
Sure you may delete sda5 ( keep present swap, and the new install will go much faster)... but version 9.04 ...no longer supported in any means,,,not at all advisable...for continued Long Term Support ...install 12.04 and yer good 'till the year 2017 !

edit: I am gone ..later !
[/COLOR][INDENT=2][COLOR=#000000]
what can I say ...desk top user version 12.04

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
Will do.  (kept it but will delete it when 12.04 is installed :)

---

### Post by sports fan Matt on 2013-06-05
Since I now have 12.04 installed, what is the best way to get rid of my 13.04 (which is on SDA 5 and allocate that space to my 12.04) which can still be on SDA5, correct?

---

### Post by sports fan Matt on 2013-06-05
Forgot to add I'm using Gparted

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt; Hey, Looking good...
As to modifications on your system. your system and only you know what you want, I can only relate to you what I do with my system and see if you like it.... 
for that old install on sda5, how 'bout making that into a -perhaps - shared partition between Windows and ubuntu ? or maybe dedicate that partition to ubuntu for "data" and backups ? You have to know what you want and come up with a plan... before anything can be done.

To see what you have on your set-up presently, show the output of terminal codes from the liveDCD (nothing mounted) :
[/COLOR]```
sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print #if you have more than one hard disk

``` and better advise can follow.[INDENT=2]
just my thought

[/INDENT]
[INDENT=2][COLOR=#000000]

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
I could do that.  :)  12.04 is installed with one minor hiccup.  I created a new sources.list but tried to add the tualtrix ppa, which gave me this error.  An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sabled' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-precise.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.'

Easy fix, but cant remember.  (Coming back after three years away from Ubuntu)

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### GNOME3 extra apps - [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

#### Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) precise main


####### 3rd Party Source Repos

#### GNOME3 extra apps (Source) - [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

#### Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) precise main

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt; 
You might do some further investigation of "tuallatrix". A quick check on my part indicates the last supported version (for the desk top anyway) was "lucid".

In the meantime, disable that source and try again.

Anytime one steps out from under ubuntu's umbrella of package management protection... best know why and what you are in for !
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
I erased everything tualtrix from my sources list and the line 2 is now blank as shown.  

Here is a new copy of my sources list but the error remains..hmm.  

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### GNOME3 extra apps - [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

#### Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220


####### 3rd Party Source Repos

#### GNOME3 extra apps (Source) - [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

#### Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

Post back the entire output of the error... will see what I can see// Bet there are other PPAs the package manager is not happy about.
[/COLOR][INDENT=2][COLOR=#000000]
look see do

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
E: Type 'sabled' is not known on line 1 in source list /etc/apt/sources.list.d/tualatrix-ppa-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Now I generated a brand new sources list (thinking that would solve the hiccup)  

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### GNOME3 extra apps - [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


####### 3rd Party Source Repos

#### GNOME3 extra apps (Source) - [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

---

### Post by sports fan Matt on 2013-06-05
That's a fresh sources list.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt; Hey,

Please read and heed the error message:
[/COLOR]> [COLOR=#000000]line 1 in source list /etc/apt/sources.list.d/tualatrix-ppa-precise.list[/COLOR][COLOR=#000000]
Tells you the file location is : /etc/apt/sources.list.d/ ->
The file name that has the bad line : tualatrix-ppa-precise ->
the line number : 1
The bad format : sabled

sooo...
load up a text editor -administrator mode -, point it to that directory "sources.list.d" on the path /etc/apt/
load into the editor the file [/COLOR][COLOR=#000000]tualatrix-ppa-precise.list and ,by looking at other files in the directory, fix the format error in line 1.

```
ls -la /etc/apt/sources.list.d/
``` A directory that contains other source list files.
[/COLOR][INDENT=2][COLOR=#000000]
reading is good for what ails you[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
Thanks.  I'm just very frustrated because it should be easy to fix.  (Maybe the faxct I've slept very little in the last 24 hours has something to do with it).  

It may take me a while cause I read this and it's over my head so far, but i'll keep trying :)

---

### Post by sports fan Matt on 2013-06-05
> **sox fan Matt said:**
> Thanks.  I'm just very frustrated because it should be easy to fix. 

It may take me a while cause I read this and it's over my head so far, but i'll keep trying :)

load up a text editor -administrator mode (So if I loaded up Gedit, and you say line 1 in source list /etc/apt/sources.list.d/tualatrix-ppa-precise.list..but when i loaded up my sources list I have this. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
 
(I guess I'm not seeing it when I type in  sudo gedit /etc/apt/sources.list to see mine.  Weird.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

 It ain't no big deal ...
Howto:
ctl_alt+t -> terminal
In that terminal enter:

```
sudo cp /apt/sources.list.d/tualatrix-ppa-precise.list /apt/sources.list.d/tualatrix-ppa-precise.list-orig #3backup just because
gksudo gedit /apt/sources.list.d/tualatrix-ppa-precise.list 

```
which will load that file for editing with admin authority. When ya looked at it, look at another file in that same directory to know how that line is to be formatted,,of the top of my head.... I would surmise that just removing the term "sabled" will most likely make that line conform to the expected syntax/format .... you will have to examine it and compare to make sure.

Make your edit and save the file;
```
sudo apt-get update
sudo apt-get upgrade
``` to see the {a,e}ffect.

And yeah, sleep deprivation does funny things to the mind !... take extra care !
[/COLOR][INDENT=2][COLOR=#000000]
ain't no step for a stepper
 [/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
We're close!  I see the file which you are wanting me to edit, but it's blank, meaning sabled is not there obviously..So I'm not sure sure if you want me to imput something into there or leave it blank.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt; 

I am tired too, so perhaps I made an error ...lets look this way
```
 ls -la /etc/apt/sources.list.d/
```

also, I am having some problems in transitioning "copy/paste" between google-chrome/forum post. Don't have it nailed yet, so having to watch and catch the "errors" that happen.
[/COLOR][INDENT=2][COLOR=#000000]
see if a tale is to be told

[/COLOR][/INDENT]

---

### Post by sports fan Matt on 2013-06-05
total 52
drwxr-xr-x 2 root root 4096 Jun  5 14:52 .
drwxr-xr-x 6 root root 4096 Jun  5 19:51 ..
-rw-r--r-- 1 root root   64 Jun  5 11:35 alecive-antigone-lucid.list.distUpgrade
-rw-r--r-- 1 root root   64 Jun  5 11:34 alecive-antigone-lucid.list.save
-rw-r--r-- 1 root root    0 Jun  5 17:21 alecive-antigone-precise.list
-rw-r--r-- 1 root root   99 Jun  5 17:21 alecive-antigone-precise.list.save
-rw-r--r-- 1 root root   62 Jun  5 11:35 tiheum-equinox-lucid.list.distUpgrade
-rw-r--r-- 1 root root   62 Jun  5 11:34 tiheum-equinox-lucid.list.save
-rw-r--r-- 1 root root    0 Jun  5 17:21 tiheum-equinox-precise.list
-rw-r--r-- 1 root root   97 Jun  5 17:21 tiheum-equinox-precise.list.save
-rw-r--r-- 1 root root   61 Jun  5 11:35 tualatrix-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root   61 Jun  5 11:34 tualatrix-ppa-lucid.list.save
-rw-r--r-- 1 root root   29 Jun  5 19:12 tualatrix-ppa-precise.list
-rw-r--r-- 1 root root   29 Jun  5 19:12 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root    0 Jun  5 17:20 ubuntu-tweak-stable.list
-rw-r--r-- 1 root root   89 Jun  5 17:20 ubuntu-tweak-stable.list.save


Now I see them, but unsure how to get rid of them :)

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]sox fan Matt;

The file is there and I find no error in comparrison to what is and what I submitted
That file in non-zero in length so must have content,
ergo ya made a typo and the editor did not open the desired file... try again with CARE. (copy and paste)

As to removal of any file there --- get rid of the old lucid ones for sure ---just remove them:
```
cd /etc/apt/sources.list.d/
sudo rm <file_name>
```
and they are gone and the package manager will never see them again.[INDENT=3]BE VeRy Carefull, once "rm'd" they are gone, no getting back, linux does not forgive errors !
[/INDENT]
[INDENT=4]
[/INDENT]
[INDENT=5]are we there yet ?

[/INDENT]

[/COLOR]

---

### Post by sports fan Matt on 2013-06-05
I got rid of those but the problem remains...Strangely the same error even after I got conformation they were deleted.  'E:Type 'sabled' is not known on line 1 in source list /etc/apt/sources.list.d/tualatrix-ppa-precise.list'.  Have no idea why.  Got it when running the update manager.  (And the lucid ones are gone with rm: cannot remove `alecive-antigone-lucid.list.distUpgrade': No such file or directory)...So I know they are deleted

---

### Post by sports fan Matt on 2013-06-05
Ok brain dead moment.  Let me go and see if when I remove them ALL the message disappears.  (Only did the ones from lucid)

---

### Post by sports fan Matt on 2013-06-05
Finally fixed. Thank you so much for your bearing with me :)

---

### Post by Bashing-om on 2013-06-06
[COLOR=#000000]sox fan Matt; 

Outstanding, glad it is all sorted out ... up and running !
Now let me advise you to avail yourself of the opportunity to read the sticky in the beginners forum "How to get your questions answered ...."

If you had of known and presented the needed info instead of prying it out of you; This situation would have been readily resolved.
But, it is all a process of learning.

Please mark this thread as solved, aide others seeking similar solutions, and helps keep the forum tidy.
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT]
and as always enjoy, make the best of it[/INDENT]

---

