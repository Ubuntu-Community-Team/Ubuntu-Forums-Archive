---
title: "Problems with Edgy"
date: 2006-11-14
forum: General Help
---

### Post by 2pacalypse on 2006-11-14
I upgraded into Edgy Eft. yesterday (from Dapper Drake) and currently I'm kinda unhappy with Edgy, due to the fact the it took 2.5 days to upgrade and the fact that it deleted half of my system (including XServer :S) from some unknown reason, i already fixed the XServer problem however after fixing it I've found several additional problems which need fixing

A) All my fonts are messed up, and all of the sudden all of my system is using some weird, barely readable font on ALL the applications, whether it is  Nautilus,FireFox System files, Terminal etc. and i wish to return all my font back to its original form before the upgrade (as it was in default) I know that there is an option for changing the fonts in System->Preferences->Font but I dont like anyone of those fonts

B)My Desktop Icon are twice as large, and theres annoying Computer and trash icons which i cannot delete. furthermore theres details about files that i do not need (Size, amount of files in folder etc.) right below the file/folder name

C)My Nautilus seems to be without a command line or anything like that... theres only the line with "File, Edit" and those stuff

D)Around 60% of all my programs/files/configurations are lost, and i seek a way to retrieve them

any help with these problems will be much appreciated ;)

Thanks in advance

---

### Post by taurus on 2006-11-14
How did you upgrade from Dapper to Edgy?

---

### Post by 2pacalypse on 2006-11-14
as it was written in a wiki i found

```

 sudo aptitude update && sudo aptitude upgrade

gksudo "update-manager -c -d"

sudo apt-get dist-upgrade
```

EDIT:

I found two additional problem with Nautilus, first one is when I open a folder, he opens it in a new window and closes the first windows with a flash that really really hurts your eyes... the secound is that if you do back (which can only be done by keyboard cuz the back button is missing) it opens the folder in a new window (though i want it in the same window)

---

### Post by darrenm on 2006-11-14
Sounds like the gnome-settings-daemon isnt running. 

Can you check your repositories are all Edgy 
```
cat /etc/apt/sources.list
```
Then do a 
```
sudo apt-get update
```
Then
```
sudo apt-get install -f
```
```
sudo apt-get dist-upgrade
```
and reboot.

---

### Post by 2pacalypse on 2006-11-14
ok, heres the cat output

```

## Edgy Repo
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main

#deb http://packages.freecontrib.org/plf/ edgy free non-free
#deb-src http://packages.freecontrib.org/plf/ edgy free non-free 

## End of Edgy Rep

## Dapper Repo

## Uncomment the following two lines to fetch updated software from the network
##deb http://archive.ubuntu.com/ubuntu dapper main restricted
##deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
##deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
##deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
##deb http://archive.ubuntu.com/ubuntu dapper universe
##deb-src http://archive.ubuntu.com/ubuntu dapper universe

##deb http://security.ubuntu.com/ubuntu dapper-security main restricted
##deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

##deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

##deb http://archive.ubuntu.com/ubuntu dapper multiverse
##deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

##deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

##deb http://archive.canonical.com/ubuntu dapper-commercial main

##deb http://packages.freecontrib.org/plf/ dapper free non-free
##deb-src http://packages.freecontrib.org/plf/ dapper free non-free

## End of Dapper Repo


## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

## skype
## only uncomment it if you need it
deb http://download.skype.com/linux/repos/debian/ stable non-free
anarch@anarch-desktop:~$ 

```

I know theres some Dapper Repo's there still, I placed them myself if any future need will occur, right not its with ## so ubuntu just ignored them ;)

heres the output from the third command

```

anarch@anarch-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt-odbc libiodbc2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

and heres the output from the dist-upgrade

```

anarch@anarch-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kompile
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
anarch@anarch-desktop:~$ 

```

---

### Post by taurus on 2006-11-14
Wait a second!  How come you have dapper in your /etc/apt/sources.list while your system is running Edgy???  Disable the lines with dapper in them by placing a # in front and update/upgrade it again!!!

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by 2pacalypse on 2006-11-14
I disabled it even before i ran the updater. They already have ## infront of them... the only Repo's which i havent disabled are the skype, wine and Edgy repo's

the Repo's are fine, and Edgy works ok, theres only the font&Nautilus problems... about the missing programs and configurations it doesnt really matter because I already reconfigurated and reinstall a large part of the missing files

---

### Post by 2pacalypse on 2006-11-15
I found another problem, My Ubuntu Cannot Read,Write or work in Hebrew at all... whenever i open anything in Hebrew all i see are square shapes

Can Any1 plz help me out with these problems? i really really need help

---

### Post by 2pacalypse on 2006-11-18
Can Any1 please help me out with this problem. Its been 3 days already and its really really bugging me

---

### Post by darrenm on 2006-11-18
Someones already said. You still have a Dapper repo uncommented.

---

### Post by 2pacalypse on 2006-11-21
I already uncommented even before the dist upgrade. and it didnt worked, I removed it shortly after he said to uncomment it... still it doesnt work.

---

