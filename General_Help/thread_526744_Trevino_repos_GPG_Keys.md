---
title: "Trevino repos GPG Keys"
date: 2007-08-15
forum: General Help
---

### Post by skymera on 2007-08-15
im sure you all know about that HUGE sources list from Trevino.
and you all know how much a pain int he *** it can be adding all the missing GPG!

well, since im a nice guy, ive listed ALL the GPG keys needed.
ive done this in my own time, hopefully get some good commentrs.

or a stick to keep useful for new users :)

also take reference at the sources list at bottom :)

```


gpg --keyserver subkeys.pgp.net --recv 033431536A423791
gpg --export --armor 033431536A423791 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv A278DF5EE8BDA4E3
gpg --export --armor A278DF5EE8BDA4E3 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv CB210090B029CB84
gpg --export --armor CB210090B029CB84 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 2A5E3A5A52ABFCB1
gpg --export --armor 2A5E3A5A52ABFCB1 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 8BB73F9E1D59E694
gpg --export --armor 8BB73F9E1D59E694 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 80E5E56B02544D0E
gpg --export --armor 80E5E56B02544D0E | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv A361B38AB6A4EB33
gpg --export --armor A361B38AB6A4EB33 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv C12ADDB16FB65A0F
gpg --export --armor C12ADDB16FB65A0F | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv FC0A1CC62F306651
gpg --export --armor FC0A1CC62F306651 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 4C8BC4C880DF6D58
gpg --export --armor 4C8BC4C880DF6D58 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 2404ED3A6AAAA569
gpg --export --armor 2404ED3A6AAAA569 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv BC40ED2499419355
gpg --export --armor BC40ED2499419355 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 371A69E3AE3BE9AA
gpg --export --armor 371A69E3AE3BE9AA | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 223020C2A7C6F0DF
gpg --export --armor 223020C2A7C6F0DF | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 9CFD7AEA3C6489CB
gpg --export --armor 9CFD7AEA3C6489CB | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 576856718434D43A
gpg --export --armor 576856718434D43A | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 84F27CD6A2BF7BCB
gpg --export --armor 84F27CD6A2BF7BCB | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv A714EB87D1B1F415
gpg --export --armor A714EB87D1B1F415 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 49A120FD1135D466
gpg --export --armor 49A120FD1135D466 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 3A39A02A92132F7B
gpg --export --armor 3A39A02A92132F7B | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 2A5E3A5A52ABFCB1
gpg --export --armor 2A5E3A5A52ABFCB1 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 0E466170BCF1FC29
gpg --export --armor 0E466170BCF1FC29 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 8CC68B397E2E4741
gpg --export --armor 8CC68B397E2E4741 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv BC40ED2499419355
gpg --export --armor BC40ED2499419355 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 580E2519969F3F57
gpg --export --armor 580E2519969F3F57 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 4C8BC4C880DF6D58
gpg --export --armor 4C8BC4C880DF6D58 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv DB5D6B0AA3012FB3
gpg --export --armor DB5D6B0AA3012FB3 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv B8F0E6C98ABD1965
gpg --export --armor B8F0E6C98ABD1965 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 3C33E735F854AFD7
gpg --export --armor 3C33E735F854AFD7 | sudo apt-key add -

gpg --keyserver subkeys.pgp.net --recv 02D40794DD385D79
gpg --export --armor 02D40794DD385D79 | sudo apt-key add -

```

AT LAST! WOO
and now the sources, taken directly from Trevino site.

