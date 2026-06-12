---
title: "Cannot install all available updates"
date: 2006-12-10
forum: General Help
---

### Post by Quicky on 2006-12-10
I've been having a problem when running updates using the Update Manager whereby a popup appears telling me that it “Cannot install all available updates” and that I should try the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update my system completely.

Obviously I've tried the Synaptic and dist-upgrade suggestions, but my system still refuses to update completely, with the popup appearing whenever I run Update Manager.

The update that is skipped is Kino – no other prograns are listed.

Does anybody know why this is happening, and more importantly, how I can fix it?

Thanks

---

### Post by PriceChild on 2006-12-10
Please open up a terminal, and copy this in:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```Enter your password when needed.

Then paste the output back in here.

I'm guessing you haven't got enough entries on your sources list and are running into dep problems, but we'll see.

---

### Post by Quicky on 2006-12-10
Here you go:

```
quicky@quicky-laptop:~$ sudo apt-get update
Password:
Get: 1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get: 2 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get: 3 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Get: 4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Fetched 4B in 1s (3B/s)
Reading package lists... Done
quicky@quicky-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  kino
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
quicky@quicky-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  kino
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by PriceChild on 2006-12-10
Hmm.. I "think" you're missing an "update" repository or two...

Could you post
```
cat /etc/apt/sources.list
```Please for me to double check.

---

### Post by Quicky on 2006-12-10
No worries, see below:

```
quicky@quicky-laptop:~$ cat /etc/apt/sources.list
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


#created by arniedappersecond

```

---

### Post by PriceChild on 2006-12-10
Hmm.. I'm thinking this probably isn't the cause of your problems because the lack of error message earlier...

Might as well try anyway.

```
gksudo gedit /etc/apt/sources.list
```and replace everything with ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```Then save close, and try to update, upgrade and dist-upgrade again.

---

### Post by Quicky on 2006-12-10
Just tried that, and had the same output as earlier, with Kino not being upgraded. Any other suggestions?

---

### Post by PriceChild on 2006-12-10
Yeah thought It'd be the same...

Try
```
sudo apt-get -f install
```

Hmm.

Is there anyone else running Dapper here able to shed light on this issue?

---

### Post by Quicky on 2006-12-10
Nope, that didn't work either. Could it be a particular issue with Kino, rather than a repository problem?

---

### Post by lamego on 2006-12-10
```
sudo apt-get remove kino
sudo apt-get install kino
```

---

### Post by themusicwave on 2007-01-29
I also have the exact same problem with kino.  No idea how to fix it though.

---

