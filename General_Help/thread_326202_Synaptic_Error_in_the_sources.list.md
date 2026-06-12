---
title: "Synaptic Error in the sources.list"
date: 2006-12-27
forum: General Help
---

### Post by ltk5 on 2006-12-27
Hello first!
I've been using Ubuntu for about 3 or 4 months now, and I must say I'm impressed. It works great!
But, because of my newb-ishnes, I have some problems, with which you could maybe help me. The latest one is::D . When I run Synaptic it displays and error:

E: Napa&#269;na vrstica 39 v seznamu virov /etc/apt/sources.list (raz&#269;lenitev distribucije)
E: Napa&#269;na vrstica 2 v seznamu virov /etc/apt/sources.list.d/edgy-universe.list (raz&#269;lenitev distribucije)
E: Seznama virov ni mo&#269; brati.
Pojdite v dialog skladiš&#269;a in odpravite težavo.

too bad it's in slovene, but I'll try to translate:
E: wrong line 39 in  the list of sources /etc/apt/sources.list (dissection of distribution)
E wrong line 2 in the list of sources /etc/apt/sources.list.d/edgy-universe.list (the same as above)
E: the list can't be read
go to the repository and solve the problem..
--this was just a try of translation, I really hope it will help

The problem became noticable, when I opened Software sources and changed the download location from Slovenia to Main Server. Before that I got some errors (but just ignored them; as being used to in windows:( ) 
Then I changed the download location back to Slovenia's server but that didn't help.

Any suggestions;) ?
Thanks!

---

### Post by taurus on 2006-12-27
There is something wrong with your /etc/apt/sources.list so either correct it or post it here and somebody will spot your mistake...

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by ltk5 on 2006-12-27
Ok, here is what I have. Thanks:) I really don't understand much here.

lotko@lotko-ltk05:~$ cat /etc/apt/sources.list

deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe #Added by software-properties
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe #Added by software-properties
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe

---

### Post by taurus on 2006-12-27
Here's the one, third line from the bottom...

```
deb http://si.archive.ubuntu.com/ubuntu/ edgy
```
Therefore, you need to edit /etc/apt/sources.list and remove it...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ltk5 on 2006-12-27
I removed the third line from the bottom, but I still get this error.

lotko@lotko-ltk05:~$ sudo aptitude update
E: Napa&#269;na vrstica 2 v seznamu virov /etc/apt/sources.list.d/edgy-universe.list (raz&#269;lenitev distribucije)
E: Ni mogo&#269;e dobiti zaklenjene datoteke /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Napa&#269;na vrstica 2 v seznamu virov /etc/apt/sources.list.d/edgy-universe.list (raz&#269;lenitev distribucije)
E: The list of sources could not be read.

--the first E says: wrong line 2 ...
--second E:Couldn't get the locked file ...
--the fourth E: wrong line 2 in list..
----------------------------------------------------------
Any ideas maybe?

---

### Post by ltk5 on 2006-12-27
Please help! I still can't update nor install anything

---

### Post by taurus on 2006-12-27
Edit /etc/apt/sources.list and put a # in front of the first line of text, line 2 (since the first line is an empty space)...

```
#deb http://si.archive.ubuntu.com/ubuntu/ edgy main restricted
```
Then, run those two commands again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ltk5 on 2006-12-27
Wohooo! It's almost okay :) thanks. Now I just need to edit the second line here :/etc/apt/sources.list.d/edgy-universe.list 

ok, did that. now I just have a duplicate entry.. gonna check that.

 It works. It has updated and upgraded. Thanks!!:D :D 
Ubuntu forums are such a nice comunnity

---

### Post by taurus on 2006-12-27
> **ltk5 said:**
> Wohooo! It's almost okay :) thanks. Now I just need to edit the second line here :/etc/apt/sources.list.d/edgy-universe.list 

ok, did that. now I just have a duplicate entry.. gonna check that.

 It works. It has updated and upgraded. Thanks!!:D :D 
Ubuntu forums are such a nice comunnity

Glad to hear you have your problem resolved.  ;)

---

### Post by ~LoKe on 2006-12-27
> #deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe #Added by software-properties
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe #Added by software-properties
deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy universe multiverse
#deb [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe
Try that?

---

### Post by ltk5 on 2006-12-27
at the moment :) everything's working fine. I'll try that if it happens again. Thanks:eek:

---

