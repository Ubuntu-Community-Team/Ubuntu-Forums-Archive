---
title: "Accidentally wiped usb stick partition"
date: 2008-04-11
forum: General Help
---

### Post by Old Marcus on 2008-04-11
Probably one of the stupidest things to do, but it happened. I didn't realise it was the usb stick, and wiped it during a reinstallation.

Now my usb stick is a void of empty space, with no partitioning and I've lost a fair amount of data on there as well. Is it possible to recover this? If so, how?

---

### Post by ibuclaw on 2008-04-11
```
 sudo apt-get install testdisk 
```

Then:
```
 sudo testdisk 
```
And follow the instructions on the terminal screen. Choose your device, and save to a separate folder in your /home/username directory to start with, as the filenames may be gibberish and need renaming.
Not to forget that if you save it to your usb disk, you risk loosing more data as the new data overwrites the lost/deleted data. So **save it to your /home/username** directory! I cannot emphasise that any more.

If you can't recover the partition data, then
```
 sudo photorec 
```
Will recover individual files from the disk. (photorec is part of the testdisk package).
Again, first save it to your /home directory as the filenames may be gibberish again.

Regards
Iain

---

### Post by cmnorton on 2008-04-11
I do not know if there is a way for you to recover a "wiped" stick. 

Was it wiped out by formatting the drive during an installation?

What was the file system type?

To re-initialize the file system, you would have to know the memory stick's device name:

Here is mine:

/dev/sda1              1999004   1725024    273980  87% /media/KITS

You will set the paritition on the device with fdisk and put the a filesystem on with mkfs. I am not sure if that file system is mkfs.vfat or not.

Look at man fdisk and man mkfs for more details.

---

### Post by cdenley on 2008-04-11
If the filesystem is untouched, you should be able to mount it
```

sudo mkdir /media/recover
sudo mount /dev/sdb /media/recover -o offset=16384

```
Replace /dev/sdb with the path to your usb drive.

---

### Post by Old Marcus on 2008-04-13
For some reason whenever I try to download/install a package I get a broken package error:
```
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
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  testdisk: Depends: libntfs9 (>= 1.13.1) but it is not installable
E: Broken packages

```
I also get a similar problem trying to get wine and install plugins for totem movie player.

---

### Post by cdenley on 2008-04-14
If this doesn't work...
```

sudo apt-get update
sudo apt-get install testdisk

```

...then you must not have some repositories enabled that you need. If you post your /etc/apt/sources.list, someone might see your problem. My solution in my previous reply shouldn't require any additional packages to be installed.

---

### Post by Old Marcus on 2008-04-14
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```
I think this is because I cannot get a working net connection until linux is installed.

---

### Post by Old Marcus on 2008-04-15
Any help on this one? One of the things I'm trying to do is set my mtu in Windows but don't know how.

---

### Post by cdenley on 2008-04-15
If you can't get internet, you won't be able to install testdisk. Also, all the internet repositories are disabled, or commented out with a "#". Your network problem probably belongs in its own thread. I would need more information to help you with that. For recovering your files, did you try the command from my original reply?
```

sudo mkdir /media/recover
sudo mount /dev/sdb /media/recover -o offset=16384

```
That will mount the first partition of /dev/sdb, regardless of what is in the partition table. If you have no network connection, and the filesystem hasn't been reformatted, this is the easiest way to recover your files.

---

### Post by Old Marcus on 2008-04-16
I sorted out my internet problem, reinstalled linux on a friend's connection, and it seems to work fine now. Haven't done all the testdisk stuff yet.

---

### Post by Old Marcus on 2008-04-16
Ok, I've used photorec to recover the files except that it's not allowing me to access the folders or files. How do I access them via root?

Oh and by the way, thanks to everyone who's helped so far, I really appreciate it. :)

---

### Post by cdenley on 2008-04-16
If you've recovered the files while running photorec as root, the files are probably owned by root. You can just make yourself the owner.
```

sudo chown -R myuser:myuser /path/to/recovered/files

```

---

### Post by Old Marcus on 2008-04-16
Thanks guys, you've really helped a lot. :D

One more question: how do I enable the bloody quick reply? :P

---

### Post by ibuclaw on 2008-04-16
Due to the large community of people willing to help their fellow ubuntu-ers 24/7 at no cost for almost every conceivable problem (except homework).
You will potentially get a very quick answer 75% of the time (If I were to set the bar at within an hour of you posting your question/problem).

If you were unfortunate enough not to get a reply.
That's due to the fact that we were "all sleeping" or were "too busy in the real world"...
So best help is to stay positive and try again in a different timezone!:popcorn:

Regards
Iain

---

### Post by Old Marcus on 2008-04-16
Oh, sorry, I meant the quick reply feature, I can't see a single button that activates it. Sorry for the confusion.

---