```

    # Treviño’s Ubuntu Feisty Fawn Sources list
    # http://3v1n0.tuxfamily.org/blog/?page_id=13
    #
    # Repository List based on standard feisty with many extra packages
    #
    # If you get errors about missing keys, lookup the key in this file
    # and run these commands (replace KEY with the key number):
    #
    #  gpg --keyserver subkeys.pgp.net --recv KEY
    #  gpg --export --armor KEY | sudo apt-key add -
    #
    # If you have a gpg key URL use (replace URL with the key address):
    #
    #  wget URL --quiet -O - | sudo apt-key add -
    #
    # If you have a gpg key file use (replace FILE with the key file):
    #
    #  sudo apt-key add FILE
    #
    # In the repository list page there’s also a script that can do this
    # work automatically, this is suggested only if you know what you’re doing

    # Ubuntu supported packages (GPG key: 437D05B5)
    deb http://archive.ubuntu.com/ubuntu feisty main restricted
    deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
    deb http://archive.ubuntu.com/ubuntu feisty-security main restricted
    deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted
    deb-src http://archive.ubuntu.com/ubuntu feisty main restricted
    deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted
    deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted
    deb-src http://archive.ubuntu.com/ubuntu feisty-proposed main restricted

    # Ubuntu community supported packages (GPG key: 437D05B5)
    deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
    deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
    deb http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
    deb http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse
    deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
    deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
    deb-src http://archive.ubuntu.com/ubuntu feisty-security universe multiverse
    deb-src http://archive.ubuntu.com/ubuntu feisty-proposed universe multiverse

    # Ubuntu backports project (GPG key: 437D05B5)
    deb http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse
    deb-src http://mi.mirror.garr.it/ubuntu feisty-backports main restricted universe multiverse

    # CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
    # RealPlayer10, Opera, VmWare Server and more to come.)
    deb http://archive.canonical.com/ubuntu feisty-commercial main

    # UbuntuStudio Repository (GPG key: B6A4EB33)
    deb http://archive.ubuntustudio.org/ubuntustudio feisty main
    deb-src http://archive.ubuntustudio.org/ubuntustudio feisty main

    ## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
    #deb http://kubuntu.org/packages/kde-latest feisty main
    #deb-src http://kubuntu.org/packages/kde-latest feisty main

    ## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
    #deb http://kubuntu.org/packages/koffice-latest feisty main
    #deb-src http://kubuntu.org/packages/koffice-latest feisty main

    ## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
    #deb http://kubuntu.org/packages/amarok-latest feisty main
    #deb-src http://kubuntu.org/packages/amarok-latest feisty main

    # kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
    deb http://kubuntu.org/packages/kde4-3.90.1 feisty main
    deb-src http://kubuntu.org/packages/kde4-3.90.1 feisty main

    # Bleeding edge wine packages
    deb http://wine.budgetdedicated.com/apt feisty main
    deb-src http://wine.budgetdedicated.com/apt feisty main

    # Seveas’ packages (GPG key: 1135D466)
    # GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
    deb http://mirror.ubuntulinux.nl feisty-seveas all
    deb-src http://mirror.ubuntulinux.nl feisty-seveas all

    # The Opera browser (packages) (GPG key: 6A423791)
    deb http://deb.opera.com/opera etch non-free

    ## Google picasa packages (GPG key: 7FAC5991 - missing)
    #deb http://dl.google.com/linux/deb/ stable non-free

    # Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
    # GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
    deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
    deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

    # The repository from Kubuntu Germany
    # GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
    deb http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
    deb-src http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview

    # Achim’s Unofficial ‘feisty’ Kubuntu packages
    # GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
    deb http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
    deb-src http://www.mpe.mpg.de/~ach/kubuntu/feisty ./

    # Ubuntu feisty University Klagenfurt packages
    # GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
    # $ sudo apt-key add uniklu-debuild.pub
    #   uniklu:         backports and new packages
    #   uniklu-intern:  not freely redistributable (jvm), or modified packages
    #   uniklu-testing: packages not ready for general use
    deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu
    deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-intern
    deb     http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-testing
    deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu
    deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-intern
    deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  feisty  uniklu-testing

    # MEPIS improvements, overrides and updates (distro based on kubuntu)
    #deb http://apt.mepis.org/mepis32-6.5/ mepis main
    #deb http://apt.mepis.org/simply32-6.0/ mepis main

    # Ekiga and Debian pkg-voip
    deb http://pkg-voip.buildserver.net/ubuntu feisty main

    # MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
    deb http://home.eng.iastate.edu/~superm1 feisty all
    deb-src http://home.eng.iastate.edu/~superm1 feisty all

    # Official Beryl Ubuntu Packages (GPG key: 1609B551)
    # GPG key-file: http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
    deb http://ubuntu.beryl-project.org feisty main
    deb-src http://ubuntu.beryl-project.org feisty main

    # Ubuntu repository for Screenlets (GPG key: F854AFD7)
    # GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
    deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
    deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

    # Subpixel Font rendering packages (GPG key: 937215FF)
    # Improved fonts on LCDs - WARNING: May violate some patents
    # GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
    deb http://www.telemail.fi/mlind/ubuntu feisty fonts main
    deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts main

    ## Others mlind experimental misc Packages (GPG key: 937215FF)
    ## GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
    #deb http://www.telemail.fi/mlind/ubuntu feisty experimental
    #deb-src http://www.telemail.fi/mlind/ubuntu feisty experimental

    # Skype packages
    deb http://download.skype.com/linux/repos/debian/ stable non-free

    # Geole’s Ubuntu Repository
    # GPG key-file: http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
    deb http://ubuntu.geole.info/ feisty universe multiverse
    deb-src http://ubuntu.geole.info/ feisty universe multiverse
    deb http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted
    deb-src http://ubuntu.geole.info/ feisty-backports main universe multiverse restricted

    # Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
    deb http://www.linux2go.dk/ubuntu feisty main
    deb-src http://www.linux2go.dk/ubuntu feisty main

    # Asher256’s Repository
    deb http://asher256-repository.tuxfamily.org edgy main dupdate french
    deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

    # Tvfreeplayer Packages (GPG key: )
    # GPG key-file: http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg
    deb http://www.tvfreeplayer.com/linux/falcon feisty all
    deb-src http://www.tvfreeplayer.com/linux/falcon feisty all

    # gnomemeeting - ekiga (GPG key: 52ABFCB1)
    deb http://snapshots.ekiga.net/ubuntu/ feisty main
    deb-src http://snapshots.ekiga.net/ubuntu/ feisty main

    ## lprod packages: many audio/video apps: avidemux, cinelerra…
    #deb http://lprod.org/deb/feisty/ ./
    #deb-src http://lprod.org/deb/feisty/ ./

    # Cinelerra Feisty packages
    deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./

    ## Spring Packages (RTS game)
    #deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
    #deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

    # Cafuego’s feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)…
    deb http://au.ubuntu.cafuego.net feisty-cafuego all
    deb-src http://au.ubuntu.cafuego.net feisty-cafuego all

    # Debuntu Ubuntu feisty packages
    # GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
    deb http://repository.debuntu.org/ feisty multiverse
    deb-src http://repository.debuntu.org/ feisty multiverse

    ## BMPx feisty Repository
    ## GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
    #deb http://files.beep-media-player.org/packages/ubuntu feisty main testing
    #deb-src http://files.beep-media-player.org/packages/ubuntu feisty main testing

    # Morgoth Repository (GPG key: 7E2E4741)
    # Provides Monkey’s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity…
    # GPG key-file: http://morgoth.free.fr/files/morgoth-signkey.gpg.asc
    deb http://morgoth.free.fr/ubuntu feisty-backports main
    deb-src http://morgoth.free.fr/ubuntu feisty-backports main

    ## ATi & nVidia drivers Ubuntu packages
    ## GPG key: http://albertomilone.com/drivers/tseliot.asc
    #deb http://www.albertomilone.com/drivers/feisty/latest/32bit binary/

    # Automatix repository (GPG key: E23C5FC3)
    deb http://www.getautomatix.com/apt feisty main

    # edevelop - e17 (Enlightenment DR 17)
    # GPG key: http://lut1n.ifrance.com/repo_key.asc
    deb http://edevelop.org/pkg-e/ubuntu feisty e17
    deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
    #deb http://e17.dunnewind.net/ubuntu feisty e17
    #deb-src http://e17.dunnewind.net/ubuntu feisty e17

    # Musicbrainz Repository
    # GPG key-file: http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key
    deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz
    deb-src http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz

    ## Imbrandons software repository (GPG key: 887D9FD2)
    ## GPG key-file: http://www.imbrandon.com/packages/887D9FD2.gpg
    #deb http://www.imbrandon.com/packages feisty all
    #deb-src http://www.imbrandon.com/packages feisty all

    ## Candyz’s Ubuntu Packages
    ## GPG key-file: http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
    #deb http://cle.linux.org.tw/candyz/Ubuntu/feisty i386/

    # The Ubuntu NLP Repository (GPG key: 8ABD1965)
    # GPG key-file: http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg
    deb http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all
    deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp feisty all

    # Ubuntu System Administrator packages (GPG key: 2F306651)
    # GPG key-file: http://ubuntu.moshen.de/2F306651.gpg
    deb http://ubuntu.moshen.de feisty multimedia misc
    deb-src http://ubuntu.moshen.de feisty multimedia misc

    ## Michael Biebl Tracker Repository (GPG key: BD058554)
    ## GPG Key-file: http://www.teco.edu/~biebl/biebl.asc
    #deb http://debs.michaelbiebl.de/ feisty main
    #deb-src http://debs.michaelbiebl.de/ feisty main

    # The Consciousness Repository (GPG key: DD385D79)
    # GPG key-file: http://debs.peadrop.com/DD385D79.gpg
    deb http://debs.peadrop.com feisty all
    deb-src http://debs.peadrop.com feisty all

    ## Tolero Ubuntu Repository
    #deb http://ubuntu.tolero.org/ feisty main
    #deb-src http://ubuntu.tolero.org/ feisty main

    # IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
    # GPG key-file: http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg
    deb http://dl.ivtvdriver.org/ubuntu feisty all
    deb-src http://dl.ivtvdriver.org/ubuntu feisty all

    # syzygy42 repository: avant-window-navigator, exaile, closure… (GPG key: 8434D43A)
    # GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
    deb http://download.tuxfamily.org/syzygy42/ feisty all
    deb-src http://download.tuxfamily.org/syzygy42/ feisty all

    ## Firefox 3.0 alpha builds for feisty (unstable)
    #deb http://gnomefreak.youmortals.com/mozilla-testing feisty main
    #deb-src http://gnomefreak.youmortals.com/mozilla-testing feisty main

    ## Swiftfox (enhanced Firefox for linux) packages
    deb http://getswiftfox.com/builds/debian unstable non-free

    # Sonnes repository (aMule AdunanZa, Audacious)
    deb http://adurepo.altervista.org/ubuntu feisty all
    deb-src http://adurepo.altervista.org/ubuntu feisty all

    # darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
    # GPG key-file: http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg
    deb http://mirror.randumb.org/darkmagez/repo feisty-darkmagez multimedia-experimental #core-experimental
    deb-src http://mirror.randumb.org/darkmagez/repo feisty-darkmagez multimedia-experimental #core-experimental

    ## Raof Repository: newer versions of Compiz, beagle, mono, scribus… (GPG key: 2F306651)
    ## GPG key-file: http://raof.dyndns.org/falcon/2F306651.gpg
    #deb http://raof.dyndns.org/falcon feisty all
    #deb-src http://raof.dyndns.org/falcon feisty all

    # FoLKeN ‘Repozytorium’ (GPG key: 6FB65A0F)
    deb http://deb.svx.pl/ feisty main universe bleeding
    deb-src http://deb.svx.pl/ feisty main universe bleeding

    # Le dépomaniak repository (GPG key: 1D59E694)
    # GPG key-file: http://ubuntu.davromaniak.eu/1D59E694.gpg
    deb http://ubuntu.davromaniak.eu feisty-depomaniak all
    deb-src http://ubuntu.davromaniak.eu feisty-depomaniak all

    # Mez’s Repository (GPG key: 6AAAA569)
    # GPG key-file: http://apt.sourceguru.net/6AAAA569.gpg
    deb http://apt.sourceguru.net feisty all
    deb-src http://apt.sourceguru.net feisty all

    # Ryan Kavanagh’s packages (GPG key: 02544D0E)
    # GPG key-file: http://packages.ryanak.ca/02544D0E.gpg
    deb http://packages.ryanak.ca ryan-feisty all
    deb-src http://packages.ryanak.ca ryan-feisty all

    # OpenedHand Debian/Ubuntu Packages
    deb http://debian.o-hand.com feisty/
    deb-src http://debian.o-hand.com feisty/

    # OpenSync svn ubuntu repository (GPG key: B029CB84)
    deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
    deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
    # deb http://www.in.fh-merseburg.de/~jahn/opensync-svn/ feisty main
    # deb-src http://www.in.fh-merseburg.de/~jahn/opensync-svn/ feisty main

    # Iuculano’s debian packages (GPG key: AE3BE9AA)
    # GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg
    deb http://ubuntu.iuculano.it feisty amsn thunderbird #ck-kernel #all
    deb-src http://ubuntu.iuculano.it feisty amsn thunderbird #ck-kernel #all

    # Elisa Debian Packages
    deb http://elisa.fluendo.com/packages feisty main

    # PollyCooke, il repository :)
    deb http://download.tuxfamily.org/pollyrepo feisty/

    # Treviño’s Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
    # Many "random" bleeding edge software: aMule, aMSN, Mercury, flash…
    # Further informations and complete packages list: http://3v1n0.tuxfamily.org
    deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
    deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0

    # Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
    # Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
    # built using latest available (working) sources from git/svn/cvs…
    deb http://download.tuxfamily.org/3v1deb feisty eyecandy
    deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

    ## Treviño’s Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
    ## Ubuntu kernels patched with Suspend2 plus other related tools www.suspend2.net
    ## Warning: they will replace standard ubuntu kernel related packages
    #deb http://download.tuxfamily.org/3v1deb feisty suspend2
    #deb-src http://download.tuxfamily.org/3v1deb feisty suspend2

```

