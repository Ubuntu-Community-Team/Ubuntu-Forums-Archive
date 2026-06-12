---
title: "apt-get autoremove"
date: 2007-07-03
forum: General Help
---

### Post by HeavyAl on 2007-07-03
Hey all, 

Odd thing (to me) here .. I normally use Gnome exclusively but I was in the mood to try new things and so installed all the KDE core stuff and have been messing around with it today. The funny thing is that now when I'm on a command line and do something like this:

```

apt-get remove gdmap

```

I get this along with the notification to remove the given app:

```

The following packages were automatically installed and are no longer required:
  knetwalk kpat kpdf kde-amusements kdepim ksokoban kolf blinken
  kscreensaver-xsavers krdc krec korn krfb kscd kppp libktnef1 kshisen kmoon
  kmahjongg klaptopdaemon ksig ksim libkscan1 kwifimanager kcharselect
  kjumpingcube kdeartwork-style kdeartwork-misc kcoloredit artsbuilder kdessh
  kanagram libpth20 knode kmrml katomic libcvsservice0 kleopatra ksvg
  kdegames-card-data kscreensaver kruler ktux klettres kgoldrunner kbackgammon
  kpoker dirmngr kdepim-kfile-plugins libkiten1 ksnapshot kpackage liblockdev1
  kooka kenolaba kblackbox libkcal2b atlantikdesigner konsolekalendar klatin
  kfloppy kdegraphics-kfile-plugins kstars ttf-dustin ksame kbruch
  libpoppler1-qt kdepim-kio-plugins libkdegames1 kcalc libmimelib1c2a keduca
  kandy kdeedu-data kdemultimedia-kappfinder-data kontact
  kdeadmin-kfile-plugins kdeartwork-theme-icon kmplot kweather kalzium ksirc
  librss1 klinkstatus klickety kpovmodeler ksayit kmouth kalarm noatun-plugins
  kworldclock mpeglib kalzium-data kdewebdev kdegames amor kdict ktouch ktnef
  khexedit kdeaccessibility kedit libkleopatra1 kbounce kvoctrain korganizer
  kdetoys kdenetwork-kfile-plugins kimagemapeditor atlantik kbstate akregator
  tidy libtidy-0.99-0 ark kwordquiz kcron libjasper-runtime kview libdb4.3++c2
  ktron ttf-sjfonts ksync cvs kdenetwork libtiff-tools kttsd
  kdeartwork-emoticons dcoprss ksysv kwin4 kdewallpapers libksieve0 kuser
  klettres-data kreversi kdf libksba8 kspaceduel kig libkpimidentities1
  gnupg-agent kpf juk libkdepim1a noatun kdnssd klines
  kdemultimedia-kfile-plugins fifteenapplet kdemultimedia kfaxview kstars-data
  edict lskat knotes libarts1-mpeglib kgamma kviewshell kfilereplace kommander
  kdeutils kdegraphics kaboodle khangman kaddressbook libkpimexchange1
  kmailcvt libindex0 kanjidic kdeartwork-theme-window ksmiletris konq-plugins
  libkmime2 libarts1-audiofile kxsldbg quanta kbattleship kiconedit
  libmeanwhile1 kdeadmin kpilot kasteroids kfouleggs libgpgme11 libmal1
  libkdeedu3 libkgantt0 knewsticker kopete ksnake kiten eyesapplet kdat karm
  indi kmail kdeedu kdelirc kpercentage superkaramba kjots kfax secpolicy
  ksirtet libjpeg-progs kmines kdvi kget pinentry-qt kgpg konquest
  kate-plugins libboost-python1.33.1 kolourpaint gpgsm gnupg2 kmousetool
  kitchensync kdeaddons-kfile-plugins libarts1-xine kmag kdepim-kresources
  kdepim-wizards kmilo ktuberling kturtle kaudiocreator ktimer quanta-data
  kmid kteatime kverbos kmix kdeartwork kodo
Use 'apt-get autoremove' to remove them.

```

Now, I just installed that stuff, so why is apt thinking that I need to autoremove it?

---

### Post by FuturePilot on 2007-07-03
Are you in Gnome when you try this? Perhaps switch to KDE and then try removing that package.

---

### Post by Juan_VCS on 2007-07-03
It seems like the usual autoremove notice; it shows up after a while as a suggestion but it's not necessary to perform it.

---

### Post by FuturePilot on 2007-07-03
That's not usual though. It only will show up if there are dependencies that are no longer needed. But not an entire DE:o

---

### Post by HeavyAl on 2007-07-03
Yeah, kind of strange. I used synaptic to install kde-base, then found that it was lacking some things so went ahead and installed some other kde package - can't recall which one, it was a meta-package though .. then I switched over to kdm at some point and when i went to remove some old gnome packages to recover some drive space I started getting the messages as above. 

Since messing with that I got frustrated and decided to just try ripping out gnome altogether in the hope of beating this thing into submission but I think I might have taken it a bit too far - it seems adept doesn't warn you of package dependency issues before letting you go ahead with a process and so I'm currently running an uninstall of around 500 megs of apps from that - we'll see what happens when its done. I guess at worst I can reinstall the DE from a CL.

---

### Post by HeavyAl on 2007-07-03
Well, I went to psychocats.net and found various ways of swapping out your DE between gnome, kde etc and followed some of the advice there on how to remove gnome which cleared out a lot more than I expected - ended up losing some things I didn't really want to lose but what the heck, this was a test machine anyhow. 

After killing gnome off (sorry gnome, I love you but this is all in the interest of science!) I did the install of kubuntu-desktop and everything seemed to work fine. Then I tried installing some more packages from the CL and AGAIN I see all that junk about auto-remove .. so now I'm taking the plunge and letting it do it since I didn't have anything concrete built in kde at the moment anyhow. It appears that it actually removed everything that was in that list .. now I've started sudo apt-get install kubuntu-desktop again so that I can be sure to have some sort of DE to boot into ...

... and it looks like everything is there!

More than likely that was NOT the best way to handle this but I hate loose ends and this seems to have tied them up .. yep, just check apt-get again .. no more complaints about needing to auto-remove stuff ..

---

### Post by go_beep_yourself on 2007-11-23
How can

```
sudo apt-get --purge autoremove
```

be done using Synaptic Package Manager?

How can

```
sudo apt-get --purge autoremove
```

be done using Synaptic Package Manager?

How can

```
sudo apt-get --purge autoremove
```

be done using Synaptic Package Manager?

How can

```
sudo apt-get --purge autoremove
```

be done using Synaptic Package Manager?

---

### Post by hikaricore on 2007-11-23
> **go_beep_yourself said:**
> How can

```
sudo apt-get --purge autoremove
```

be done using Synaptic Package Manager?

You're making this entirely too complicated.. lol

1. Start Synaptic
2. Click "**Installed (auto removable)**"
3. Click at the top of the list on the right, then hold Shift, then press the End key.
4. With all of these packages selected right click and chose "Mark For Complete Removal".
5. Hit Apply.

---

### Post by go_beep_yourself on 2007-11-23
> **hikaricore said:**
> You're making this entirely too complicated.. lol

1. Start Synaptic
2. Click "**Installed (auto removable)**"
3. Click at the top of the list on the right, then hold Shift, then press the End key.
4. With all of these packages selected right click and chose "Mark For Complete Removal".
5. Hit Apply.

I don't have "Installed (auto removable)."

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51166&stc=1&d=1195859421[/IMG]

---

### Post by hikaricore on 2007-11-24
Then there aren't any packages that meet this criteria.... ..... ..... ...

---

