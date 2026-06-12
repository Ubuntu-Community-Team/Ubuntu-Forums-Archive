---
title: "Uninstall KDE :) .......... so simple"
date: 2008-02-12
forum: General Help
---

### Post by msayed2004 on 2008-02-12
Hi everybody;
As many ppl I installed it on Ubuntu just for testing & I found Gnome better for me, searching for away to uninstall it to free the used 500MB I found suggestions about removal of some vital KDE lib(s) via synaptic which will also tell you about the rest, or to use apt-get to remove the kubuntu-desktop & finally to remove any thing start with k (never do this) !!!

All of the above does not fit me as I already need some of the KDE stuff to use some of the KDE app(s) on Gnome like Quanta+ & because I selected KDE instead of kubuntu-desktop form synaptic when I installed it.

Depending on the installation history saved in synaptic I used the following code to remove it & I made this post to share this method with others in the same situation [COLOR=Red]but you have to know that no one except you will be responsible about any damage occur due to using the following command line[/COLOR] ([Read this please]("http://ubuntuforums.org/announcement.php?f=131")) :

```
sudo apt-get remove akregator amor ark arts artsbuilder atlantik atlantikdesigner blinken dcoprss dirmngr edict enscript eyesapplet fifteenapplet gnupg-agent gnupg2 gpgsm indi juk kaboodle kaddressbook kaddressbook-plugins kalarm kalzium kalzium-data kamera kanagram kandy kanjidic kappfinder karm kasteroids kate kate-plugins katomic kaudiocreator kbackgammon kbattleship kblackbox kbounce kbruch kbstate kcalc kcharselect kcoloredit kcontrol kcron kdat kde kde-amusements kde-core kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-emoticons kdeartwork-misc kdeartwork-style kdeartwork-theme-icon kdeartwork-theme-window kdebase kdebase-bin kdebase-data kdebase-kio-plugins kdeedu kdeedu-data kdegames kdegames-card-data kdegraphics kdegraphics-kfile-plugins kdelibs kdelirc kdemultimedia kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork kdenetwork-kfile-plugins kdepasswd kdepim kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict kdnssd kdvi kedit keduca kenolaba kfax kfaxview kfind kfloppy kfouleggs kgamma kgeography kgeography-data kget kghostview kgoldrunner kgpg khangman khelpcenter khexedit kicker kicker-applets kiconedit kig kimagemapeditor kiten kjots kjumpingcube klaptopdaemon klatin kleopatra klettres klettres-data klickety klines klipper kmag kmahjongg kmail kmailcvt kmenuedit kmid kmilo kmines kmix kmoon kmousetool kmouth kmplot kmrml knetwalk knetworkconf knewsticker knode knotes kodo kolf kolourpaint konq-plugins konqueror konqueror-nsplugins konquest konsole konsolekalendar kontact kooka kopete korganizer korn kpackage kpager kpat kpdf kpercentage kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash kstars kstars-data ksvg ksysguard ksysguardd ksysv kteatime ktimer ktip ktnef ktouch ktron kttsd ktuberling kturtle ktux kuser kverbos kview kviewshell kvoctrain kwalletmanager kweather kwifimanager kwin kwin4 kwordquiz kworldclock kxsldbg libakode2 libarts1-akode libarts1-audiofile libarts1-mpeglib libarts1-xine libboost-python1.34.1 libdb4.4++ libdbus-qt-1-1c2 libgpgme11 libindex0 libjpeg-progs libkcal2b libkcddb1 libkdeedu3 libkdegames1 libkdepim1a libkgantt0 libkiten1 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libpoppler-qt2 libpth20 librss1 libsamplerate0 libtiff-tools lskat networkstatus noatun noatun-plugins pinentry-qt poster psutils superkaramba tex-common texlive-base texlive-base-bin texlive-common texlive-doc-base texlive-fonts-recommended ttf-dustin ttf-sjfonts
```You may need also to open synaptic as it may offer more unneeded lib(s) which can be safely removed as the KDE installation may installed some more stuff on your machine that no other app need it but for me I need anything left from it.

But again be careful.

---

