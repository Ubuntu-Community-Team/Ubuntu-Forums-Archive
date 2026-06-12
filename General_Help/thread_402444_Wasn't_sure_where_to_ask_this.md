---
title: "Wasn't sure where to ask this"
date: 2007-04-05
forum: General Help
---

### Post by Hymn on 2007-04-05
I keep recieving errors like this...

> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages


and its preventing me from installing... wine, beryl

:\

---

### Post by x64Jimbo on 2007-04-05
Have you tried using Synaptic to manage your software installation? It usually fixes problems like that automatically.

---

### Post by Hymn on 2007-04-05
> **x64Jimbo said:**
> Have you tried using Synaptic to manage your software installation? It usually fixes problems like that automatically.

I had been using it, it also yells at me for dependencies.

---

### Post by johnc4510 on 2007-04-05
Try this in a terminal:

sudo apt-get -f install

This command fixes package problems

---

### Post by Hymn on 2007-04-05
> **johnc4510 said:**
> Try this in a terminal:

sudo apt-get -f install

This command fixes package problems

```
hymn@hymn-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

```

???  What now?

---

### Post by johnc4510 on 2007-04-05
Try these 2 commands, one at a time.

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by Hymn on 2007-04-05
> **johnc4510 said:**
> Try these 2 commands, one at a time.

sudo apt-get update

sudo apt-get dist-upgrade

```
hymn@hymn-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  bluez-pcmcia-support foomatic-db-gutenprint gok gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  ijsgutenprint libcompfaceg1 libgnutls12 libnetcdf3 libtasn1-2 libwnck18
  pcmcia-cs python-gadfly python-htmltmpl python-kjbuckets python-netcdf
  python-parted
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
hymn@hymn-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  bluez-pcmcia-support foomatic-db-gutenprint gok gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  ijsgutenprint libcompfaceg1 libgnutls12 libnetcdf3 libtasn1-2 libwnck18
  pcmcia-cs python-gadfly python-htmltmpl python-kjbuckets python-netcdf
  python-parted
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
```

---

### Post by johnc4510 on 2007-04-05
Sorry, I don't know what to tell ya.

---

### Post by Hymn on 2007-04-05
> **johnc4510 said:**
> Sorry, I don't know what to tell ya.

>_< ima cry.  This is so annoying.


Possibly a bad install?  I could get a fresh install and start again.

---

### Post by tgm4883 on 2007-04-05
I don't suppose your sources.list is all screwed up?

---

### Post by Hymn on 2007-04-05
> **tgm4883 said:**
> I don't suppose your sources.list is all screwed up?

Lets find out shall we?

> deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
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

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


Not sure if this should look different or not

---

### Post by Hymn on 2007-04-05
>_> someone has to know whats wrong?

---

### Post by WW on 2007-04-05
You are mixing dapper and edgy repositories.  That is probably a bad idea.

---

### Post by Hymn on 2007-04-05
> **WW said:**
> You are mixing dapper and edgy repositories.  That is probably a bad idea.

I'll remove the dapper repository, I think I added it when I was mindlessly following an old guide.

---

### Post by tgm4883 on 2007-04-05
> **WW said:**
> You are mixing dapper and edgy repositories.  That is probably a bad idea.

In Adam's voice from mythbusters "Well there's your problem"

---

### Post by Hymn on 2007-04-05
> **tgm4883 said:**
> In Adam's voice from mythbusters "Well there's your problem"

It didn't change anything, I don't think I used that source for anything inparticular.

Perhaps if I unstalled all the packets its "excluding" then reinstalled them?



on a victorious off topic footnote: I sucessfully setup a LEAP wireless connection ^_^

---

### Post by Stochastic on 2007-04-05
after you removed the edgy repositories did you "apt-get update" then "apt-get  -f install" then "apt-get upgrade" then "apt-get dist-upgrade"?

---

### Post by Stochastic on 2007-04-05
> **Hymn said:**
> I don't think I used that source for anything inparticular.

You do realize that you've got an edgy universe repo in the mix too, not just edgy beryl and wine repos.  That's probably the main issue here.  It would certainly explain the errors you've recieved.

---

### Post by Hymn on 2007-04-06
> **Stochastic said:**
> You do realize that you've got an edgy universe repo in the mix too, not just edgy beryl and wine repos.  That's probably the main issue here.  It would certainly explain the errors you've recieved.
Thank you >_<

This is starting to make a lot of sense now.

---

### Post by WW on 2007-04-06
Stochastic: If he has edgy installed, there should not be a problem with using the universe repository, but maybe I am missing something.  Why would that explain the errors?

---

### Post by Hymn on 2007-04-06
> **WW said:**
> Stochastic: If he has edgy installed, there should not be a problem with using the universe repository, but maybe I am missing something.  Why would that explain the errors?
No that IS the problem.  I'm running a dapper release version.


Now the question of the moment is, is there a way I can update from Dapper Drake to Edgy Eft without a CD?

---

### Post by Maestro23 on 2007-04-06
Edgy Upgrade: [https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28edgy%29%7C%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28edgy%29%7C%28upgrade%29)

---

### Post by WW on 2007-04-06
OH!  That's different. :)

When you said earlier that you would remove a dapper repository, I assumed that meant that you were using edgy.

---

### Post by Hymn on 2007-04-06
> **WW said:**
> OH!  That's different. :)

When you said earlier that you would remove a dapper repository, I assumed that meant that you were using edgy.
Saying this is going to make me sound like a retard, but my friend installed ubuntu for me, because I asked him to.  He told me he updated the system to the current version, in which I assumed was edgy after reading about it.  This solves ALOT of problems :)

Anyways, thanks for all your help, now I can go install everything.

---

### Post by Stochastic on 2007-04-06
> **WW said:**
> Stochastic: If he has edgy installed, there should not be a problem with using the universe repository, but maybe I am missing something.  Why would that explain the errors?

He doesn't have any edgy main repos in his listing so I took the liberty of assuming (maybe I made an a** out of myself) that he didn't have edgy installed.  If that were the case I think the issue would be not having the edgy main repo but rather the dapper main repo.

---

