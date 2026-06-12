---
title: "Download problem from repository - bad header line, goes on for few days now"
date: 2006-12-12
forum: General Help
---

### Post by matjaz_pirnovar on 2006-12-12
When I try to download Eclipse IDE from Repositiries downloading stopns towards the end and I get this message:

"Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?"

And these details:
W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/poo...buntu1_all.deb](http://ubuntu.cs.utah.edu/ubuntu/poo...buntu1_all.deb)
Bad header line


W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/poo...buntu1_all.deb](http://ubuntu.cs.utah.edu/ubuntu/poo...buntu1_all.deb)
Bad header line


W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/poo...buntu6_all.deb](http://ubuntu.cs.utah.edu/ubuntu/poo...buntu6_all.deb)
Bad header line

HELP!

Matjaz

---

### Post by hod139 on 2006-12-12
Eclipse is available in the multiverse repository.  For installing the repository version of eclipse and repository version of java see this [howto:]("http://ubuntuforums.org/showthread.php?t=201378")
What does your /etc/apt/sources.list look like, my guess is you have unofficial repositories and they are down.

---

### Post by matjaz_pirnovar on 2006-12-12
Hi,

Below is my sources list. Should I try another soucer list? Everything else usually works and is downloadable or if not it is ok after few days, but Eclipse is stuck :(
Thanks for advice.


deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-updates main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-security main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-backports main universe multiverse restricted
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-backports main restricted universe multiverse

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://debian.isisetup.ch/](http://debian.isisetup.ch/) unstable/

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

Matjaz

---

### Post by hod139 on 2006-12-12
> **matjaz_pirnovar said:**
> Hi,

Below is my sources list. Should I try another soucer list? Everything else usually works and is downloadable or if not it is ok after few days, but Eclipse is stuck :(
Thanks for advice.


deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-updates main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-security main restricted universe multiverse

deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-backports main universe multiverse restricted
deb-src [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) dapper-backports main restricted universe multiverse

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://debian.isisetup.ch/](http://debian.isisetup.ch/) unstable/

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

Matjaz

Strange sources.list.  Try replacing all your utah lines with:
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```

Also, why do you have these repos?
deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://debian.isisetup.ch/](http://debian.isisetup.ch/) unstable/

Only use these repos if you really need something from them, I'm not sure why you have them.  Having too many non-standard repos is a good way to mess up your system.

---

### Post by matjaz_pirnovar on 2006-12-13
Hey,

Thanks a lot for those comments. I have used your sources list and it sudo apt-get update worked nicely some files I wasn't able to update were now updated.
But when trying to instal Eclipse, same problem occured:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/ant/ant_1.6.5-3ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/ant/ant_1.6.5-3ubuntu1_all.deb)
  Bad header line [IP: 195.248.90.38 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/ant/ant-optional_1.6.5-3ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/ant/ant-optional_1.6.5-3ubuntu1_all.deb)
  Bad header line [IP: 195.248.90.38 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse-jdt-common_3.1.2-1ubuntu6_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/eclipse-jdt-common_3.1.2-1ubuntu6_all.deb)
  Bad header line [IP: 195.248.90.38 80]

Pffffff....will try more...

Matjaz

---

### Post by matjaz_pirnovar on 2006-12-13
After new sources list I got notice to update some header lines, so I did. But Eclipse still doesn't want to install. Same as above posting  :(

Not sure what to do. Have downloaded Eclipse from the web plus neccessary additions (Java JRE) but something is blocking there a bit as well, so I'm stuck...

Suggestions welcome. Why some repos information wouldn't fetch??? Hm.

Thanks.
M

---

### Post by az on 2006-12-13
sudo apt-get update?

---

### Post by matjaz_pirnovar on 2006-12-14
> **azz said:**
> sudo apt-get update?

hi 

Yes. When executing "sudo apt-get update" in terminal I got some unfetched files on the list. With the new sources.list these were more or less solved.

Basically, I'd just like to download Eclipse.

Why do I get that note about 3 files that couldn't be fetched during downloading the Eclipse??

"W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb)
Bad header line [IP: 195.248.90.38 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb)
Bad header line [IP: 195.248.90.38 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu6_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu6_all.deb)
Bad header line [IP: 195.248.90.38 80]"

If sources.list sin't a problem any more, what could it be??

???

Thanks

---

