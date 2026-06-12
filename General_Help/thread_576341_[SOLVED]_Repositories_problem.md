---
title: "[SOLVED] Repositories problem"
date: 2007-10-15
forum: General Help
---

### Post by deformation on 2007-10-15
Hello all

I've been using Xubuntu for more than 8 months now, i am on the feisty Xubuntu now..

i had no problem whatever related to installing from synaptic or updating my system (which i do daily)

but i am having this annoying problem right now when updating or using synaptic, which is showing me that there are upgradable programs in the list ( transmission, liferea feed reader, tea , gYachi, leafpad, and some other programs) but IT CANNOT UPGRADE THEM, it is showing me an error telling me somthing like : (The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.)

what i did, (actually a stupid act ) is removing (uninstalling) the unupgradable programs from synaptic, and then trying to install them again, which gave me the same message > ( Could not mark all packages for installation or upgrade...The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.)

how can i solve this problem? 
and if the error was because i did something wrong, can anyone point me to what did i do?


here is my sources.list

> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main
deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) feisty main restricted
deb [http://www.ubuntume.com/repository](http://www.ubuntume.com/repository) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main


Thanks in advance.

---

### Post by wormser on 2007-10-15
Try removing the comments on the following lines.

> # deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy universe

# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


Then do a sudo apt-get update.

---

### Post by deformation on 2007-10-15
i did not get it, why should i enable the edgy repo while i am on feisty? and what would the backports repo help me with?

---

### Post by wormser on 2007-10-15
> **deformation said:**
> i did not get it, why should i enable the edgy repo while i am on feisty? and what would the backports repo help me with?

I did not notice that.  It looks like you have a mix of feisty and edgy through out you whole source.list.  Maybe this has something to do with it.  I also did not see a Feisty Universe repository.  Take a look at System> Administration> Software Sources.  See if Universe and Multiverse are checked.  The whole file looks like a mess to me and I am not sure what else to do.

---

### Post by deformation on 2007-10-15
Thanks for the reply, Yes in the software sources the universe and multiverse are enabled.

if my sources.list is missed up can someone kindly correct it for me, or post their source.list, i think it will be the same as mine, i do not have any strange repo on my list i think. 

how can i install the software back? and get lost of these annoying errors?

---

### Post by PmDematagoda on 2007-10-15
Edit your sources.list file by disabling these repos with the # as shown:-

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
#deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
#deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
#deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main
#deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
#deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

And try again.

---

### Post by deformation on 2007-10-15
I did like what you said, and disabled the mentioned repo, but the error still the same.

 for example, here is what the terminal gives me after the command apt-get install liferea :

> 
deformation@deformation-laptop:~$ sudo apt-get install liferea
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  liferea: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
           Depends: libdbus-1-3 (>= 1.1.1) but 1.0.2-1ubuntu4 is to be installed
           Depends: libdbus-glib-1-2 (>= 0.74) but 0.73-1 is to be installed
           Depends: libglade2-0 (>= 1:2.6.1) but 1:2.6.0-3 is to be installed
           Depends: libglib2.0-0 (>= 2.14.0) but 2.12.11-0ubuntu1 is to be installed
           Depends: libgnutls13 (>= 1.6.3-0) but 1.4.4-3build1 is to be installed
           Depends: libgtk2.0-0 (>= 2.12.0) but 2.10.11-0ubuntu3 is to be installed
           Depends: libnotify1 (>= 0.4.4) but 0.4.3-1 is to be installed
           Depends: libnotify1-gtk2.10 but it is not installable
           Depends: liborbit2 (>= 1:2.14.8) but 1:2.14.7-0ubuntu1 is to be installed
           Depends: libpango1.0-0 (>= 1.18.2) but 1.16.2-0ubuntu1 is to be installed
           Depends: libsqlite3-0 (>= 3.4.2) but 3.3.13-0ubuntu1 is to be installed
           Depends: libxdamage1 (>= 1:1.1) but 1:1.0.3-3 is to be installed
           Depends: libxml2 (>= 2.6.29) but 2.6.27.dfsg-1ubuntu3 is to be installed
           Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
           Depends: liferea-mozilla (= 1.4.5b-1~getdeb1) but it is not going to be installed
E: Broken packages
deformation@deformation-laptop:~$ 


any ideas?

---

### Post by bapoumba on 2007-10-15
Please paste your modified source.list again. Make sure you have only feisty repos, for main, restricted, universe, multiverse, and comment all the third party repos. Basically, you source.list should be like:
```

# Base.
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

# Security.
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

```
You need to run:
```
sudo apt-get update
```
To reload the repos before you can install anything.

---

### Post by deformation on 2007-10-15
Thanks for the reply,

I did what you said and disabled all the other repo, here is what my sources.list look like now :

> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
#deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
#deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
#deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main
#deb [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
#deb-src [http://hydr0g3n.free.fr/qbittorrent/feisty/](http://hydr0g3n.free.fr/qbittorrent/feisty/) ./
#deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
#deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
#deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) feisty main restricted
#deb [http://www.ubuntume.com/repository](http://www.ubuntume.com/repository) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main


that magically fixed the problem, i already installed liferea again, but now after disabling the other repos, i cannot find the other packages (i.e trasmission, gYache...)

and if you dont mind, please can you tell me whats the proper way to add repos to the list? and for the old repos how can i activate them again without the error back?


thanks in advance.

---

### Post by bapoumba on 2007-10-15
You still have a line that you should remove:
```
deb http://security.ubuntu.com/ubuntu edgy-security universe
```
You can just delete all the edgy lines from the source.list.

And you are still missing universe and multiverse (comapre with the one I suggested).
The packages you mentionned are not in the ubuntu repositories (or not by these names). Where did you get them from ?

---

### Post by deformation on 2007-10-15
I deleted the wholw edgy repositories, and about the 3rd party repos, i took it from an article once posted on lifehacker.com, it was (first 10 things to do when installing ubuntu) or somthing near :)

