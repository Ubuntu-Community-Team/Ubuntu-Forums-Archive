---
title: "Problem installing and removing files"
date: 2017-08-15
forum: General Help
---

### Post by jsfcabrilloinbox on 2017-08-15
hello,
I am just returning to Ubuntu after a long time not using.
I had problems installing any new programs yesterday. They were showing a loading bar but they never fully installed. I found a solution on line but today I am getting a new error message: Detailed errors from the package manager follow:
```
Apt transaction returned result exit-failed


```
so just now I tried this command:
```
sudo apt-get update && sudo apt-get install --only-upgrade gnome-software

```
This is the result I got:

```
-PC:~$ sudo apt-get update && sudo apt-get install --only-upgrade gnome-software
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:4 [http://ppa.launchpad.net/tails-team/tails-installer/ubuntu](http://ppa.launchpad.net/tails-team/tails-installer/ubuntu) xenial InRelease
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:5 [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease [166 kB]
Ign:5 [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease       
Fetched 370 kB in 1s (302 kB/s)
Reading package lists... Done
W: GPG error: [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553  NO_PUBKEY 7638D0442B90D010
W: The repository 'http://http.debian.net/debian jessie-backports InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-software is already the newest version (3.20.5-0ubuntu0.16.04.5).
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libidl-2-0 liborbit2 libxmlbird1
  python-gconf python-gnome2 python-pyorbit unicode-data
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,520 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package gnome-software-common (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of gnome-software:
 gnome-software depends on gnome-software-common (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software-common is not configured yet.

dpkg: error processing package gnome-software (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-software:
 ubuntu-software depends on gnome-software (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software is not configured yet.

dpkg: error processing package ubuntu-software (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 gnome-software-common
 gnome-software
 ubuntu-software
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2017-08-15
jsfcabrilloinbox;  Hello;

Best we can say " Don't - just don't "
> 
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial
W: The repository 'http://http.debian.net/debian jessie-backports


See: - all bets are off
[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian)
The reverse is also true. 

Not good
[INDENT][INDENT]just the way it is,[/INDENT][/INDENT]

---

### Post by jsfcabrilloinbox on 2017-08-15
what do you mean by "don't", you mean there isn't anything at all I should do?

---

### Post by vocx on 2017-08-15
> **jsfcabrilloinbox said:**
> what do you mean by "don't", you mean there isn't anything at all I should do?
He is implying something, but he is not spelling it clearly.

Basically, your "sources.list" file has a repository belonging to Debian Jessie.
```

