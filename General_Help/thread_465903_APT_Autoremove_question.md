---
title: "APT Autoremove question"
date: 2007-06-06
forum: General Help
---

### Post by dkaddict on 2007-06-06
Hello to all,

I have a question regarding apt which I am hoping someone can help me with. Big thanx in advance for any and all replies!

Ok, all it is is, when I use apt to download and install an application through the command line, ie 'sudo apt-get install blahblahblah' it works fine and the app is installed correctly etc. During this process, however, apt tells me of a load of apps that I no longer need and suggests my using 'apt-get autoremove' to get rid of them. Now I would normally go ahead and get rid of this clutter from my notebook. The list of apps, however, that apt wants me to remove just seems too long. in fact, it loks like most of the stuff I have on my comp. I will post the list below.

Here it is

dkaddict@dkaddict-knotebook:~$ sudo apt-get remove noatun
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  emodule0-screenshot python-crypto knetwalk kpat kde-amusements
  kdepim libxtrap-dev ksokoban kolf emodule0-wlan blinken
  python-zopeinterface python-twisted-names krec korn libxmuu-dev
  python-twisted-core kshisen kmoon kmahjongg ksig kwifimanager
  kcharselect kjumpingcube kcoloredit artsbuilder kdessh kanagram
  libpth20 katomic kleopatra kdegames-card-data kruler
  linux-headers-2.6.20-15-generic ktux libatk1.0-dev klettres
  kgoldrunner kbackgammon kpoker dirmngr kdepim-kfile-plugins
  emodule0-language libkiten1 kpackage kenolaba liburi-perl
  kblackbox python-twisted-web libfame-0.9 libpango1.0-dev
  atlantikdesigner konsolekalendar klatin kfloppy kstars ttf-dustin
  ksame kbruch libdecoration0 python-twisted-runner libpvm3
  libkdegames1 linux-headers-2.6.20-15-386 libhtml-parser-perl
  libpisock9 emodules0-all keduca kandy emodule0-mail libpostproc0d
  kdeedu-data kdemultimedia-kappfinder-data libcairo2-dev kmplot
  kweather kalzium ksirc libdjconsole0 librss1 klinkstatus klickety
  libdirectfb-extra ksayit emodule0-photo
  linux-headers-2.6.20-13-generic libxp-dev kmouth kalarm
  kworldclock mpeglib kalzium-data kdewebdev emodule0-deskshow
  kdegames kicker-applets amor emodule0-taskbar kdict
  x11proto-trap-dev ktouch libdirectfb-dev ktnef x11proto-record-dev
  kdeaccessibility emodule0-flame kbounce kvoctrain kdetoys
  kimagemapeditor atlantik python-twisted-mail tidy libtidy-0.99-0
  kwordquiz emodule0-moon libdb4.3++c2 ktron ttf-sjfonts ksync
  kdenetwork libtiff-tools kttsd x11proto-scrnsaver-dev
  libgnomecanvasmm-2.6-1c2a dcoprss ksysv kwin4 kuser klettres-data
  kreversi kdf libgtk2.0-dev libksba8 kspaceduel kig
  python-twisted-lore python-twisted-conch gnupg-agent juk
  python-twisted-news emodule0-mixer python-twisted-words
  emodule0-rain klines fifteenapplet kfaxview kstars-data
  emodule0-cpu emodule0-uptime edict python-twisted lskat
  libarts1-mpeglib kaddressbook-plugins kgamma transcode
  kfilereplace kommander libdjconsole-data libxpm-dev
  linux-headers-2.6.20-13-386 kdeutils kdegraphics kaboodle
  x11proto-print-dev khangman linux-headers-2.6.20-13
  linux-headers-2.6.20-14 linux-headers-2.6.20-15 emodule0-mem
  libindex0 kanjidic emodule0-net linux-headers-2.6.20-14-generic
  ksmiletris libarts1-audiofile kxsldbg quanta kbattleship kiconedit
  libmac2 kdeadmin kpilot kasteroids kfouleggs libmal1 libkdeedu3
  libkgantt0 knewsticker emodule0-tclock libhtml-tree-perl
  emodule0-snow ksnake kiten emodule0-winselector eyesapplet
  emodule0-slideshow libwww-perl kdat indi kdeedu kpercentage
  superkaramba kjots kfax secpolicy ksirtet kmines kdvi kget
  pinentry-qt libhtml-tagset-perl libxss-dev kgpg libid3-3.8.3c2a
  konquest kate-plugins libboost-python1.33.1 kolourpaint
  python-twisted-bin libxtst-dev gpgsm gnupg2
  kdeaddons-kfile-plugins emodule0-alarm x-dev emodule0-forecasts
  libarts1-xine linux-headers-2.6.20-14-386 ktuberling kturtle
  ktimer libmpeg3-1 quanta-data kmid kteatime kverbos
  emodule0-weather kodo
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kde kdeaddons kdemultimedia noatun noatun-plugins
0 upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 8745kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 221717 files and directories currently installed.)
Removing kde ...
Removing kdeaddons ...
Removing kdemultimedia ...
Removing noatun-plugins ...
Removing noatun ...
dkaddict@dkaddict-knotebook:~$


Does that long list seem too long? 
If I go ahead with 'auto-remove' will I have problems thereafter?
Also, on the above copy of my terminal output, it says that, in removing Noatun, it has also removed 'kde, kde-addons, and kdemultimedia'. Are these packages ok to get rid of?

I am relatively new to Linux and think it is great. Windows is history in my on-line life now and I won't use it unless really necessary. The only annoyance I have with (K)Ubuntu is the package dependency thing. As I have shown, in order to uninstall Noatun I had to lose the KDE, KDE-multimedia etc apps.

I am confused now as to what I can get rid of without messing my config up.

Help!!!!
:)

Peace

dkaddict

EDIT: Now I have removed Noatun, when I (left) click on a music file I get the following error message

'KDEInit could not launch 'NOATUN'
Could not find 'noatun' executable.

I removed Noatun because I want to play my tunes with XMMS and got fed up having to right click and 'open with' XMMS. I still have to do so, despite removing Noatun.
Is there a way I can tel KDEInit to launch XMMS as the default player?

Thanx again

dkaddict

---

### Post by Nonno Bassotto on 2007-06-06
Please, do not autoremove all that stuff!

The fact is the following: you have metapackages, which are there just to have dependencies. So you install kde and have all the dependencies installed at a time. When you removed noatun, which is a kde dependency, kde and something else had to be removed too. This is fine, they are just metapackages. But then APT thinks you don't need anything which was installed as a kde dependency, and this is plain false, so do not use the autoremove option.

To open the music files with xmms I think you have to associate these files with the program in the K control center.

---

### Post by dkaddict on 2007-06-06
Ok. Thanks a lot for your reply. I am glad I asked now for I was planning on doing wha apt was suggesting I should do. Again, the list just seemed too long so I have had a stroke of luck really. I am going to try to make the time to have a better look at the meta-package/dependencies thing. it's no good complaining about something I haven't looked into properly.

Thanks again for your reply

Your English looks pretty good to me. Better, dare I say it, than your average Englishman. ;)

peace

dkaddict

---