i have 3 questions (please be patient with me) :

1. how do i add the missing repostries you told me about (universe and multiverse) properly?
2.where can i find the proper 3rd party repositories (for example, getdeb.net, beryl, etc..)?
3.is Ubuntu sources.list generator website any useful for me to create a fresh new list?

edit..

here is the list generated from source-o-matic :

> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://my.archive.ubuntu.com/ubuntu](http://my.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) feisty-seveas all 

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

# Upstream Opera
# GPG key: 6A423791
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 

# Upstream Beryl
# GPG key: ed8a569e
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main 

needs any correction/add/remove?



Thanks in advance.

---

### Post by bapoumba on 2007-10-16
Hello, sorry I did not answer last night. I was in the middle of my answer and boom! Everything shut down on me :D

The source.list is fine, I just see etch (debian) and edgy repos that I would remove.
For beryl and Opera, browse the forums, you'll see what other people use.

The sources.list file tells the package manager where to fetch packages. You should use only Ubuntu repos (and not debian ones) and the same release repos (and not edgy ones), this to prevent dependencies issues, or bigger problems.

To edit the sources.list, you can use **nano**, a small text editor working in a terminal.
Open a terminal (> Accessories > Terminal).

First save the file before you edit it:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak

```
After _bak, I usually place the date (for ex 071016) and the rev (v1 etc..) so that I can easily retrieve my backups.

Open the file with nano:
```
sudo nano /etc/apt/sources.list
```
Make the changes.
Save the file with CTRL-O.
Exit with CTRL-X.
Reload the file:
```
sudo apt-get update
```

---

### Post by deformation on 2007-10-16
Thanks for the reply, and again sorry for all the headache :)

i did like what you said, but with gedit as i am used to it, i made a backup list and pasted the new repositories (source-o-metric) and did the apt-get update..

then i found a hell of errors telling me about the GPG key, thats when i stopped, how should i run these commands to get the GPG key :

gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -

i mean all at once. or 1 by 1, and where at this command should i place the GPG key of each repo?


another question, (since its free knowledge :) ), i go to my software sources under the system menu, and i found that the old repos still there, isnt that strange? whats the differance between editing the sources.list manually by nano or gedit and editting it from the software sources GUI ?

eveything is so messed up, i want everything to become fine and prepared to welcome gutsy :)


thanks in advance

---

### Post by deformation on 2007-10-17
i think i figured out how to fix the GPG key thing, you have to run the commands i mentioned separtly with the key :)


thanks for help guys

i will mark this as solved.

---

### Post by bapoumba on 2007-10-17
Oh sorry, I thought I had replied.. Cheers and enjoy!
For one repo, you can chain the two commands with **&&** on a single line (the second will be executed if the first one is successful ;))

---