[http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease

```

Although Ubuntu is derived from Debian, Ubuntu has its own repositories, as you can see in the "/etc/apt/sources.list" file. Adding a Debian repository, like you do, is not recommended. Although one package may be able to be installed directly from the Debian repositories, this is not recommended because you may be introducing strange errors with the dependencies of other packages.

You should remove those lines from your "sources.list", belonging to Debian. There should be a way to get the software that you want for Ubuntu. Many programs keep special personal package archives (PPA) for Ubuntu in order to get the newest versions of a given program, which seems your intention with that Debian repository.

---

### Post by Bashing-om on 2017-08-15
jsfcabrilloinbox;

Well. well ..

With the addition of debian jessie-backports repository you have introduced unknown variables into ubuntu.
May be well above my skill level to untangle the resulting dependencies .

I am willing to give it my all, see what we can do .

1st up is to remove those foreign sources .
Show what we have presently:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
once the sources files are pristine, then run the package manager and see what condition the condition is in.
And then do what ?

[INDENT][INDENT]could be a long hard road .
[/INDENT][/INDENT]

---

### Post by jsfcabrilloinbox on 2017-08-15
ok this is what i got so far:

computer-PC:~$ [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InReleasehttp://cdn-fastly.deb.debian.org/debian jessie-backports InRelease
bash: [http://cdn-fastly.deb.debian.org/debian:](http://cdn-fastly.deb.debian.org/debian:) No such file or directory

computer-PC:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     6    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    11    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    17    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    18    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    19    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    27    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    28    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    29    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    37    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    38    
    39    ## Uncomment the following two lines to add software from Canonical's
    40    ## 'partner' repository.
    41    ## This software is not part of Ubuntu, but is offered by Canonical and the
    42    ## respective vendors as a service to Ubuntu users.
    43    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    44    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    45    
    46    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    47    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    48    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    49    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    50    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    51    deb [http://http.debian.net/debian/](http://http.debian.net/debian/) jessie-backports main
    52    # deb-src [http://http.debian.net/debian/](http://http.debian.net/debian/) jessie-backports main
    53    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
computer-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/tails-team-ubuntu-tails-installer-xenial.list <==
deb [http://ppa.launchpad.net/tails-team/tails-installer/ubuntu](http://ppa.launchpad.net/tails-team/tails-installer/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/tails-team/tails-installer/ubuntu](http://ppa.launchpad.net/tails-team/tails-installer/ubuntu) xenial main

---

### Post by Bashing-om on 2017-08-15
@vocx; Thanks for taking the time to clarify my muddy waters :)

jsfcabrilloinboxl l Hey;

Not as bad as I had anticipated, one line .
line 51
> 
51 deb [http://http.debian.net/debian/](http://http.debian.net/debian/) jessie-backports main

comment it out.

Now what results:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```
please post these outputs between code tags to maintain the formatting and promote readability :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see what we got to do next.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by jsfcabrilloinbox on 2017-08-15
so what exactly should i do to that one line?

---

### Post by jsfcabrilloinbox on 2017-08-15
also thanks for both your help

---

### Post by jsfcabrilloinbox on 2017-08-15
I think you might have wanted me to try those few lines you just posted:

computer-PC:~$ sudo apt update
[sudo] password for computer

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:3 [http://ppa.launchpad.net/tails-team/tails-installer/ubuntu](http://ppa.launchpad.net/tails-team/tails-installer/ubuntu) xenial InRelease
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:5 [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease [166 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Err:5 [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease       
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553  NO_PUBKEY 7638D0442B90D010
Reading package lists... Done
W: GPG error: [http://cdn-fastly.deb.debian.org/debian](http://cdn-fastly.deb.debian.org/debian) jessie-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553  NO_PUBKEY 7638D0442B90D010
E: The repository 'http://http.debian.net/debian jessie-backports InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

computer-PC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libidl-2-0 liborbit2 libxmlbird1
  python-gconf python-gnome2 python-pyorbit unicode-data
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,520 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y 
dpkg: error processing package gnome-software-common (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of gnome-software:
 gnome-software depends on gnome-software-common (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software-common is not configured yet.

dpkg: error processing package gnome-software (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-software:
 ubuntu-software depends on gnome-software (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software is not configured yet.

dpkg: error processing package ubuntu-software (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 gnome-software-common
 gnome-software
 ubuntu-software
E: Sub-process /usr/bin/dpkg returned an error code (1)


computer-PC:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libidl-2-0 liborbit2 libxmlbird1
  python-gconf python-gnome2 python-pyorbit unicode-data
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,520 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package gnome-software-common (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of gnome-software:
 gnome-software depends on gnome-software-common (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software-common is not configured yet.

dpkg: error processing package gnome-software (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of ubuntu-software:
 ubuntu-software depends on gnome-software (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software is not configured yet.

dpkg: error processing package ubuntu-software (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 gnome-software-common
 gnome-software
 ubuntu-software
E: Sub-process /usr/bin/dpkg returned an error code (1)

computer-PC:~$ sudo dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 gnome-software-common Software Center for GNOME (common files)

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 gnome-software       Software Center for GNOME
 ubuntu-software      Utility for browsing, installing, and removing software

---

### Post by jsfcabrilloinbox on 2017-08-15
I also have the iso file on another computer that I used for this install if that helps

---

### Post by vocx on 2017-08-15
> **jsfcabrilloinbox said:**
> so what exactly should i do to that one line?
He, he, you have much to learn.

> **Bashing-om said:**
> 
Not as bad as I had anticipated, one line .
line 51

comment it out.


Commenting out means to make a line a comment, so it is ignored by the system.

Do you know how to open text files? Well, you need to open "/etc/apt/sources.list".

Then you need to find the offending line, and then you need to delete it, or add a pound sign before the line. This is commenting it out. Then that line will be ignored.
```

sudo nano /etc/apt/sources.list

```
Exit and save the file by the keyboard combination "Cntrl X", and the "yes".

Change
```

deb [http://http.debian.net/debian/](http://http.debian.net/debian/) jessie-backports main

```
into
```

#deb [http://http.debian.net/debian/](http://http.debian.net/debian/) jessie-backports main

```
Or just delete it.

> **jsfcabrilloinbox said:**
> I think you might have wanted me to try those few lines you just posted:


Then you may run the commands that you ran.

I have a question. Who installed the system for you? Or why do you have that Debian repository in your Ubuntu system? Who told you to add it? What program did you want to download and upgrade from those backports? What guide were you following? Your system is throwing warnings about "gnome-software" so that's a bit worrying. Maybe it downloaded a lot of Gnome packages that may not be easy to restore to their Ubuntu versions.

---

### Post by Bashing-om on 2017-08-15
jsfcabrilloinbox; Yukkie;

I had assumed ( yeah yeah ) that you were familiar with the term " comment out"
> 
comment it out.


If you do not have a backup of the sources.list file make one at this time . Never can tell what might happen .
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-15aug2017

```

and now in your favorite text editor open /etc/apt/sources.list
and add a # character to the start of line 51.
here is gedit for the editor:
```

sudo -H gedit /etc/apt/sources.list

```
make the edit and save the file.

now  show what our work here produced:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

see now what we need to address and fix .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jsfcabrilloinbox on 2017-08-16
I did not know what comment it out meant before today.
I installed this system and I'm not sure what I did to get to this spot.
working on your fixes now

---

### Post by jsfcabrilloinbox on 2017-08-16
I dont think anything changed. not sure if i commented out the correct line, there weren't even 51 lines in the text editor 

computer-PC:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list-15aug2017
[sudo] password for 
computer-PC:~$ sudo -H gedit /etc/apt/sources.list

(gedit:2697): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:2697): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:2697): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:2697): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
joel@joel-Presario-CQ62-Notebook-PC:~$ sudo apt update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:4 [http://ppa.launchpad.net/tails-team/tails-installer/ubuntu](http://ppa.launchpad.net/tails-team/tails-installer/ubuntu) xenial InRelease
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [60.1 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [211 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [52.1 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [171 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [226 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5,132 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [48.7 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [64.2 kB]
Fetched 1,458 kB in 2s (660 kB/s)                                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

computer-PC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libidl-2-0 liborbit2 libxmlbird1
  python-gconf python-gnome2 python-pyorbit unicode-data
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,520 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Abort.

computer-PC:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto fonts-roboto-hinted libidl-2-0 liborbit2 libxmlbird1
  python-gconf python-gnome2 python-pyorbit unicode-data
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,520 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package gnome-software-common (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of gnome-software:
 gnome-software depends on gnome-software-common (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software-common is not configured yet.

dpkg: error processing package gnome-software (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-software:
 ubuntu-software depends on gnome-software (= 3.20.5-0ubuntu0.16.04.5); however:
  Package gnome-software is not configured yet.

dpkg: error processing package ubuntu-software (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 gnome-software-common
 gnome-software
 ubuntu-software
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2017-08-16
jsfcabrilloinbox; Hey ...

Looking promising .
We know:
> 
3 not fully installed or removed.

we have a bit of work ahead of us once we do get the package manager's requirements satisfied.

Let's take a gentle poke at it - taking the package manager's advise:
Run terminal command:
```

sudo apt install --reinstall gnome-software-common

```
Depending on what happens here is how we proceed .

[INDENT][INDENT]Let there be light-
[/INDENT][/INDENT]

---

