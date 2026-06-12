---
title: "Help!! Can't change anything"
date: 2006-12-15
forum: General Help
---

### Post by theaverageidiot on 2006-12-15
I tried to install figlet earlier and I got some error and I forgot about it. But now when I try to install or update ANYTHING I get this error:

"E: The package figlet needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

What's wrong?? :( :( :( I don't care about getting figlet working anymore I just want to get rid of that error!

---

### Post by po0f on 2006-12-16
theaverageidiot,

How did you try to install it?  Via command line?  Try using `aptitude` instead.

---

### Post by theaverageidiot on 2006-12-16
> **po0f said:**
> theaverageidiot,

How did you try to install it?  Via command line?  Try using `aptitude` instead.
I entered aptitude just now in command line. What is it? And I didn't use aptitude to install.

---

### Post by d3v1ant_0n3 on 2006-12-16
aptitude is a way of installing packages.

You can use it with terminal to install and remove packages in a similar way to apt-get. For example :

```
sudo aptitude install <package name> 
``` will install a given package (and any dependencies that is in the repos, whereas
```
sudo aptitude remove <package name>
``` will remove that package.

```
sudo aptitude purge <package name>
``` will remove a package and all it's config files.

If you need a more detailed explanation, in terminal type ```
man terminal
```

---

### Post by theaverageidiot on 2006-12-16
> **d3v1ant_0n3 said:**
> aptitude is a way of installing packages.

You can use it with terminal to install and remove packages in a similar way to apt-get. For example :

```
sudo aptitude install <package name> 
``` will install a given package (and any dependencies that is in the repos, whereas
```
sudo aptitude remove <package name>
``` will remove that package.

```
sudo aptitude purge <package name>
``` will remove a package and all it's config files.

If you need a more detailed explanation, in terminal type ```
man terminal
```

> sudo aptitude purge figlet
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  figlet{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing figlet (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 figlet
Aborted (core dumped)

:(

---

### Post by theaverageidiot on 2006-12-18
bump

---

### Post by ayoli on 2006-12-18
did you try the aptitude suggestion ? i mean reinatll your package , then remove it
```
sudo aptitude install figlet && sudo aptitude purge figlet
```

---

### Post by theaverageidiot on 2006-12-18
> **ayoli said:**
> did you try the aptitude suggestion ? i mean reinatll your package , then remove it
```
sudo aptitude install figlet && sudo aptitude purge figlet
```

root@[edit]s-computer:/home/[edit]# sudo aptitude install figlet && sudo aptitude purge figlet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the figlet package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by ayoli on 2006-12-18
> **theaverageidiot said:**
> root@[edit]s-computer:/home/[edit]# sudo aptitude install figlet && sudo aptitude purge figlet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the figlet package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
your prompt:
```
root@[edit]s-computer:/home/[edit]#
```
show you're root so you don't have to use sudo

---

### Post by theaverageidiot on 2006-12-18
> **ayoli said:**
> your prompt:
```
root@[edit]s-computer:/home/[edit]#
```
show you're root so you don't have to use sudo

Still doesn't work.

```
root@[edit]s-computer:/home/[edit]# aptitude install figlet && aptitude purge figlet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the figlet package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
```

---

### Post by theaverageidiot on 2006-12-18
bump again

---

### Post by ayoli on 2006-12-19
waht about trying:
```
sudo apt-get install -f
```
(without sudo if you're logged as root already)

---

### Post by theaverageidiot on 2006-12-19
> **ayoli said:**
> waht about trying:
```
sudo apt-get install -f
```
(without sudo if you're logged as root already)

```
[edit]@[edit]s-computer:~$ sudo apt-get install -f 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package figlet needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by theaverageidiot on 2006-12-19
bump

---

### Post by ayoli on 2006-12-19
do you have multiverse repos enabled ?
post your /etc/apt/source.list here if you dont know

---

### Post by theaverageidiot on 2006-12-19
Here it is:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://wine.budgetdedicated.com/apt dapper main
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
```

---

### Post by ayoli on 2006-12-19
> **theaverageidiot said:**
> Here it is:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://wine.budgetdedicated.com/apt dapper main
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
```
okay
```
gksudo gedit /etc/apt/sources.list
```
find this line:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
```
add multiverse at end of line so the line look like that after:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
```
then in a term:
```
sudo apt-get update && sudo apt-get -f install
```

---

### Post by theaverageidiot on 2006-12-19
Looks like it worked! Thanks!! Thank you very very much!! :D :D

---

### Post by huang earnie on 2006-12-23
.

---

