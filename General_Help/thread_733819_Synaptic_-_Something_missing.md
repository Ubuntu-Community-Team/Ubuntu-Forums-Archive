---
title: "Synaptic - Something missing?"
date: 2008-03-24
forum: General Help
---

### Post by NotoriousTF on 2008-03-24
I think I have a problem with Synaptic Package Manager. I went to install a program "DeVeDe" after being told it was in the repositories, but it wasn't listed. Looking at Synaptic its only got 2,693 packages listed and 1,464 are installed. 

Surely that can't be right?? I remember looking through the list before seeing many, many more packages. Everything is selected on the Software Sources list too. Is there something missing?

---

### Post by mali2297 on 2008-03-24
The package [devede]("http://packages.ubuntu.com/gutsy/devede") should be available in the multiverse repository. In Synaptic, go to Settings -> Repositories and check that you have the repo enabled.

---

### Post by plucky on 2008-03-24
Mine says 23160 packages ```
cat /etc/apt/sources.list
``` can you post your sources list so we can see what repositories you have enabled? Thank you
Edit: Too late

---

### Post by NotoriousTF on 2008-03-24
Heres what I've got enabled. I've just notice the 'restricted universe multiverse' listed in the first two lines. Could it be something there?

```

NotoriousTF@NotoriousTF-laptop:~$ cat /etc/apt/sources.list

deb http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by mali2297 on 2008-03-24
Why do you have old edgy and feisty stuff there? :-?

Anyhow, try
```

sudo apt-get update

```
in the terminal. Any errors?

---

### Post by NotoriousTF on 2008-03-24
Ok that worked! It seems like there was some problems downloading from the Irish server as opposed to the main one; the connection to the Irish server kept on timing out. Switching to the main server sorted it all. Thank you, it had me quite confused.

---

### Post by zvacet on 2008-03-24
You have mixed source list which is not good.

```
gksudo gedit /etc/apt/sources.list
```

delete all lines which are not Gutsy.

```
sudo apt-get update
```

**system<software sources**>chack all boxes under Ubuntu software and updates tab.Reload.

---

### Post by NotoriousTF on 2008-03-24
Out of curiosity, why is a mixed source list not good? 

I gave it a clean-up as suggested and everything looks good now. Thank you.

---

