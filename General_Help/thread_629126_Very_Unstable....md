---
title: "Very Unstable..."
date: 2007-12-02
forum: General Help
---

### Post by hkpolitik on 2007-12-02
I just installed Ubuntu on my Compaq for the first time...

Everything seemed to be working smoothly, So I opened up Firefox and the internet seemed to work so I tried the change my homepage but it  just froze. I had hold the power button to get my pc to shutdown...

After I turned it back on again and logged on it would just display a blank desktop...so I restarted it again and switched the session to Gnome and got it to log on correctly but I can't even update correctly without Ubuntu locking up...

I have a Compaq SR1403WM...Any help is appreciated...

---

### Post by PmDematagoda on 2007-12-02
Some advice, do not cold reboot Ubuntu whenever it freezes as it could damage data and the HDD's, which may be what is wrong with your PC right now, if you want a safer way of restarting Ubuntu while it is frozen, then I recommend that you read this [thread.]("http://ubuntuforums.org/showthread.php?t=617349")

Concerning your problem with the updates, can you post the results of:-

```
cat /etc/apt/sources.list
```

---

### Post by hkpolitik on 2007-12-02
Ok, I won't cold reboot it anymore, and I'll get you the results as soon as I can, but its very difficult to get things running...I assume you want me to put that code into the terminal? Sorry, I'm a total noob...

---

### Post by PmDematagoda on 2007-12-02
Yes, the code must be input into a terminal.

If it is too difficult to get anything running, why don't you try booting Ubuntu by selecting Ubuntu (Recovery Mode), this will start Ubuntu in a CLI(Command Line Interface).

---

### Post by hkpolitik on 2007-12-02
jon@Cannibal:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
jon@Cannibal:~$

---

### Post by hkpolitik on 2007-12-02
This is very strange...

So when I'd open programs they wouldn't display correctly, and I'd have to hover my cursor over them to display chunks of the window...So as I was trying to post the results, Firefox just magically clicked back to a normal functioning mode. Things are displaying correctly now, but the updater is still not working. It gives me this when I try...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by PmDematagoda on 2007-12-02
Your sources.list file looks ok.

Why don't you try:-

```
sudo dpkg --configure -a
```

as suggested by the error message it might solve the problem with updating.

---

### Post by hkpolitik on 2007-12-02
The updates worked, and I'm up to date. Ubuntu is running smoothly now...

Thank you **very** much for your time & patience. :grin:

---

### Post by PmDematagoda on 2007-12-02
> **hkpolitik said:**
> The updates worked, and I'm up to date. Ubuntu is running smoothly now...

Thank you **very** much for your time & patience. :grin:

No problem, glad I was able to help:).

---

