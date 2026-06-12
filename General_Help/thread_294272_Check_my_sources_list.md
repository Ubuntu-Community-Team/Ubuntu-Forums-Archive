---
title: "Check my sources list?"
date: 2006-11-06
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-06
Would some one please check this sources list & see if I am missing some thing? Thank you                                deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by taurus on 2006-11-06
Looks good to me.  If you want to me mine (/etc/apt/sources.list, that is ;) ), just say so...

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
That would be GREAT! Good morning taurus. Lot's of sunshine here today. Any ways I was up till 5:30 AM fixing (tweaking) Couple of issues: I hadn't used Firefox in quite a while as I used Iceweasel. I didn't realize how slow Firefox was compared to Iceweasel. I got Iceweasel back but I do not recall how I got flash 9 to work as Iceweasel calls for gnash and I never got that one. Also before I "Boinked" my system the newer kernels 2.19 etc were in synaptic. This time around they are not. Other than that my overhall went ok Got Frostwire javas and flash worked for Firefox but not Iceweasel

---

### Post by taurus on 2006-11-06
So, I bet all those crazy fools left tons of trash on the streets from yesterday, eh!!!  

Here is my /etc/apt/sources.list that I use on my machine in the office...

```

# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

# Deluge bittorrent client...
#deb http://espergreen.com/apt edgy main

# Automatix...
# wget http://www.getautomatix.com/apt/key.gpg.asc
# gpg --import key.gpg.asc
# gpg --export --armor 521A9C7C | sudo apt-key add -
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START
deb http://dl.google.com/linux/deb/ stable non-free
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

```
Enjoy.

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
kept telling me I needed public key and what ever I did now when I do : sudo gedit /etc/apt/sources.list> nothing comes up but my name$ so I did sudo nano gedit /etc/apt/sources.list and that was empty. Please I do not want to** Boink** this fresh install!

---

### Post by Ramses de Norre on 2006-11-06
You'll want ```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
```
in your first one, the src one doesn't give you binary packages.
You might also want to add universe and multiverse to every repo.

---

### Post by taurus on 2006-11-06
> **MustangSallydd said:**
> kept telling me I needed public key and what ever I did now when I do : sudo gedit /etc/apt/sources.list> nothing comes up but my name$ so I did sudo nano gedit /etc/apt/sources.list and that was empty. Please I do not want to** Boink** this fresh install!
I have included the "public key" for automatix2...  At the prompt, enter

```

gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

```
Otherwise, you can remove everything starting from

```

# Deluge bittorrent client...
#deb http://espergreen.com/apt edgy main

# Automatix...
# wget http://www.getautomatix.com/apt/key.gpg.asc
# gpg --import key.gpg.asc
# gpg --export --armor 521A9C7C | sudo apt-key add -
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START
deb http://dl.google.com/linux/deb/ stable non-free
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

```

You can use either gedit or nano to edit your /etc/apt/sources.list but you cannot use both in the same line...  In other words, either one of these would work.

```
gksudo gedit /etc/apt/sources.list
-or-
sudo nano -Bw /etc/apt/souces.list
-but not-
sudo nano gedit /etc/apt/sources.list  <--  a big NO NO...
```

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
I can not get sources list to come up: $ gksudo gedit /etc/apt/sources.list

(gedit:9966): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Ramses de Norre on 2006-11-06
I always get that message but normally gedit should start shortly after it.

---

### Post by NeoLithium on 2006-11-06
```
sudo gedit /etc/apt/sources.list
```

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
nothing has come up, no source list. I just get that warning and a flashing curser and it has been over 5 minutes

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
ok I did the nano thingy and the window popped up blank so I pasted a sources list in there but how do you save? Is it Ctr+o or Ctrl+x remember this is in the GNU nano  File: gedit

---

### Post by taurus on 2006-11-06
If your /etc/apt/sources.list is empty, just paste mine in except skip everything after the # deluge...  And if you use nano, then that would be <Ctrl>x to exit and it will ask you if you want to exit and what name you want to save it as.  Just answer y and enter to save it as sources.list.  Now, if you look at it, you should see your list.

```
more /etc/apt/sources.list
```
If everything is fine, then just update it.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by IusedTObeSOMEONEelse on 2006-11-06
ok, I think I have it all together! whew! an observation though: when I do >sudo gedit /etc/apt/sources.list;  nothing comes up when I do the nano thing then some thing pops up. should I not worry.I do not like editing sources through nano rather do sudo gedit. Thank you for averting another one of my disasters ;)

---

### Post by taurus on 2006-11-06
If you want to use gedit, I recommand you use it with gksudo instead of sudo...

```
gksudo gedit <filename>
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

