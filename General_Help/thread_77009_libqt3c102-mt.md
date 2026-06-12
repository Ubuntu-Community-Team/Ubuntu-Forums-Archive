---
title: "libqt3c102-mt"
date: 2005-10-16
forum: General Help
---

### Post by jeremy on 2005-10-16
The only non-free programme that I use is mailwasher, I have tried to install  mailwasher_1.1.2_i386_kubuntu.deb on  Kubuntu 5.10, but it depends on libqt3c102-mt which is not installed, and not available in the repos. Does anyone know where I can get libqt3c102-mt, and will it be safe to install it?

BTW. I have also tried to install kshowmail, but it has the same dependency problem.

---

### Post by greatshape on 2005-10-16
[QUOTE=jeremy]The only non-free programme that I use is mailwasher, I have tried to install  mailwasher_1.1.2_i386_kubuntu.deb on  Kubuntu 5.10, but it depends on libqt3c102-mt which is not installed, and not available in the repos. Does anyone know where I can get libqt3c102-mt, and will it be safe to install it?

BTW. I have also tried to install kshowmail, but it has the same dependency problem.[/QUOTE]

hmmm, running kubuntu breezy here...
root@Linux:/home/steve # apt-cache search libqt3c102-mt
libqt3c102-mt - Qt GUI Library (Threaded runtime version), Version 3
root@Linux:/home/steve #

Did you comment out the universe repo's in sources.list?

Regards, Steve

---

### Post by jeremy on 2005-10-16
Thanks Steve, for your quick reply.
jeremy@work:~$ apt-cache search libqt3c102-mt
returns nothing for me, I have universe and multiverse uncommented in sources.list

---

### Post by greatshape on 2005-10-16
[QUOTE=jeremy]Thanks Steve, for your quick reply.
jeremy@work:~$ apt-cache search libqt3c102-mt
returns nothing for me, I have universe and multiverse uncommented in sources.list[/QUOTE]

apt-get update? 
here's my sources.list

deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by asimon on 2005-10-16
libqt3c102-mt was replaces with libqt3-mt, thus just install libqt3-mt.

---

### Post by jeremy on 2005-10-16
I had already done apt-get update, but have just done it again to be sure, still no libqt3c102-mt.

Here is my sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe

---

### Post by jeremy on 2005-10-16
Thanks asimon, but I already have libqt3-mt installed.

---

### Post by greatshape on 2005-10-16
[QUOTE=jeremy]I had already done apt-get update, but have just done it again to be sure, still no libqt3c102-mt.

Here is my sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe[/QUOTE]


Well , i don't really get it also, but maybe you can give it a try with this one:
[http://packages.debian.org/stable/libs/libqt3c102-mt](http://packages.debian.org/stable/libs/libqt3c102-mt) 

Good luck, 
steve

---

### Post by jeremy on 2005-10-16
Well, I just tried to install [http://packages.debian.org/stable/libs/libqt3c102-mt](http://packages.debian.org/stable/libs/libqt3c102-mt) but it conflicts with libqt3-mt - I do not want to risk removing libqt3-mt!

---

### Post by jeremy on 2005-10-16
I have worked around this by downloading a mailwasher.rpm and using alien to create a .deb, which then installed ok.
Thanks to all for your help and suggestions.

---

### Post by greatshape on 2005-10-16
[QUOTE=jeremy]I have worked around this by downloading a mailwasher.rpm and using alien to create a .deb, which then installed ok.
Thanks to all for your help and suggestions.[/QUOTE]

Nice, but maybe just for the record, can you mention where you've found the mailwasher rpm? 
Not for me, i run my own mailserver, but it might be interesting for other people reading this thread in the future.

Regards, Steve

---

### Post by jeremy on 2005-10-16
Yes, of course, I used mailwasher-1.1.2-050719_mdk101.i386.rpm from [http://www.firetrust.com/firetrustmwpro_download.html](http://www.firetrust.com/firetrustmwpro_download.html)

---

### Post by ndwork on 2005-12-08
Could you explain the last step a little better?  I'm having the same trouble trying to get synaptic to install mythgame.

-Nick

---

### Post by Glenoid on 2006-01-25
I'm new to this sort of thing and I hope this is the appropriate place to present this...

I had a similar problem with the libqt3c102-mt package required for the installation of skype. Needless to say the installation was unsuccessful. 

I tried using alien to convert the skype rpm to a deb package and HEY PRESTO! it worked. 

later...

---

### Post by Seinfeld on 2006-02-07
Check this out and give it a try chaps

[http://forum.skype.com/viewtopic.php?t=30291](http://forum.skype.com/viewtopic.php?t=30291)

The procedure simply "edits" the dependency list file by OR'ing an alternative available library libqt3-mt to the rare/unavailable one
libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt

BINGO.. 

Check it out and let me know ;) 

Thanks

---

### Post by jeremy on 2006-02-08
Yes, that works, thanks.
(I actully did it a few months ago, but didn't think to post it here!)

---

### Post by LaneLester on 2006-07-23
Jeremy, you're a jenius! I would hate to admit how much time I've wasted trying to solve this problem.

The new .deb installed without a hiccup. When I executed mailwasher, it complained about a couple of libraries. I just had to copy the ones I had to files with the version numbers mailwasher was looking for.

Finally, I can stop wading through the spam. Thanks for sharing!

Lane

---

