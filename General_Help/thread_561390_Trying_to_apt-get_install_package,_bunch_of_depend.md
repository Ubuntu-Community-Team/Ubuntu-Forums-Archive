---
title: "Trying to apt-get install package, bunch of dependency errors!#@%"
date: 2007-09-27
forum: General Help
---

### Post by herbster on 2007-09-27
I am trying to build the program nitrogen, and it gives me an error at ./configure that I need libgtk2.0-dev, so I am getting the following, which is me getting the error at the beginning and then trying to install the dependencies myself, of course I'm surely doing it wrong but nevertheless:

```
bobby:~/Desktop/nitrogen-1.0$ sudo apt-get install libgtk2.0-dev
Password:
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages
bobby:~/Desktop/nitrogen-1.0$ sudo apt-get install libpango1.0-dev libcairo2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.10-1turner3~feisty0.1 is to be installed
E: Broken packages
bobby:~/Desktop/nitrogen-1.0$ sudo apt-get install libpango1.0-dev libcairo2-dev libcairo2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcairo2 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.10-1turner3~feisty0.1 is to be installed
E: Broken packages
bobby:~/Desktop/nitrogen-1.0$ sudo apt-get install libcairo2Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcairo2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bobby:~/Desktop/nitrogen-1.0$
```

---

### Post by por100pre1 on 2007-09-27
Have you added some extra repositories to /etc/apt/sources.list ? 

```
cat /etc/apt/sources.list
```

post the results...

If you have added extra repositories, try disabling them for a while, then

```
sudo aptitude update
```

and then try installing again. :-k

---

### Post by herbster on 2007-09-27
> **por100pre1 said:**
> Have you added some extra repositories to /etc/apt/sources.list ? 

```
cat /etc/apt/sources.list
```

post the results...

If you have added extra repositories, try disabling them for a while, then

```
sudo aptitude update
```

and then try installing again. :-k

I had a few extra repos, went into Synaptic and unchecked them, did apt-get update, then tried again and same error :(

---

### Post by rsambuca on 2007-09-27
Post your sources.list

There is obviously something wrong in there.  Also, are you using Edgy as your profile says, or are you using Feisty?

---

### Post by herbster on 2007-09-27
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
## Claws-Mail
# deb http://www.claws-mail.org/ubuntu/feisty/ ./
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
# Font rendering fix
# deb http://www.telemail.fi/mlind/ubuntu feisty fonts
# deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts
```

And I am using Feisty, haven't updated my profile (whoops) :)

---

### Post by rsambuca on 2007-09-27
I think you are missing a couple of deb-src lines from your sources.

Try adding these and see if it works:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

---

### Post by herbster on 2007-09-27
I added those, apt-get update'd and still getting errors. Perhaps sense can be made of this:

```
bobby:~$ sudo apt-get install libcairo2-dev
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.10-1turner3~feisty0.1 is to be installed
E: Broken packages
bobby:~$ sudo apt-get install libcairo2-dev
```

---

### Post by rsambuca on 2007-09-27
> **herbster said:**
> I added those, apt-get update'd and still getting errors. Perhaps sense can be made of this:

```
bobby:~$ sudo apt-get install libcairo2-dev
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.10-1turner3~feisty0.1 is to be installed
E: Broken packages
bobby:~$ sudo apt-get install libcairo2-dev
```
Maybe check launchpad for reported bugs.

---

### Post by por100pre1 on 2007-09-27
It seems that the package form the official repository will likely break a package from the Feisty font fix you seem to have installed. Try downloading the package from [here]("http://packages.ubuntu.com/feisty/libdevel/libcairo2-dev"), then try to install it.

You can also try this:

```
sudo apt-get install -f
```

```
sudo aptitude install libcairo2-dev
```

---

### Post by herbster on 2007-09-27
> **por100pre1 said:**
> It seems that the package form the official repository will likely break a package from the Feisty font fix you seem to have installed. Try downloading the package from [here]("http://packages.ubuntu.com/feisty/libdevel/libcairo2-dev"), then try to install it.

You can also try this:

```
sudo apt-get install -f
```

```
sudo aptitude install libcairo2-dev
```

I actually didn't install the font fix, this is a reinstall as of about a week or more ago, I just copied over my sources.list from backup.

I have downloaded the libcairo2-dev, should I double-click on the deb and install it still?

EDIT: I just opened the .deb and it says "Error: dependency is not satisfiable: libcairo2"

---

### Post by herbster on 2007-09-27
Fixed, had to do this:

```
sudo apt-get install libcairo2=1.4.2-0ubuntu1
```

to downgrade, then apt-get update and finally had to install a few other packages that came up for request during the ./configure, and now my program works! :)

Thanks for pointing out launchpad.net rsambuca, much appreciated! :)

---

### Post by zadig on 2007-12-06
I have the same problem, did you get to solve this ?

---

### Post by mikeyfbi on 2008-04-11
I am also getting the same error.

I'm trying to install a .deb but it keeps saying "Dependency not satisfiable:libcairo2"

Synamptic Says I have it...i tried 

"sudo apt-get install libcairo2=1.4.2-0ubuntu1"

 and it says 

E: Version '1.4.2-0ubuntu1' for 'libcairo2' was not found

I also tried just "sudo apt-get install libcairo2" and it says I have the newest version.

Also tried reinstalling it...no dice.  

Any ideas?


mike

ps.
[http://packages.ubuntu.com/gutsy/libs/libcairo2](http://packages.ubuntu.com/gutsy/libs/libcairo2) 

is not fount for me ATM

---

