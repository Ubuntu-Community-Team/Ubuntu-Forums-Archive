---
title: "tons of packages suddenly showing up as no longer needed in apt"
date: 2008-06-27
forum: General Help
---

### Post by retrovertigo on 2008-06-27
Without warning, when I installed perl-doc yesterday via apt, I got the following:

```
perl-doc is already the newest version.
The following packages were automatically installed and are no longer required:
  knetwalk kpat kpdf texlive-common kalzium-data ksokoban kolf kdemultimedia-kappfinder-data
  blinken krdc krec korn libdb4.6++ krfb kscd kppp kshisen kmoon kdeartwork-style kmahjongg ksim
  libkscan1 kcharselect kcoloredit artsbuilder kdessh kanagram ktip kdeprint
  kdeartwork-theme-window kmrml katomic kleopatra ksvg kruler kpersonalizer
  kdemultimedia-kfile-plugins ktux klettres kgoldrunner kbackgammon kpoker atlantikdesigner
  dirmngr libkpathsea4 libkiten1 kgeography ksnapshot kpackage liblockdev1 kooka kenolaba
  kblackbox kdebase libboost-python1.34.1 klatin kfloppy libopensync0 kstars ksame kbruch kpager
  kdeaddons-kfile-plugins kfilereplace kdeadmin-kfile-plugins kde-core kcalc texlive-base-bin
  kicker-applets libpisock9 libpoppler-qt2 keduca libarts1-xine klipper texlive-fonts-recommended
  konsolekalendar kaudiocreator kdeedu-data kimagemapeditor kweather kmplot ksmserver kalzium
  ksirc ksysguard knetworkconf librss1 klinkstatus klickety kpovmodeler konq-plugins kmouth kalarm
  klaptopdaemon kworldclock mpeglib kdewebdev kmenuedit kregexpeditor kdegames amor kdict ktouch
  khexedit kbounce kvoctrain kdetoys atlantik kbstate tidy gettext arts ark kwordquiz kcron
  superkaramba kview noatun-plugins ktron kdegraphics-kfile-plugins ttf-sjfonts
  kdenetwork-kfile-plugins cvs kdenetwork kttsd dcoprss ksysv kwin4 kate-plugins kuser kreversi
  kdf kspaceduel kig libcvsservice0 kpf juk noatun kdnssd klines kfaxview kstars-data poster edict
  lskat kgamma kviewshell kommander kdegames-card-data libarts1-mpeglib kaddressbook-plugins
  kgeography-data kwifimanager kjumpingcube kdepim-kfile-plugins kdegraphics kaboodle khangman
  kdeartwork-theme-icon kdeartwork-misc kmailcvt libindex0 kanjidic ksysguardd texlive-base
  ksmiletris psutils kxsldbg quanta kbattleship kiconedit kdeadmin kasteroids texlive-doc-base
  kfouleggs libkdeedu3 libkgantt0 knewsticker kopete ksnake kdelibs kiten libtiff-tools kappfinder
  eyesapplet kdat indi kate kdeedu kdewallpapers kpercentage libkdegames1 kjots kde-amusements
  klettres-data kfax kdeartwork-emoticons ksirtet kmines kdvi kget kgpg konquest tex-common
  kolourpaint fifteenapplet kdemultimedia kmousetool kitchensync kmag libtidy-0.99-0 kmilo
  ktuberling kturtle ktimer quanta-data kmid kteatime kverbos kdepasswd kmix kdeartwork
  libarts1-audiofile kodo
Use 'apt-get autoremove' to remove them.
```

The problem is that I *KNOW* I am using several of these apps, like kmix, kate, etc... they are most certainly not in need of removal.

Any idea what caused this/how to resolve it?  I know that I accidentally used aptitude to install something recently (while I normally use apt-get), I don't know if that could have possibly caused this.

---

### Post by unutbu on 2008-06-27
What happens if you try

```
sudo apt-get install kdelibs4c2a
```
That seems to be a common dependency of many if not all of those packages.

Also please post

```
apt-cache policy kdelibs4c2a
```

---

### Post by retrovertigo on 2008-06-30
When I tried to install that package via apt, it said it was already installed.  Here's the output from **apt-cache policy**

```
kdelibs4c2a:
  Installed: 4:3.5.9-0ubuntu7.1
  Candidate: 4:3.5.9-0ubuntu7.1
  Version table:
 *** 4:3.5.9-0ubuntu7.1 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     4:3.5.9-0ubuntu7 0
        500 http://us.archive.ubuntu.com hardy/main Packages
```

---

### Post by unutbu on 2008-06-30
Please run the command
```
dpkg --get-selections > pkgstate
```
and post pkgstate.

---

### Post by retrovertigo on 2008-06-30
Here it is, I bzip2'ed it because it was very long.

Thanks for helping out.

---

### Post by unutbu on 2008-06-30
Run 
```
echo "kde install" | sudo dpkg --set-selections
```
Does the problem go away? 

If it does not entirely go away, post the new list of packages that "were automatically installed and are no longer required"

---

### Post by retrovertigo on 2008-06-30
There was no output to the above command, and the list of packages remained unchanged after running it.

---

### Post by jocko on 2008-06-30
I guess those packages were installed as dependences to something else, that you have uninstalled.
My guess would be that you have removed the package kubuntu-desktop.

---

### Post by unutbu on 2008-06-30
Did you install some packages with aptitude, and others with apt-get (or Synaptic or Adept)?

If you have used aptitude in the past, try:
```
aptitude keep-all
```
(I am getting this from [http://www.phpfreaks.com/forums/index.php?topic=198045.0](http://www.phpfreaks.com/forums/index.php?topic=198045.0))

If you haven't used aptitude in the past, don't execute the above command. (It's probably not a good idea to get aptitude involved in this if it isn't involved already).

---

### Post by retrovertigo on 2008-06-30
**jocko**, I don't have the kubuntu-desktop package installed, and I don't think I ever did.  I'm not certain if it is part of the Kubuntu 8.04 ISO or not.  My system was installed using the 8.04 "KDE4 Remix" DVD.  I then installed the KDE3 environment alongside it.


**unutbu**, I've installed pretty much everything with apt-get, and I installed one package recently (before this all started) using aptitude.  I don't typically use aptitude, but I copy-and-pasted something from the web and didn't change "aptitude" to "apt-get" before hitting Enter.

I tried the keep-all option with aptitude and it worked.  Thanks for the suggestion!

---

