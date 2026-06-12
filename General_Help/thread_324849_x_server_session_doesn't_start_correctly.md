---
title: "x server session doesn't start correctly"
date: 2006-12-24
forum: General Help
---

### Post by insert_name_here on 2006-12-24
My system, Lenovo T60, intel Core Duo, 1gb RAM, 100gb HDD, Edgy Eft, Beryl/XGL, was working fine until I tried to install Automatix2.  

Automatix installed incorrectly and said I should run apt-get install -f to put in all the correct dependencies.  However, when I tried to start the terminal, an error message came up saying that "gnome-terminal"  could not be found.

I restarted, and I got to login, but I got an error message every time saying that my X sessoin had lasted less than 10 seconds and linked to my ~/.xsession-errors file: 
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "merrillj"
/etc/gdm/Xsession: Beginning session setup...
[: 12: closing paren expected
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/merrillj-laptop:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
exec: 3: gnome-session: not found

Is this saying that the gnome executable itself cannot be found?  If so (or if not) how should I fix this?

---

### Post by taurus on 2006-12-24
Boot into recovery mode from GRUB menu and at the prompt, run

```
apt-get install -f
apt-get update
apt-get upgrade
shutdown -r now
```

---

### Post by insert_name_here on 2006-12-24
'Fraid that didn't work.

I had already removed Automatix2 (sudo apt-get remove automatix2) and since AFAIK it isn't in a repository but just installed from a package, I don't know how to reinstall it from the command line, if that would even help.

---

### Post by taurus on 2006-12-24
Let's have a look at your /etc/apt/sources.list first before you install anything else then!!!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by insert_name_here on 2006-12-24
Here it is.  I'm pretty sure I formatted it correctly, as it came out (with the ext2 driver for WinXP from driver-fs.org) as 2 long lines.
> 

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main 
#Added by software-properties


## Uncomment the following two lines to add software from the 'universe'
## repository.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe restricted main

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe restricted main 
#Added by software-properties
# 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe


## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.
# 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main 
#Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main


---

### Post by taurus on 2006-12-24
You are running Edgy but how come you have dapper repos in /etc/apt/sources.list!  You cannot fix both Dapper and Edgy in your repos because bad things can happen and will happen (sooner rather than later).  Therefore, edit /etc/apt/sources.list and replace those "dapper" with "edgy" then...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by insert_name_here on 2006-12-24
I did all that, although I had to use vi instead of gedit, because the command line said that gedit could not be found (!).

It seems like all the gnome-related programs are gone...

---

### Post by taurus on 2006-12-24
After replacing all the **dapper** with **edgy** in /etc/apt/sources.list, run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by insert_name_here on 2006-12-24
That worked, thanks for the help!

---