Your Welcome :D
please comment/ move if necessary/ stick if necessary

---

### Post by steveneddy on 2007-08-15
cool - thanks

---

### Post by skymera on 2007-08-15
nooo problem :D

---

### Post by rigdzinthar on 2007-08-22
seriously awesome, 
i always avoided his repos for the "non-ease" reason

---

### Post by bmxmarine on 2007-09-04
where do i put the gpg's in what file?

---

### Post by skymera on 2007-09-05
add all the repos.
and 
sudo apt-get update

it will say that its missing a load of gpg keys 
which i have kidnly puy=t in this post.

enter them intop the terminal :)

---

### Post by Coyote21 on 2007-09-18
That list is an fake, half of the packages don't work, because their can't be reached, the sites where their are have been used for something else, and plus if you get the amd64 ubuntu installed even more packages don't work. It's an totally waste of time... :(

This is the output of my apt-get update

```

Obter:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-pt_PT
Ign http://security.ubuntu.com feisty-security/restricted Translation-pt_PT
Obter:2 http://www.linux2go.dk feisty Release.gpg [191B]
Obter:3 http://kubuntu.org feisty Release.gpg [189B]
Ign http://kubuntu.org feisty/main Translation-pt_PT
Obter:4 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-pt_PT
Obter:5 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-pt_PT
Obter:6 http://download.tuxfamily.org feisty Release.gpg [189B]
Ign http://download.tuxfamily.org feisty/all Translation-pt_PT
Obter:7 http://download.tuxfamily.org feisty Release.gpg [189B]
Obter:8 http://archive.ubuntu.com feisty-proposed Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-proposed/restricted Translation-pt_PT
Ign http://archive.ubuntu.com feisty-proposed/main Translation-pt_PT
Obter:9 http://elisa.fluendo.com feisty Release.gpg [189B]
Obter:10 http://archive.czessi.net feisty Release.gpg [481B]
Ign http://archive.czessi.net feisty/main Translation-pt_PT
Obter:11 http://medibuntu.sos-sts.com feisty Release.gpg [189B]
Ign http://medibuntu.sos-sts.com feisty/free Translation-pt_PT
Ign http://security.ubuntu.com feisty-security/universe Translation-pt_PT
Ign http://security.ubuntu.com feisty-security/multiverse Translation-pt_PT
Ign http://security.ubuntu.com feisty-security/restricted Translation-pt_PT
Obter:12 http://ubuntu.geole.info feisty Release.gpg [481B]
Ign http://ubuntu.geole.info feisty/universe Translation-pt_PT
Ign http://ubuntu.geole.info feisty/multiverse Translation-pt_PT
Obter:13 http://janvitus.interfree.it feisty-upure64 Release.gpg [189B]
Ign http://janvitus.interfree.it feisty-upure64/main-amd64 Translation-pt_PT
Atingido http://security.ubuntu.com feisty-security Release
Ign http://www.mpe.mpg.de ./ Release.gpg
Ign http://www.mpe.mpg.de ./ Translation-pt_PT
Obter:14 http://deb.opera.com etch Release.gpg [189B]
Ign http://deb.opera.com etch/non-free Translation-pt_PT
Obter:15 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-pt_PT
Ign http://kubuntu.org feisty/main Translation-pt_PT
Ign http://ubuntu.tolero.org feisty Release.gpg
Ign http://kubuntu.org feisty Release.gpg
Ign http://kubuntu.org feisty/main Translation-pt_PT
Ign http://ubuntu.tolero.org feisty/main Translation-pt_PT
Ign http://kubuntu.org feisty/main Translation-pt_PT
Obter:16 http://ubuntu.uni-klu.ac.at feisty Release.gpg [189B]
Ign http://ubuntu.uni-klu.ac.at feisty/uniklu Translation-pt_PT
Ign http://ubuntu.uni-klu.ac.at feisty/uniklu-intern Translation-pt_PT
Ign http://www.linux2go.dk feisty/main Translation-pt_PT
Atingido http://archive.canonical.com feisty-commercial Release
Obter:17 http://snapshots.ekiga.net feisty Release.gpg [189B]
Ign http://snapshots.ekiga.net feisty/main Translation-pt_PT
Atingido http://wine.budgetdedicated.com feisty Release
Err http://wine.budgetdedicated.com feisty Release
  
Obter:18 http://e17.dunnewind.net feisty Release.gpg [189B]
Ign http://archive.ubuntu.com feisty-proposed/multiverse Translation-pt_PT
Ign http://archive.ubuntu.com feisty-proposed/universe Translation-pt_PT
Atingido http://archive.ubuntu.com feisty-proposed Release
Ign http://archive.czessi.net feisty/restricted Translation-pt_PT
Ign http://archive.czessi.net feisty/universe Translation-pt_PT
Ign http://archive.czessi.net feisty/multiverse Translation-pt_PT
Ign http://archive.czessi.net feisty/preview Translation-pt_PT
Atingido http://archive.czessi.net feisty Release
Err http://archive.czessi.net feisty Release
  
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-pt_PT
Ign http://medibuntu.sos-sts.com feisty/free Translation-pt_PT
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-pt_PT
Atingido http://medibuntu.sos-sts.com feisty Release
Err http://medibuntu.sos-sts.com feisty Release
  
Obter:19 http://ubuntu.geole.info feisty-backports Release.gpg [481B]
Ign http://ubuntu.geole.info feisty-backports/main Translation-pt_PT
Ign http://ubuntu.geole.info feisty-backports/universe Translation-pt_PT
Ign http://ubuntu.geole.info feisty-backports/multiverse Translation-pt_PT
Obter:20 http://gnomefreak.youmortals.com feisty Release.gpg [6106B]
Ign http://ubuntu.geole.info feisty-backports/restricted Translation-pt_PT
Atingido http://ubuntu.geole.info feisty Release
Atingido http://security.ubuntu.com feisty-security/main Packages
Obter:21 http://ubuntu.beryl-project.org feisty Release.gpg [191B]
Ign http://www.albertomilone.com binary/ Release.gpg
Ign http://www.albertomilone.com binary/ Translation-pt_PT
Ign http://kubuntu.org feisty Release.gpg
Ign http://kubuntu.org feisty/main Translation-pt_PT
Ign http://kubuntu.org feisty/main Translation-pt_PT
Obter:22 http://kubuntu.org feisty Release.gpg [189B]
Ign http://kubuntu.org feisty/main Translation-pt_PT
Atingido http://kubuntu.org feisty Release
Ign http://janvitus.interfree.it feisty-upure64/experimental-amd64 Translation-pt_PT
Obter:23 http://debs.peadrop.com feisty Release.gpg [189B]
Atingido http://www.mpe.mpg.de ./ Release
Ign http://debs.peadrop.com feisty/all Translation-pt_PT
Atingido http://janvitus.interfree.it feisty-upure64 Release
Err http://janvitus.interfree.it feisty-upure64 Release
  
Atingido http://hendrik.kaju.pri.ee feisty Release
Err http://hendrik.kaju.pri.ee feisty Release
  
Atingido http://archive.canonical.com feisty-commercial/main Packages
Atingido http://deb.opera.com etch Release
Err http://deb.opera.com etch Release
  
Obter:24 http://edevelop.org feisty Release.gpg [189B]
Ign http://edevelop.org feisty/e17 Translation-pt_PT
Ign http://kubuntu.org feisty Release
Ign http://ubuntu.uni-klu.ac.at feisty/uniklu-testing Translation-pt_PT
Obter:25 http://www.linux2go.dk feisty Release [1454B]
Atingido http://ubuntu.uni-klu.ac.at feisty Release
Atingido http://archive.ubuntu.com feisty-proposed/restricted Packages
Obter:26 http://archive.ubuntustudio.org feisty Release.gpg [189B]
Obter:27 http://wine.budgetdedicated.com feisty Release [1007B]
Err http://ubuntu.uni-klu.ac.at feisty Release
  
Ign http://ubuntu.tolero.org feisty Release
Ign http://www.linux2go.dk feisty Release
Ign http://wine.budgetdedicated.com feisty Release
Ign http://archive.ubuntustudio.org feisty/main Translation-pt_PT
Ign http://getswiftfox.com unstable Release.gpg
Atingido http://snapshots.ekiga.net feisty Release
Err http://snapshots.ekiga.net feisty Release
  
Obter:28 http://archive.czessi.net feisty Release [27,9kB]
Obter:29 http://medibuntu.sos-sts.com feisty Release [2195B]
Ign http://medibuntu.sos-sts.com feisty Release
Atingido http://ubuntu.geole.info feisty-backports Release
Atingido http://security.ubuntu.com feisty-security/restricted Packages
Atingido http://security.ubuntu.com feisty-security/main Sources
Atingido http://security.ubuntu.com feisty-security/restricted Sources
Atingido http://security.ubuntu.com feisty-security/universe Packages
Ign http://e17.dunnewind.net feisty/e17 Translation-pt_PT
Atingido http://www.mpe.mpg.de ./ Packages
Ign http://kubuntu.org feisty Release
Atingido http://kubuntu.org feisty Release
Obter:30 http://hendrik.kaju.pri.ee feisty Release [6906B]
Obter:31 http://deb.opera.com etch Release [866B]
Ign http://deb.opera.com etch Release
Obter:32 http://janvitus.interfree.it feisty-upure64 Release [5249B]
Atingido http://archive.ubuntu.com feisty-proposed/main Packages
Atingido http://archive.ubuntu.com feisty-proposed/multiverse Packages
Atingido http://archive.ubuntu.com feisty-proposed/universe Packages
Ign http://ubuntu.beryl-project.org feisty/main Translation-pt_PT
Ign http://wine.budgetdedicated.com feisty/main Packages
Obter:33 http://www.linux2go.dk feisty/main Packages [14B]
Obter:34 http://ubuntu.uni-klu.ac.at feisty Release [11,0kB]
Atingido http://security.ubuntu.com feisty-security/multiverse Packages
Atingido http://security.ubuntu.com feisty-security/restricted Packages
Atingido http://security.ubuntu.com feisty-security/universe Sources
Atingido http://security.ubuntu.com feisty-security/multiverse Sources
Atingido http://security.ubuntu.com feisty-security/restricted Sources
Ign http://ubuntu.tolero.org feisty/main Packages
Ign http://medibuntu.sos-sts.com feisty/free Packages
Ign http://cle.linux.org.tw i386/ Release.gpg
Obter:35 http://ubuntu.geole.info feisty Release [7297B]
Obter:36 http://snapshots.ekiga.net feisty Release [3536B]
Ign http://www.albertomilone.com binary/ Release
Obter:37 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-pt_PT
Ign http://snapshots.ekiga.net feisty Release
Atingido http://kubuntu.org feisty/main Packages
Atingido http://kubuntu.org feisty/main Sources
Atingido http://kubuntu.org feisty/main Packages
Atingido http://kubuntu.org feisty/main Sources
Atingido http://www.mpe.mpg.de ./ Sources
Atingido http://debs.peadrop.com feisty Release
Err http://debs.peadrop.com feisty Release
  
Atingido http://wine.budgetdedicated.com feisty/main Sources
Ign http://janvitus.interfree.it feisty-upure64 Release
Ign http://deb.opera.com etch/non-free Packages
Obter:38 http://www.linux2go.dk feisty/main Sources [14B]
Ign http://archive.czessi.net feisty Release
Atingido http://e17.dunnewind.net feisty Release
Atingido http://edevelop.org feisty Release
Err http://e17.dunnewind.net feisty Release
  
Err http://edevelop.org feisty Release
  
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Ign http://ubuntu.tolero.org feisty/main Sources
Ign http://ubuntu.geole.info feisty Release
Ign http://getswiftfox.com unstable/non-free Translation-pt_PT
Ign http://download.tuxfamily.org feisty/3v1n0 Translation-pt_PT
Atingido http://download.tuxfamily.org feisty Release
Atingido http://ubuntu.beryl-project.org feisty Release
Atingido http://archive.ubuntustudio.org feisty Release
Err http://ubuntu.beryl-project.org feisty Release
  
Err http://archive.ubuntustudio.org feisty Release
  
Ign http://kubuntu.org feisty/main Packages
Ign http://kubuntu.org feisty/main Sources
Ign http://kubuntu.org feisty/main Packages
Ign http://kubuntu.org feisty/main Sources
Obter:39 http://gnomefreak.youmortals.com feisty/main Translation-pt_PT [6106B]
Ign http://kubuntu.org feisty/main Packages
Ign http://kubuntu.org feisty/main Sources
Atingido http://snapshots.ekiga.net feisty/main Packages
Ign http://medibuntu.sos-sts.com feisty/free Packages
Atingido http://wine.budgetdedicated.com feisty/main Packages
Ign http://hendrik.kaju.pri.ee feisty Release
Atingido http://archive.czessi.net feisty/main Packages
Err http://deb.opera.com etch/non-free Packages
  404 Not Found
Atingido http://www.getautomatix.com feisty Release
Err http://www.getautomatix.com feisty Release
  
Atingido http://janvitus.interfree.it feisty-upure64/main-amd64 Packages
Ign http://ubuntu.uni-klu.ac.at feisty Release
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Obter:40 http://ubuntu.geole.info feisty-backports Release [14,0kB]
Atingido http://download.tuxfamily.org feisty Release
Ign http://www.albertomilone.com binary/ Packages
Ign http://kubuntu.org feisty/main Packages
Ign http://kubuntu.org feisty/main Sources
Atingido http://kubuntu.org feisty/main Packages
Atingido http://kubuntu.org feisty/main Sources
Err http://ubuntu.tolero.org feisty/main Packages
  404 Not Found
Obter:41 http://e17.dunnewind.net feisty Release [4797B]
Atingido http://medibuntu.sos-sts.com feisty/free Packages
Atingido http://medibuntu.sos-sts.com feisty/non-free Packages
Atingido http://medibuntu.sos-sts.com feisty/free Sources
Obter:42 http://debs.peadrop.com feisty Release [6970B]
Atingido http://snapshots.ekiga.net feisty/main Sources
Atingido http://hendrik.kaju.pri.ee feisty/screenlets Packages
Atingido http://archive.czessi.net feisty/restricted Packages
Atingido http://archive.czessi.net feisty/universe Packages
Atingido http://archive.czessi.net feisty/multiverse Packages
Atingido http://archive.czessi.net feisty/preview Packages
Atingido http://archive.czessi.net feisty/main Sources
Atingido http://archive.czessi.net feisty/restricted Sources
Atingido http://archive.czessi.net feisty/universe Sources
Atingido http://archive.czessi.net feisty/multiverse Sources
Atingido http://archive.czessi.net feisty/preview Sources
Obter:43 http://edevelop.org feisty Release [4797B]
Ign http://gnomefreak.youmortals.com feisty/main Translation-pt_PT
Obter:44 http://download.tuxfamily.org feisty Release [26,9kB]
Atingido http://ubuntu.uni-klu.ac.at feisty/uniklu Packages
Ign http://ubuntu.geole.info feisty-backports Release
Obter:45 http://archive.ubuntustudio.org feisty Release [1304B]
Ign http://archive.ubuntustudio.org feisty Release
Err http://kubuntu.org feisty/main Packages
  404 Not Found
Err http://kubuntu.org feisty/main Sources
  404 Not Found
Ign http://getswiftfox.com unstable Release
Err http://kubuntu.org feisty/main Packages
  404 Not Found
Err http://kubuntu.org feisty/main Sources
  404 Not Found
Err http://kubuntu.org feisty/main Packages
  404 Not Found
Atingido http://janvitus.interfree.it feisty-upure64/main-amd64 Sources
Atingido http://janvitus.interfree.it feisty-upure64/experimental-amd64 Packages
Atingido http://janvitus.interfree.it feisty-upure64/experimental-amd64 Sources
Obter:46 http://www.getautomatix.com feisty Release [6738B]
Atingido http://medibuntu.sos-sts.com feisty/non-free Sources
Atingido http://medibuntu.sos-sts.com feisty/free Packages
Atingido http://medibuntu.sos-sts.com feisty/non-free Packages
Atingido http://medibuntu.sos-sts.com feisty/free Sources
Err http://ubuntu.tolero.org feisty/main Sources
  404 Not Found
Ign http://elisa.fluendo.com feisty/main Translation-pt_PT
Atingido http://hendrik.kaju.pri.ee feisty/screenlets Sources
Ign http://e17.dunnewind.net feisty Release
Atingido http://ubuntu.geole.info feisty/universe Packages
Atingido http://ubuntu.geole.info feisty/multiverse Packages
Atingido http://ubuntu.geole.info feisty/universe Sources
Atingido http://ubuntu.geole.info feisty/multiverse Sources
Err http://kubuntu.org feisty/main Sources
  404 Not Found
Obter:47 http://ubuntu.beryl-project.org feisty Release [2965B]
Err http://kubuntu.org feisty/main Packages
  404 Not Found
Err http://kubuntu.org feisty/main Sources
  404 Not Found
Ign http://ubuntu.beryl-project.org feisty Release
Err http://www.albertomilone.com binary/ Packages
  404 Not Found
Atingido http://ubuntu.uni-klu.ac.at feisty/uniklu-intern Packages
Atingido http://ubuntu.uni-klu.ac.at feisty/uniklu-testing Packages
Atingido http://ubuntu.uni-klu.ac.at feisty/uniklu Sources
Atingido http://ubuntu.uni-klu.ac.at feisty/uniklu-intern Sources
Atingido http://ubuntu.uni-klu.ac.at feisty/uniklu-testing Sources
Atingido http://medibuntu.sos-sts.com feisty/non-free Sources
Obter:48 http://gnomefreak.youmortals.com feisty Release [6106B]
Ign http://debs.peadrop.com feisty Release
Atingido http://ubuntu.geole.info feisty-backports/main Packages
Atingido http://ubuntu.geole.info feisty-backports/universe Packages
Atingido http://ubuntu.geole.info feisty-backports/multiverse Packages
Atingido http://ubuntu.geole.info feisty-backports/restricted Packages
Atingido http://ubuntu.geole.info feisty-backports/main Sources
Ign http://edevelop.org feisty Release
Atingido http://elisa.fluendo.com feisty Release
Ign http://www.getautomatix.com feisty Release
Err http://elisa.fluendo.com feisty Release
  
Atingido http://e17.dunnewind.net feisty/e17 Packages
Ign http://archive.ubuntustudio.org feisty/main Packages
Atingido http://ubuntu.beryl-project.org feisty/main Packages
Ign http://getswiftfox.com unstable/non-free Packages
Atingido http://ubuntu.geole.info feisty-backports/universe Sources
Atingido http://ubuntu.geole.info feisty-backports/multiverse Sources
Atingido http://ubuntu.geole.info feisty-backports/restricted Sources
Ign http://gnomefreak.youmortals.com feisty Release
Obter:49 http://elisa.fluendo.com feisty Release [1363B]
Ign http://elisa.fluendo.com feisty Release
Atingido http://e17.dunnewind.net feisty/e17 Sources
Ign http://download.tuxfamily.org feisty Release
Atingido http://www.getautomatix.com feisty/main Packages
Ign http://debs.peadrop.com feisty/all Packages
Atingido http://edevelop.org feisty/e17 Packages
Obter:50 http://download.tuxfamily.org feisty Release [14,2kB]
Atingido http://archive.ubuntustudio.org feisty/main Sources
Ign http://cle.linux.org.tw i386/ Translation-pt_PT
Atingido http://getswiftfox.com unstable/non-free Packages
Obter:51 http://gnomefreak.youmortals.com feisty/main Packages [6106B]
Atingido http://ubuntu.beryl-project.org feisty/main Sources
Atingido http://debs.peadrop.com feisty/all Sources
Ign http://download.tuxfamily.org feisty Release
Atingido http://edevelop.org feisty/e17 Sources
Err http://gnomefreak.youmortals.com feisty/main Packages
  Sub-processo bzip2 retornou um código de erro (2)
Err http://archive.ubuntustudio.org feisty/main Packages
  404 Not Found
Atingido http://download.tuxfamily.org feisty/all Packages
Atingido http://download.tuxfamily.org feisty/all Sources
Ign http://elisa.fluendo.com feisty/main Packages
Err http://debs.peadrop.com feisty/all Packages
  404 Not Found
Obter:52 http://pt.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://pt.archive.ubuntu.com feisty/main Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty/restricted Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty/universe Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty/multiverse Translation-pt_PT
Obter:53 http://pt.archive.ubuntu.com feisty-proposed Release.gpg [191B]
Ign http://pt.archive.ubuntu.com feisty-proposed/main Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-proposed/restricted Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-proposed/universe Translation-pt_PT
Obter:54 http://gnomefreak.youmortals.com feisty/main Sources [6106B]
Ign http://pt.archive.ubuntu.com feisty-proposed/multiverse Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-proposed/restricted Translation-pt_PT
Obter:55 http://pt.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://pt.archive.ubuntu.com feisty-updates/main Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-updates/restricted Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-updates/universe Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-updates/multiverse Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-updates/restricted Translation-pt_PT
Obter:56 http://pt.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://pt.archive.ubuntu.com feisty-backports/main Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-backports/restricted Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-backports/universe Translation-pt_PT
Ign http://pt.archive.ubuntu.com feisty-backports/multiverse Translation-pt_PT
Atingido http://pt.archive.ubuntu.com feisty Release
Err http://gnomefreak.youmortals.com feisty/main Sources
  Sub-processo bzip2 retornou um código de erro (2)
Atingido http://download.tuxfamily.org feisty/3v1n0 Packages
Atingido http://download.tuxfamily.org feisty/3v1n0 Sources
Atingido http://pt.archive.ubuntu.com feisty-proposed Release
Atingido http://pt.archive.ubuntu.com feisty-updates Release
Atingido http://pt.archive.ubuntu.com feisty-backports Release
Atingido http://pt.archive.ubuntu.com feisty/main Packages
Atingido http://pt.archive.ubuntu.com feisty/restricted Packages
Atingido http://pt.archive.ubuntu.com feisty/main Sources
Atingido http://pt.archive.ubuntu.com feisty/restricted Sources
Atingido http://pt.archive.ubuntu.com feisty/universe Packages
Atingido http://pt.archive.ubuntu.com feisty/multiverse Packages
Atingido http://pt.archive.ubuntu.com feisty/universe Sources
Atingido http://pt.archive.ubuntu.com feisty/multiverse Sources
Atingido http://pt.archive.ubuntu.com feisty/restricted Sources
Err http://elisa.fluendo.com feisty/main Packages
  404 Not Found
Ign http://cle.linux.org.tw i386/ Release
Atingido http://pt.archive.ubuntu.com feisty-proposed/main Packages
Atingido http://pt.archive.ubuntu.com feisty-proposed/restricted Packages
Atingido http://pt.archive.ubuntu.com feisty-proposed/main Sources
Atingido http://pt.archive.ubuntu.com feisty-proposed/restricted Sources
Atingido http://pt.archive.ubuntu.com feisty-proposed/universe Packages
Atingido http://pt.archive.ubuntu.com feisty-proposed/multiverse Packages
Atingido http://pt.archive.ubuntu.com feisty-proposed/restricted Packages
Atingido http://pt.archive.ubuntu.com feisty-proposed/universe Sources
Atingido http://pt.archive.ubuntu.com feisty-proposed/multiverse Sources
Atingido http://pt.archive.ubuntu.com feisty-proposed/restricted Sources
Atingido http://pt.archive.ubuntu.com feisty-updates/main Packages
Atingido http://pt.archive.ubuntu.com feisty-updates/restricted Packages
Atingido http://pt.archive.ubuntu.com feisty-updates/main Sources
Atingido http://pt.archive.ubuntu.com feisty-updates/restricted Sources
Atingido http://pt.archive.ubuntu.com feisty-updates/universe Packages
Atingido http://pt.archive.ubuntu.com feisty-updates/multiverse Packages
Atingido http://pt.archive.ubuntu.com feisty-updates/restricted Packages
Atingido http://pt.archive.ubuntu.com feisty-updates/universe Sources
Atingido http://pt.archive.ubuntu.com feisty-updates/multiverse Sources
Atingido http://pt.archive.ubuntu.com feisty-updates/restricted Sources
Atingido http://pt.archive.ubuntu.com feisty-backports/main Packages
Atingido http://pt.archive.ubuntu.com feisty-backports/restricted Packages
Atingido http://pt.archive.ubuntu.com feisty-backports/universe Packages
Atingido http://pt.archive.ubuntu.com feisty-backports/multiverse Packages
Atingido http://pt.archive.ubuntu.com feisty-backports/main Sources
Atingido http://pt.archive.ubuntu.com feisty-backports/restricted Sources
Atingido http://pt.archive.ubuntu.com feisty-backports/universe Sources
Atingido http://pt.archive.ubuntu.com feisty-backports/multiverse Sources
Ign http://files.beep-media-player.org feisty Release.gpg
Ign http://files.beep-media-player.org feisty/main Translation-pt_PT
Ign http://files.beep-media-player.org feisty/testing Translation-pt_PT
Ign http://files.beep-media-player.org feisty Release
Ign http://cle.linux.org.tw i386/ Packages
Ign http://files.beep-media-player.org feisty/main Packages
Ign http://files.beep-media-player.org feisty/testing Packages
Ign http://files.beep-media-player.org feisty/main Sources
Ign http://files.beep-media-player.org feisty/testing Sources
Err http://files.beep-media-player.org feisty/main Packages
  404 Not Found
Err http://files.beep-media-player.org feisty/testing Packages
  404 Not Found
Err http://files.beep-media-player.org feisty/main Sources
  404 Not Found
Err http://files.beep-media-player.org feisty/testing Sources
  404 Not Found
Obter:57 ftp://ftp.gwdg.de  Release.gpg [189B]
Obter:58 ftp://ftp.gwdg.de  Translation-pt_PT
Err http://cle.linux.org.tw i386/ Packages
  404 Not Found
Ign ftp://ftp.gwdg.de  Translation-pt_PT
Atingido ftp://ftp.gwdg.de  Release
Err ftp://ftp.gwdg.de  Release
  
Obter:59 ftp://ftp.gwdg.de  Release [868B]
Ign ftp://ftp.gwdg.de  Release
Atingido ftp://ftp.gwdg.de  Packages
Atingido ftp://ftp.gwdg.de  Sources

``` 

And this are the errors (only of repository reaching and packages not available):

```

Falha ao obter http://ubuntu.tolero.org/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://deb.opera.com/opera/dists/etch/non-free/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://ubuntu.tolero.org/dists/feisty/main/source/Sources.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/koffice-latest/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/koffice-latest/dists/feisty/main/source/Sources.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz  404 Not Found
Falha ao obter http://www.albertomilone.com/drivers/feisty/latest/32bit/binary/Packages.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://kubuntu.org/packages/amarok-latest/dists/feisty/main/source/Sources.gz  404 Not Found
Falha ao obter http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://gnomefreak.youmortals.com/mozilla-testing/dists/feisty/main/binary-amd64/Packages.bz2  Sub-processo bzip2 retornou um código de erro (2)
Falha ao obter http://gnomefreak.youmortals.com/mozilla-testing/dists/feisty/main/source/Sources.bz2  Sub-processo bzip2 retornou um código de erro (2)
Falha ao obter http://debs.peadrop.com/dists/feisty/all/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://elisa.fluendo.com/packages/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://cle.linux.org.tw/candyz/Ubuntu/feisty/i386/Packages.gz  404 Not Found
Falha ao obter http://files.beep-media-player.org/packages/ubuntu/dists/feisty/main/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://files.beep-media-player.org/packages/ubuntu/dists/feisty/testing/binary-amd64/Packages.gz  404 Not Found
Falha ao obter http://files.beep-media-player.org/packages/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found
Falha ao obter http://files.beep-media-player.org/packages/ubuntu/dists/feisty/testing/source/Sources.gz  404 Not Found

```

Also if you read the comments on his page, you will see lots of people asking for help, because of apt-get update errors. 

(Note: I have the portuguese version of ubuntu, since I'm from Portugal.)

---

### Post by skymera on 2007-09-18
why spam this?

I DIDNT make the list.

i merely posted for it.

if you got any problem dont speak to me, speak to the dud ethat made it.

plus i get more Hits thasn Ignores.

and this is for 32bit. 64bit isnt supported very well...

better, dont use it if you are thjat bothered.

---

### Post by Coyote21 on 2007-10-01
> **skymera said:**
> why spam this?

I DIDNT make the list.

i merely posted for it.

if you got any problem dont speak to me, speak to the dud ethat made it.

plus i get more Hits thasn Ignores.

and this is for 32bit. 64bit isnt supported very well...

better, dont use it if you are thjat bothered.

Sorry, i didn't mean to offend anyone... I was only trying to post my experience on that repository list

---

### Post by skymera on 2007-10-02
you could havw saud in a more polite way :wink:

---

### Post by por100pre1 on 2007-10-02
It is possible that some of those repositories have been moved, are getting maintenance or are no longer working. Please keep in mind that adding many repositories without any research and further consideration is very risky. You can get many updates that can break important packages in your system. 

My suggestion: keep the list but don't add any repository unless specifically intend to install packages from that repository. Then you can add the GPG key you may need.

---

### Post by sagara on 2007-11-06
Am I the only soul right now that can't get updates from trevino's repository for my compiz fusion??
Is like he changed the public key and im the only one who doesn't know about this...

I keep getting the error
```

W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

```
That key does NOT exist I tell.  I haven't been able to get it to work no matter what I try.  I have the two keys that he mentions on his page but it still doesn't work (81836EBF - DD800CD9).

Can anybody show me the light?

---

### Post by FuturePilot on 2007-11-06
That's happening to me too. It started the day Gutsy came out. I'm wondering if the key expired or something.

---

### Post by sagara on 2007-11-06
I found this code from a french forum
```
wget -q http://download.tuxfamily.org/syzygy42/reacocard.asc -O- | sudo apt-key add -
```
It seems to have fixed the NO_PUBKEY problem however according to *apt-get update* there is no update for compiz fusion... I find that odd since I haven't updated for a month already...

---

