---
title: "error: Malformed line in source list."
date: 2007-01-15
forum: General Help
---

### Post by sir_fragalot on 2007-01-15
Hello, I am a brand new user to Linux (always wanted to try Linux and windows was causing problems, so I switched and I am loving it), anywho I just installed Ubuntu Edgy (well a dapper upgrade but same difference) yesterday and well I got my first error :)  Ok so anyway I get this error 

Error: Opening the cache(E: Malformed Line4 in source list /etc/apt/sources.list.d./edgy-multiverse.list(dist parse), E: The sources could not be read.

Also when I open synaptic
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

So basically I can't update or do anything like that stuff. Here are my sources using getedit /etc/apt/sources.list

```


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe main restricted multiverse #Added by software-properties
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse #Added by software-properties
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
# wxPython APT repository at wxcommunity.com
# deb http://wxpython.wxcommunity.com/apt/ubuntu/dapper /
deb-src http://wxpython.wxcommunity.com/apt/ubuntu/dapper /
# deb http://wine.budgetdedicated.com/apt dapper main

    # wxPython repository on Starship
# deb http://starship.python.net/crew/robind/wxPython/apt/ binary/
# deb-src http://starship.python.net/crew/robind/wxPython/apt/ source/

```

And my source list in the edgy multiverse list in where it said to go in my first error. 
```
# automatically added by gnome-app-install on 2007-01-15 15:26:13.546537
deb http://security.ubuntu.com/ubuntu edgy-security
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates

```

Thats about it, I am running Edgy like I said. 

Thanks for your time and paitence to help a newbie to Linux out.

---

