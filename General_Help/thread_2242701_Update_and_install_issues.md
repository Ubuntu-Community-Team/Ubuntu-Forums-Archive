---
title: "Update and install issues"
date: 2014-09-03
forum: General Help
---

### Post by Philip Gray on 2014-09-03
Good evening

I am not sure if this is the correct thread to post this. Please accept my appologies if it is not. It does not seem to fit anywhere. I do not know if my two issues are related. If they are not I will open up a separate post for the second one.

Issue One
I have Ubuntu 12.04LTS 64 bit, Zorin6 64 bit and Linux Mint 17 64 bit together with Windows 7 Ultimate 64 bit installed on my PC. The Linux distros are on a 1TB drive and Windows is on a 2TB drive. I installed Ubuntu and Zorin last year and Mint last month. I am getting errors when I try and install updates from 'Update Manager' and installing software from 'Software Centre' that I never used to get. 

This evening I wanted to install updates in Ubuntu. The updates included a kernal update and updates to Firefox and Google Chromium. When I said install I received a 'Requires installation of untrusted packages' for Chromium. When I deselected the Chromium updates I got it for Firefox. This is crazy because previously they both updated without issue.

I then then closed Update Manager and ran sudo apt-get update in the CLI and I received the response in the attached 'Update Errors 03 Sep 14.txt' file. It appears that nothing was updated. I reopened Update Manager with the same result. I then pulled out my usb modem and reinserted it. I reopened Update Manager and deselected all the Chromium updates and ran install. Well Ubuntu installed everything including the FireFox updates. I then rebooted and opened up Update Manager again, ran Vheck and I only had the Chromium updates. I selected Install and they installed with no issues.

I am wondering what is going on here.

Issue Two
I cannot install any software using the Software Centre'. I keep getting the 'Requires installation of untrusted packages' error. This is happening with programs like 'Dia, Frozen Bubble, OpenArena, Assault Cube' which have been around since 9.04. I was able to install them via Synaptic but with all the lib files I receive a 'Not Authenticated' error which I never used to get. I installed them in Mint without any issues.

I am getting these errors in Ubuntu and Zorin but not in Mint.

Last month I purchased a LTE/4G USB Vodafone modem, model K5008-Z. Previously I was using a Vodafone Huweii E220 3G modem. I am using the 4G in Ubuntu and Zorin and the 3G in Mint. I have noticed that when I insert the 4G modem Ubuntu registers it as a 'Wired Connection' and not as a 'Mobile Broadband' connection. I do not know if this has anything to do with these very weird errors.

Does anyone have have an idea as to what is going on here. I will appreciate any and all advise. In Windows the 4G modem registers as a LAN device.

Regards
Philip

---

### Post by moore.bryan on 2014-09-03
Have  you tried temporarily setting your /etc/apt/sources.list to one of the other mirrors to see if that's the issue?

---

### Post by Philip Gray on 2014-09-03
Hi moore.bryan

No I have not. I have looked in the sources.list file and I do not see where to change to a mirror site. This is my sources.list file:

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main
deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main


Regards
Philip

---

### Post by ibjsb4 on 2014-09-03
For badsig I like this fix:
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

More here:
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9)

To change your mirror:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu)

And a list of mirrors:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by yancek on 2014-09-03
Zorin 5 is unsupported so I would not expect to be able to update it.  It is based on Lubuntu 11.10 which is also unsupported.  Zorin 9 is available if you want it.

Two of the images you posted are warnings not errors and if you trust the source, which is not directly from the Ubuntu repositories, you should be able to install the app.

---

### Post by moore.bryan on 2014-09-04
go with ibjsb4's suggested links; excellent resources and advice.

---

### Post by mcduck on 2014-09-04
"Requires installation of untrusted packages" is a warning you'll get when ever any of your configured software sources can't be auhenticated, for example because of adding a third-party repository but not the signing key for that repository. (It could also be temporarily caused by issues on the repsoitory server, but that's quite rare especially on any of the official Ubuntu servers, and in that case the error would disappear as soon as the server is sorted out again).

So, the error *does not depend on if any of the packages you try to update/install actually comes from the unverified source*, simply having such source configured is enough. (The wording in the error is pretty confusing in this sense).

Anwyay, the fix is fairly simple, usually "apt-get update" should give you warnrings about the repository in question, but you can also do a simple manual check by comparing the repositories, and installed signing keys, in Software Sources to see if youa re indeed missing a key. And then just find & import the missing key and the warning message should disappear as well.

---

### Post by Philip Gray on 2014-09-09
Hi 

Thank you everyone for yr help my BADSIG problem is solved. I did the following which worked. My other issue with files in synaptic not been authenticated seems to have been resolved as well.

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean

Regards
Philip

---

### Post by ibjsb4 on 2014-09-09
Good deal :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by moore.bryan on 2014-09-11
Congrats... make sure to mark this thread as "solved."

---

