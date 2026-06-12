---
title: "Compiling problems, photoprint, freebasic and others"
date: 2006-10-28
forum: General Help
---

### Post by nomeat on 2006-10-28
I can't compile photoprint, freebasic or anything else interesting.

The problem seems to start with libg6 (apparantly I have the newest version running) but the applications seem to need an older version and I have read in this forum not to muck around with it (force install older versions, etc).
I use the dapper repos mentioned in this forum and Xubuntu.

Build essential would seem to be the easy solution but I get this:


```

computer@computer-desktop:/$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
computer@computer-desktop:/$ 
```


Some similar situations related to libc6 mentioned in this forum didn't help.
Does using Ubuntu mean I am forced to use only applications that are on the repos.

Please help.

---

### Post by elettronicha on 2006-10-28
Please, post your /etc/apt/sources.list file.

---

### Post by nomeat on 2006-10-28
Thanks for responding elettronicha

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

deb http://archive.canonical.com/ubuntu dapper-commercial main 

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

```

---

### Post by galileon on 2006-10-28
try sudo apt-get -f install

then sudo apt-get install build-essential

---

### Post by nomeat on 2006-10-29
Thanks galileon

all I get is:

0 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.

and with build essential the same story as above.

---

### Post by taurus on 2006-10-29
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by galileon on 2006-10-29
try this then:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential

---

### Post by nomeat on 2006-10-29
> **galileon said:**
> try this then:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential

...two hours later
still the same error with build-essential :confused:

---

### Post by nomeat on 2006-11-01
Still can't figure this one out.

On my laptop it works OK.
Is there anything I can take from there to make it work on my main computer?

With Linux I never understand where all the files are installed.

---

### Post by galileon on 2006-11-01
i spoze u could try to install the separate components of build-essential (which is only a meta package, ie a list of packages to install)

try installing gcc and make for instance....

---

### Post by nomeat on 2006-11-01
Hi galileon :)

yes I tried single components before with no success.
i.e.
```
computer@computer-desktop:/$ sudo apt-get install g++
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
computer@computer-desktop:/$


```

This one is interesting because lock in that position is a zero byte file.

I get the same error as above if I try to install or remove lock.

---

### Post by nomeat on 2006-11-01
That problem with lock was because I had synaptic open.

gcc and make returns that I have already newest version.

other components like g++ won't install for the same reason as when I try to install build-essential.

---

### Post by galileon on 2006-11-01
hi, ive just done man apt-get, there's another switch you could try, the -m which means ignore missing...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -m build-essential



if it all works on your laptop, you could try to copy everything in /var/cache/apt/archives on a cdrom, and mount in on the desktop, then issue:

dpkg -i *.deb 

inside the cdrom (usually /media/cdrom)

---

### Post by nomeat on 2006-11-01
Thanks galileon for the location of the archives and the new switch.

However I found this that seemed to safely downgrade lib6:

```
sudo aptitude update && sudo aptitude install g++
```

This swapped numerous libraries and added new things but my system still seems OK and it replaced one application called QUCS (a spice simulator) that could have automatically installed the wrong lib6 when I upgraded QUCS manually to a newer version a few months ago.

After this 'downgrade' I could install build-essential at last :)

Now there are other compiling problems but the error output looks is a bit more hopeful.

---

