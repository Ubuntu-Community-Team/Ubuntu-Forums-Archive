---
title: "https://ubuntuforums.org/"
date: 2020-04-26
forum: General Help
---

### Post by pegasusp on 2020-04-26
[COLOR=#000000][COLOR=#000000]

Error message appears when attempting to install new programs and[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]sudo apt-get update[/COLOR][/COLOR]

[COLOR=#000000]E: Malformed entry 29 in list file /etc/apt/sources.list (Component)[/COLOR]
[COLOR=#000000][COLOR=#000000]E: The list of sources could not be read.

I am tried to follow some instructions to immigrate MySQL to MariaDB but Now MySQL is broken though i am start MySQL it giving errors though. i gotta fix that one first

[/COLOR][/COLOR]```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multi$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe m$


###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted unive$
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted univer$
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted univ$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted u$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted un$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted $


###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

```

---

### Post by Bashing-om on 2020-04-26
pegasusp; Oh Boy ...

Are you aware:
> 
Ubuntu 12.04 LTS (Precise Pangolin) was the sixteenth release of Ubuntu. !End-of-life was April 28th 2017. 
               See [https://lists.ubuntu.com/archives/ubuntu-security-announce/2017-April/003833.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2017-April/003833.html) for more information

If this is not Ubuntu Advantage program by intent, then it is highly recommended to upgrade to a current release (20.04).

As to the error - the links should be as [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)

Note that lead "us".

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by pegasusp on 2020-04-26
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################




###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ precise main restricted universe multi$
deb-src http://us.archive.ubuntu.com/ precise main restricted universe m$




###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ precise-security main restricted unive$
deb http://us.archive.ubuntu.com/ precise-updates main restricted univer$
deb http://us.archive.ubuntu.com/ precise-backports main restricted univ$
deb-src http://us.archive.ubuntu.com/ precise-security main restricted u$
deb-src http://us.archive.ubuntu.com/ precise-updates main restricted un$
deb-src http://us.archive.ubuntu.com/ precise-backports main restricted $




###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

```
Did you mean this sir?

---

### Post by wildmanne39 on 2020-04-26
This version of Ubuntu is long dead, please install a supported version of Ubuntu, you can install 16.04, 1804 or 20.04 all have 5 years support from there release date but I would go with 18.04 myself because it has been out long enough to be very stable and still has a plenty of support years left.

---

### Post by Bashing-om on 2020-04-26
pegasusp; Well -

I stand corrected by self
as [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) does in fact complete.

Looking for line 29 in the sources list file, past back:
```

cat -n /etc/apt/sources.list

```

so I can identify that line.


But that does not rectify the fact that you are running an unsupported release !


[INDENT][INDENT]sometimes I do wander ......
[/INDENT][/INDENT]

---

### Post by pegasusp on 2020-04-26
Thank you problem been solved but now i just got another issue i'll make a new thread

---

### Post by wildmanne39 on 2020-04-26
Thread closed as 12.04 is long dead and user is moving to a supported version of Ubuntu.

---

