---
title: "Error with Sudo Apt-Get Update &amp; all Package Managers"
date: 2007-08-16
forum: General Help
---

### Post by granny4linux on 2007-08-16
When I run Update Manager, Adept, Synaptic or sudo apt-get update 
I get the following error:

"Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libpoppler1-qt (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."


I've searched through the forums and cannot seem to find a similar problem.

Does anyone have a suggestion to help me fix this problem? Thanks for your time.

---

### Post by loserboy on 2007-08-16
can you post your sources list, and are you running automatix

---

### Post by granny4linux on 2007-08-16
Thanks for your response.

I have Automatix installed. 

Sources list follows:

"# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

###Avant Navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

### Google picasa
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

##Opera Repo added by suzanne 5-22-07
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

## suzanne added the following line to get gscan2pdf for scanning 
deb [http://gscan2pdf.sourceforge.net/download/debian](http://gscan2pdf.sourceforge.net/download/debian) binary/"

---

### Post by loserboy on 2007-08-16
ok first I wanna try something, comment all the AX repos and try to $ sudo aptitude update

if that doesn't work uncomment them and follow the steps on this link [http://ubuntuforums.org/showthread.php?t=447121&page=2](http://ubuntuforums.org/showthread.php?t=447121&page=2)

---

### Post by granny4linux on 2007-08-16
> **loserboy said:**
> ok first I wanna try something, comment all the AX repos and try to $ sudo aptitude update

if that doesn't work uncomment them and follow the steps on this link [http://ubuntuforums.org/showthread.php?t=447121&page=2](http://ubuntuforums.org/showthread.php?t=447121&page=2)

I commented AX repos; did sudo apt-get update and still got the error.

However when I followed these instructions from the referenced UbuntuForum post:
"Hardcore method:
1. Search in the both files:
Code:
$ sudo gedit /var/lib/dpkg/available
$ sudo gedit /var/lib/dpkg/status
for the corrupted package and delete its whole block entry."

I was a bit confused about what corrupted package I was looking for to delete.
I looked for instances of "libpoppler" and deleted those block entries; which included "Evince" and "libpoppler1". 

I'm still clueless, thanks for your efforts.

---

### Post by loserboy on 2007-08-16
> I had this issue, and doing the following worked for me:


```

$sudo gedit /var/lib/dpkg/status
```

Press Ctrl +A to select everything, then press delete to delete the contents of the file. Save (Ctrl +s) and close (Ctrl +w).

Back at the CLI

```
$sudo rm -f /var/lib/dpkg/lock
```

Now you should be able to run update manager, synaptic, aptitude or apt-get.


```
$sudo apt-get install dpkg
```

once you've updated dpkg, the regular updates will once more be able to complete.


--------------

try this step, it makes me a little nervous that he wants you to delete the contents, but i saw a later post he made and he didnt have any problems

edit: try this at your own risk.... if someone knows about this feel free to mention if this is dangerous

---

### Post by granny4linux on 2007-08-16
> **loserboy said:**
> ```

$sudo gedit /var/lib/dpkg/status
```

Press Ctrl +A to select everything, then press delete to delete the contents of the file. Save (Ctrl +s) and close (Ctrl +w).

Back at the CLI

```
$sudo rm -f /var/lib/dpkg/lock
```

Now you should be able to run update manager, synaptic, aptitude or apt-get.


```
$sudo apt-get install dpkg
```

once you've updated dpkg, the regular updates will once more be able to complete.


--------------

try this step, it makes me a little nervous that he wants you to delete the contents, but i saw a later post he made and he didnt have any problems

edit: try this at your own risk.... if someone knows about this feel free to mention if this is dangerous

Thanks loserboy; I followed your instructions and still get the same error. Maybe someone else may have an idea.

---

### Post by loserboy on 2007-08-16
sorry bud.... I looked all over that was the closest thing i found.... good luck

---

### Post by loserboy on 2007-08-16
one last thing,  so far i've seen 3 posts with similar issues and they all have automatix installed, I bet if you talk to Arnie at the AX forums he'll get you fixed up... he's usually quick to reply as well

[www.getautomatix.com](www.getautomatix.com)

---

### Post by granny4linux on 2007-08-16
I'll try that. Thanks so much for your help.

---

### Post by granny4linux on 2007-08-17
I resolved the problem. In case anyone should have this problem in the future, here's what I did.

After further searching the terms "Problem with MergeList /var/lib/dpkg/status"
I found this post:

[http://ubuntuforums.org/showthread.php?t=357256&highlight=Problem+with+MergeList+%2Fvar%2Flib%2Fdpkg%2Fstatus]("http://ubuntuforums.org/showthread.php?t=357256&highlight=Problem+with+MergeList+%2Fvar%2Flib%2Fdpkg%2Fstatus")

Followed this solution:
cd /var/lib/dpkg
mv status status-bad
cp status-old status
apt-get update

Apt update ran fine but when I went to do the upgrade I got another error message referring to a problem with
  /var/lib/dpkg/available (sorry I did not output the exact message and don't know where to go to find it)

I replaced  /var/lib/dpkg/available with it's backup and  "sudo apt-get upgrade"
executed normally.

I don't know what I would do without these forums because going back to Windows has never been an option. Thanks to all the wonderful people who are willing to give their time to help others and report on solutions to problems.

---

