---
title: "Cannot fully upgrade KDE to 3.5.4"
date: 2006-08-05
forum: General Help
---

### Post by GooOS on 2006-08-05
Hi,
I wanted to upgrade to the latest kde to I adjusted the sources.list file to be:
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://kubuntu.org/packages/kde-354 dapper main

```

but when I "apt-get dist-upgrade" I get:
```
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  akregator amor ark artsbuilder atlantikdesigner cervisia dcoprss eyesapplet
  fifteenapplet juk kaboodle kaddressbook kaddressbook-plugins kalarm kalzium
  kamera kanagram kandy kappfinder karm kate kate-plugins kaudiocreator kbabel
  kbruch kbstate kbugbuster kcachegrind kcalc kcharselect kcoloredit kcontrol
  kcron kdat kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin
  kdeadmin-kfile-plugins kdeartwork kdeartwork-style kdeartwork-theme-window
  kdebase kdebase-bin kdebase-kio-plugins kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs4-dev kdelibs4c2a kdelirc
  kdemultimedia kdemultimedia-kfile-plugins kdemultimedia-kio-plugins
  kdenetwork kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesdk
  kdesdk-kfile-plugins kdesdk-kio-plugins kdesdk-misc kdesktop kdessh kdetoys
  kdeutils kdf kdict kdnssd kdvi kedit keduca kfax kfaxview kfind kfloppy
  kgamma kget kghostview kgpg khangman khelpcenter khexedit kicker
  kicker-applets kiconedit kig kitchensync kiten kjots klaptopdaemon klatin
  kleopatra klipper kmag kmail kmailcvt kmenuedit kmid kmilo kmix kmoon
  kmousetool kmouth kmplot kmrml kmtrace knetworkconf knewsticker knode knotes
  kodo kolourpaint kompare konq-plugins konqueror konqueror-nsplugins konsole
  konsolekalendar kontact kooka kopete korganizer korn kpackage kpager kpdf
  kpercentage kpersonalizer kpf kpilot kpovmodeler kppp krdc krec
  kregexpeditor krfb kruler ksayit kscd kscreensaver kscreensaver-xsavers ksig
  ksim ksirc ksmserver ksnapshot ksplash kspy ksvg ksync ksysguard ksysguardd
  ksysv kteatime ktimer ktip ktnef ktouch kttsd kturtle ktux kuiviewer
  kunittest kuser kverbos kview kviewshell kvoctrain kwalletmanager kweather
  kwifimanager kwin kwordquiz kworldclock libarts1-audiofile libarts1-mpeglib
  libarts1-xine libcvsservice0 libkcal2b libkcddb1 libkdeedu3 libkdepim1a
  libkgantt0 libkiten1 libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 librss1 mpeglib
  networkstatus noatun noatun-plugins secpolicy superkaramba umbrello
0 upgraded, 0 newly installed, 0 to remove and 206 not upgraded.
```

so I try to install a single package just to see why:
```
apt-get install fifteenapplet
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
  fifteenapplet: Depends: kdelibs4c2a (>= 4:3.5.3-1) but 4:3.5.2-0ubuntu18.1 is
to be installed
E: Broken packages

```

how i fix it?

---

### Post by Jucato on 2006-08-05
did you do a "sudo apt-get update" first before you "sudo apt-get upgrade"?

---

### Post by ozorba on 2006-08-05
sudo apt-get dist-upgrade

will solve your problem.

---

### Post by reyfer on 2006-08-05
Hi. After "sudo apt-get dist-upgrade" and downloading the packages, I get the following message
> Preconfiguring packages ...
(Reading database ... 96284 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.5.3-0ubuntu0.1 (using .../kdelibs-data_4%3a3.5.4-0ubuntu2~dapper1_all.deb) ...
Unpacking replacement kdelibs-data ...
Replacing files in old package kaffeine ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.4-0ubuntu2~dapper1_all.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package ktorrent
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.4-0ubuntu2~dapper1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
reyfer@reyfer-desktop:~$ 
Can someone tell me how to get this upgrade to work? I'm using Dapper 6.06

---

### Post by GooOS on 2006-08-05
Of course I apt-got dist-upgrade and it upgraded few packages (about 72 MB of download), and The rest 206 packages not upgraded.

---

### Post by RedStar on 2006-08-05
Try using 
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
instead. I'm using that one and the upgrade to kde 3.5.4 went OK.
The only problem is an incorrect dependency stated by the kde-i18n-engb package that requires language-pack-kde-engb. As this  package does not exist I'm still using the earlier version of kde-i18n-engb.

---

### Post by GooOS on 2006-08-05
tried to change the to kde-latest but it's the same,
i tired to figure out what packages stands in my way
and it's:
```
The following packages have unmet dependencies:
  kdelibs4c2a: Depends: libcupsys2 (>= 1.2.1) but 1.2.0-0ubuntu5 is to be installed

```

---

### Post by stoeptegel on 2006-08-05
@gooOS
i don't know if this is the reason, but i think you're missing this in your sources.list:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
I would get a new one on source-o-matic.

@reyfer
You have ktorrent beta or RC installed?
Remove it (with the same package you installed from) before upgrading, you can install it after the upgrade again. There might be other ways of doing this, but i think this is safer than forcing.

---

### Post by GooOS on 2006-08-06
Thank you, that did it!

---

### Post by reyfer on 2006-08-06
THANKS!!!!!:p :p

---

### Post by Buelldozer on 2006-08-07
I think it has something to do with EasyUbuntu. After doing the upgrade to KDE 3.5.4 to both my laptop and my desktop they were both "stuck" and unable to finish the upgrade due to missing/broken dependencies.

As a test I rebuilt my laptop and my desktop using the same Kubuntu 6.06 CD.

On my laptop I installed the CD version, upgraded to the 686 kernel and then added the deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main repo to my sources list (along with enabling the other stock repositories) and it upgraded perfectly.

On the desktop I installed the CD version, upgraded to the 686 kernel, then installed EasyUbuntu then added deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main repo to my sources list (along with enabling the other stock repositories) and the upgrade FAILED. Apt refused to install 75 packes because of missing dependencies.

The ONLY difference between the two installs was the installation of EasyUbuntu and the "stuff" that it installs.

Obviously the 3.022 version of EasyUbuntu needs a little tweaking somewhere.

---

### Post by asimaythink on 2006-08-08
Thank you, adding that source did it for me, too!

@Buelldozer: It's probably due to that missing repository. I have used EasyUbunut, too, and it didn't work, once I added this repository, things went fine.

---

