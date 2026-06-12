---
title: "Aborted upgrade...help me fix it? (long, confusing post)"
date: 2008-05-10
forum: General Help
---

### Post by Mutant Corn on 2008-05-10
Xubuntu Gutsy, Dell XPS m1210, Centrino Duo chipset

So I was installing my first virtual os (ubuntu studio) in virtualbox, and it pops up with a message about a new version or something is available...not the normal "it's time to update" thing. I think it had something to do with the Hardy disk in the drive. Anyway...for some reason i thought it was something associated with VB and gave it the go-ahead to update. I soon after realized that it was trying to upgrade my actul os, not the virtual one, to Hardy.

Panicking, I did a hard shutdown to stop it while it was on the "setting new software channels" screen. Stupid, I know, but I've wiped my system 3 times in the last week trying to get hardy to work with my intel wireless and I really didn't want to do it again.

I booted up again, and all appeared well. I was beginning the VBox install of ubuntu studio again when I get a message that there are updates available. 513 of them. Upon closer inspection I think it was trying to update them to the Hardy versions.

Basically...what have I done and how do I fix it?

---

### Post by ghost_ryder35 on 2008-05-10
you have begun the update process :) I do not know if this would work or not, but as long as it didnt write over any files you could revert your software source list back to gutsys
HERE IS GUTSY's list
```

deb http://nl.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
## Uncomment the following two lines to add software from the &#8216;backports&#8217;
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical&#8217;s
## &#8216;partner&#8217; repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
##################################################
##################################################
##ffmpeg of ubuntu is slower then molasses in January on the arctics
##Alternative resource for Multimedia support like ffmpeg
#is meant for Debian But works fine on my Gutsy Gibbon
##use at your own risk
##See: http://debian.video.free.fr/index.html
##get the apt GPG key from here : http://debian.video.free.fr/faq.html
deb ftp://ftp.uni-kl.de/debian-multimedia/ stable main
##############################################
##############################################

```
this is hypathetical as I do not know if/what the update process has over written (its worth a shot though right :))

---

### Post by Mutant Corn on 2008-05-10
Do I just put that into the terminal?

I'm a bit of a nooblet as far as linux goes...the terminal scares me:(

---

### Post by ghost_ryder35 on 2008-05-10
> **Mutant Corn said:**
> Do I just put that into the terminal?
 
I'm a bit of a nooblet as far as linux goes...the terminal scares me:(
save the file to your desktop, replace user with your username, and make sure you save the source list I posted above as sourcelist  Then just copy and paste the below command in the terminal
```

sudo cp /home/user/Desktop/sourcelist  /etc/apt/sources.list

```

---

### Post by Mutant Corn on 2008-05-10
```
john@john-laptop:~$ sudo cp /home/john/Desktop/sourcelist /etc/apt/sources.list
cp: cannot stat `/home/john/Desktop/sourcelist': No such file or directory
john@john-laptop:~$ sudo cp /home/user/Desktop/sourcelist /etc/apt/sources.list
cp: cannot stat `/home/user/Desktop/sourcelist': No such file or directory
john@john-laptop:~$ 
```

What did I do? :(

---

### Post by ghost_ryder35 on 2008-05-10
you didnt save it to your desktop with the name 'sourcelist'

---

### Post by ghost_ryder35 on 2008-05-10
```

sudo cp /home/john/Desktop/sourcelist.txt /etc/apt/sources.list

```
download this attachment, save it to desktop, and copy and paste the above command to terminal

---

### Post by Mutant Corn on 2008-05-10
...left off the .txt :neutral:

Well it went through with no errors, but what did it do?

```
john@john-laptop:~$ sudo cp /home/john/Desktop/sourcelist.txt /etc/apt/sources.list
john@john-laptop:~$ 

```

---

### Post by ghost_ryder35 on 2008-05-10
you replaced the sources.list file with the old gutsy file
do a
```

sudo apt-get update

```
see what it says about how many packages are available
p.s. i made two boo boo's.  I should of had you make a backup first :(  And I should of had you post the old sources.list :(

---

### Post by Mutant Corn on 2008-05-10
^ it's alright...if what you gave me was the standard gutsy list then it couldn't hurt could it?

update manager was already open so I just hit "check for updates"

it downloaded 47 packages, all from gutsy repositories, and then gave me this:

"W: GPG error: [ftp://ftp.uni-kl.de](ftp://ftp.uni-kl.de) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907"

Now it says there are 168 updates available. Is it possible that these are standard updates? The os is less than a day old..

---

### Post by ghost_ryder35 on 2008-05-10
well if you have not updated gutsy since you installed, there probally regular updates cause there were a lot of them.

---

### Post by Mutant Corn on 2008-05-10
I thought I did...but I guess not if all these are here. I'll update and see what happens.

---

### Post by ghost_ryder35 on 2008-05-10
> **Mutant Corn said:**
> I thought I did...but I guess not if all these are here. I'll update and see what happens.
thats always my strategy :) :guitar:

---

### Post by Mutant Corn on 2008-05-10
lol :)

272mb is taking qquite a while...

---

### Post by ghost_ryder35 on 2008-05-10
lol.  that it does.  stop downloading all those naughty pictures and it will go faster ;)

---

### Post by Mutant Corn on 2008-05-10
:oops:

downloading file 90 of 168....at an average of 20kbps :(

Why's it so slow, I wonder?

---

### Post by ghost_ryder35 on 2008-05-10
maybe someone is illigally stealing your internet wirelessly :(

---

### Post by Mutant Corn on 2008-05-10
....could be, but we have 64-bit WEP with no ascii password set, and I'm in a town full of rednecks. If there's someone around here smart enough to do that I'd like to meet them...

---

### Post by ghost_ryder35 on 2008-05-10
> **Mutant Corn said:**
> ....could be, but we have 64-bit WEP with no ascii password set, and **[COLOR=red]I'm in a town full of rednecks. If there's someone around here smart enough to do that I'd like to meet them.[/COLOR]**..
Me and you think a like \\:D/

---

### Post by Mutant Corn on 2008-05-10
[IMG]http://i15.photobucket.com/albums/a362/mutant_corn/cheers.gif[/IMG]

---

### Post by Mutant Corn on 2008-05-10
Done...for some reason flash isn't working but otherwise everything is working fine :)

---

