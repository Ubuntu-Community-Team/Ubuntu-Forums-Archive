---
title: "PySolfc / Python error"
date: 2022-04-25
forum: General Help
---

### Post by heroquestelf on 2022-04-25
I just upgraded my Dell Precision M4600 to Jammy Jellyfish, and I'm having a weird problem. My favorite card game, Pysol, won't work. I have installed it, uninstalled it, and reinstalled it. I even tried to go to the source code and compile it myself (which was a massive failure). I was wondering if I could get some assistance. 

When I type in "pysolfc" I get the following error:

```
Traceback (most recent call last):
  File "/usr/games/pysolfc", line 36, in <module>
    from pysollib.main import main  # noqa: E402,I202
  File "/usr/share/games/pysolfc/pysollib/main.py", line 30, in <module>
    from pysollib.app import Application
  File "/usr/share/games/pysolfc/pysollib/app.py", line 32, in <module>
    from pysollib.images import Images, SubsampledImages
  File "/usr/share/games/pysolfc/pysollib/images.py", line 28, in <module>
    from pysollib.pysoltk import copyImage, createBottom, createImage, loadImage
  File "/usr/share/games/pysolfc/pysollib/pysoltk.py", line 35, in <module>
    from pysollib.tile.tkhtml import *  # noqa: F401,F403
  File "/usr/share/games/pysolfc/pysollib/tile/tkhtml.py", line 29, in <module>
    from pysollib.ui.tktile.tkhtml import Base_HTMLViewer
  File "/usr/share/games/pysolfc/pysollib/ui/tktile/tkhtml.py", line 24, in <module>
    import formatter
ModuleNotFoundError: No module named 'formatter'

```

I tried to install "formatter", but it gave me the following error: 

```
Defaulting to user installation because normal site-packages is not writeable
Collecting formatter
  Using cached formatter-1.0.3.tar.gz (17 kB)
  Preparing metadata (setup.py) ... error
  error: subprocess-exited-with-error
  
  × python setup.py egg_info did not run successfully.
  &#9474; exit code: 1
  &#9584;&#9472;> [10 lines of output]
      Traceback (most recent call last):
        File "<string>", line 2, in <module>
        File "<pip-setuptools-caller>", line 34, in <module>
        File "/tmp/pip-install-nfumu3h0/formatter_982927e4219b4ecba7c9deb9352e1012/setup.py", line 2, in <module>
          import formatter as metadata
        File "/tmp/pip-install-nfumu3h0/formatter_982927e4219b4ecba7c9deb9352e1012/formatter/__init__.py", line 9, in <module>
          from .formatter import Formatter
        File "/tmp/pip-install-nfumu3h0/formatter_982927e4219b4ecba7c9deb9352e1012/formatter/formatter.py", line 4, in <module>
          from cStringIO import StringIO
      ModuleNotFoundError: No module named 'cStringIO'
      [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
&#9584;&#9472;> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.

```

I have installed python2:i386, python2-dev, & python 2. I installed python-dev-is-python3. I tried to install unroll & easy_install and both failed. I also tried to install setuptools and that wouldn't work either.

I'm pretty good navigating Ubuntu's native environment, but my python skills are weak. Can anyone assist?

---

### Post by Topsiho on 2022-04-25
Today Python2 is obsolete and only Python**3 **is installed in Ubuntu. I think your pysol is compiled for Python2, and therefore doesn't work as expected. Try to reinstall pysol(c?) from the repositories. Good luck!

---

### Post by Holger_Gehrke on 2022-04-25
The problem is the removal of the formatter module from python after version 3.10. The problem was fixed in pysolfc 2.14 (current version is 2.15) but that isn't in the repositories - the pysol in the repositories is version 2.6. The git-repository for pysolfc is at [https://github.com/shlomif/PySolFC](https://github.com/shlomif/PySolFC) and I'm going to try and set it up on my system and tell you whether I got it to work.

Holger

---

### Post by heroquestelf on 2022-04-25
If you are able to get it to work, please let me know. I've never compiled an app by myself before. I don't know how to do it, but I'm eager to learn if you will humor me and teach me how.

---

### Post by Holger_Gehrke on 2022-04-25
There's actually no compiling involved since Python is an interpreted language (well, mostly; there's byte code which the python source can be compiled to ...). Here's what I did:


[LIST]
[*]I removed the pysolfc and pysolfc-cardsets packages (sudo apt purge pysolfc pysolfc-cardsets). 
[*]After doing this several packages needed by pysolfc where marked for automatic removal and I marked them as manually installed because I assume that the pysolfc I'm going to install will need them (sudo apt-mark manual libmodplug1 libopusfile0 libportmidi0 libsdl2-image-2.0-0 libsdl2-mixer-2.0-0 libsdl2-ttf-2.0-0 python3-configobj python3-pygame python3-random2). 
[*]Next I installed some packages which are listed as necessary in the instructions (sudo apt-get install cpanminus make perl python3-setuptools python3-tk). I also installed git for getting the sources (sudo apt install git). 
[*]Then I ran 'git clone [https://github.com/shlomif/PySolFC.git](https://github.com/shlomif/PySolFC.git)'. This creates a directory PySolFC in the current working directory and downloads  the code into it. 
[*]Next I downloaded the cardsets for PySolFC from the sourceforge page ([https://sourceforge.net/projects/pysolfc/files/PySolFC-Cardsets/](https://sourceforge.net/projects/pysolfc/files/PySolFC-Cardsets/)). 
[*]At this point I tried running the tests (gmake test) and found something was seriously wrong. Since the errors mentioned missing Python modules named pycotap and pysol_cards I installed pip3 (**P**ython **I**nstaller for **P**ackages, version for Python**3**;'sudo apt install python3-pip') and ran 'pip3 install pycotap' and 'pip3 install pysol_cards'. 
[*]On re-running 'gmake test' I find that there are two test still failing. These test are being run from Perl-modules. Getting these to run is a pain in the ... . If you really want you can run 'cpan' to set up a user local storage for Perl modules, open a new terminal (setting up the storage puts some variable in ~/.bashrc and you need to start a new shell for these variables to become visible) and run 'cpan Test::Code::TidyAll' and 'cpan Code::TidyAll::Plugin::Flake8' and 'cpan Test::TrailingSpace' and wait about an hour for various modules to be compiled. Really, don't bother, these are checks for correctly formatted code. 
[*]The next step in the instructions is running 'gmake rules', which should find all the html-files with game rules and put them in the right places. It will complain about some rules being AWOL, but it will finish. 
[*]Next step: unpack the cards. First create a symbolic link (ln -s data/images images) then run 'tar -xvf ~/Downloads/PySolFC-Cardsets-2.1.tar.bz2'. You will obviously have to give the name and location of the cards-archive you downloaded in that command ... 
[*]Now create a directory for PysolFC's configuration data (mkdir -p ~/.PySolFC). 
[*]If - like me - you used to have PySolFC running previously and already had a configuration directory then removing the cardsets directory from there is necessary (rm -rf ~/.Pysolfc/cardsets). 
[*]Link the unpacked cardsets into the configuration directory (ln -s "$(pwd)/PySolFC-Cardsets-2.1/" ~/.PySolFC/cardsets). Again, you might have to give a different name for the cardset. 
[*]Now you can start PySolFC with 'python3 pysol.py'. 
[*]As a finishing touch create a desktop-file for it and put it in '~/.local/share/applications'. 
[/LIST]

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Name=Python Solitaire, Fan Club Edition
Comment=Comprehensive collection of solitaire games
Icon=/home/holgeh/PySolFC/data/images/icons/48x48/pysol.png
Exec=python3 pysol.py
Path=/home/holgeh/PySolFC
NoDisplay=false
Categories=Game
StartupNotify=true
Terminal=false

```

You will have to change the paths in that, obviously.

Holger

---

### Post by dragonfly41 on 2022-04-25
I don't play solitaire .. but possibly here is another approach of interest ..

[https://community.wolfram.com/groups/-/m/t/1609558](https://community.wolfram.com/groups/-/m/t/1609558)

You can install free version of wolframscript in Ubuntu.

Wolfram is a general purpose mathematical engine. Many uses.

Wolfram kernel also runs in Jupyter notebooks.

---

### Post by heroquestelf on 2022-04-26
Okay, I was with you until you got to the 'gmake rules' command. Following your instructions got me the following result. Maybe you can tell me where I went wrong.
```

~$ gmake test
gmake: *** No rule to make target 'test'.  Stop.
~$ gmake rules
gmake: *** No rule to make target 'rules'.  Stop.
~$ ln -s data/images images
ln: failed to create symbolic link 'images': File exists

```

---

### Post by Holger_Gehrke on 2022-04-26
Ooops. Left out a small but important step that seemed obvious to me: change into the directory with the downloaded source code. A simple 'cd PySolFC' should take care of that. Then your current working directory should be the one with the 'Makefile' in it and gmake will be able to find those targets.

Holger

---

### Post by heroquestelf on 2022-04-26
Okay, so here are my results. It looked like I was having issues, so I currently have your three cpan commands running. I can post the results of those as they come. 

This is from the 'gmake test' command

```

Test Summary Report
-------------------
tests/style/tidyall.t                                                         (Wstat: 512 Tests: 0 Failed: 0)
  Non-zero exit status: 2
  Parse errors: No plan found in TAP output
tests/t/tap_unittests.py                                                      (Wstat: 0 Tests: 16 Failed: 4)
  Failed tests:  1-2, 6, 16
tests/individually-importing/import_v3_pysollib.app.py                        (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.customgame.py                 (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.game.__init__.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.game.dump.py                  (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.__init__.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.acesandkings.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.acesup.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.algerian.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.auldlangsyne.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.bakersdozen.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.bakersgame.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.beleagueredcastle.py    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.bisley.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.bisley13.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.braid.py                (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.bristol.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.buffalobill.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.calculation.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.camelot.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.canfield.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.capricieuse.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.crossword.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.curdsandwhey.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.daddylonglegs.py        (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.dieboesesieben.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.diplomat.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.doublets.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.eiffeltower.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.fan.py                  (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.fortythieves.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.freecell.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.glenwood.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.golf.py                 (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.grandduchess.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.grandfathersclock.py    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.gypsy.py                (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.harp.py                 (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.headsandtails.py        (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.hitormiss.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.katzenschwanz.py        (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.klondike.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.knockout.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.labyrinth.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.larasgame.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.mahjongg.__init__.py    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.mahjongg.mahjongg.py    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.mahjongg.mahjongg1.py   (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.mahjongg.mahjongg2.py   (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.mahjongg.mahjongg3.py   (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.mahjongg.shisensho.py   (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.matriarchy.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.montana.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.montecarlo.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.moojub.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.napoleon.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.needle.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.numerica.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.osmosis.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.parallels.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.pasdedeux.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.picturegallery.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.pileon.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.precedence.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.pushpin.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.pyramid.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.royalcotillion.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.royaleast.py            (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.sanibel.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.siebenbisas.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.simplex.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.__init__.py     (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.cribbage.py     (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.hanoi.py        (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.lightsout.py    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.memory.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.pegged.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.poker.py        (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.special.tarock.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.spider.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.sthelena.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.sultan.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.takeaway.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.terrace.py              (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.threepeaks.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.tournament.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.__init__.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.dashavatara.py    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.hanafuda.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.hanafuda1.py      (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.hanafuda_common.py (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.hexadeck.py       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.larasgame.py      (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.matrix.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.mughal.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.ultra.tarock.py         (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.unionsquare.py          (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.wavemotion.py           (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.windmill.py             (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.yukon.py                (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.games.zodiac.py               (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.main.py                       (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
tests/individually-importing/import_v3_pysollib.options.py                    (Wstat: 256 Tests: 0 Failed: 0)
  Non-zero exit status: 1
  Parse errors: Bad plan.  You planned 1 tests but ran 0.
Files=202, Tests=113, 18 wallclock secs ( 0.85 usr  0.47 sys + 14.27 cusr  2.50 csys = 18.09 CPU)
Result: FAIL
gmake: *** [Makefile:69: test] Error 1

```

And this is from 'gmake rules'
```

$ gmake rules
cd html-src && ./gen-html.py
Traceback (most recent call last):
  File "/home/jonathan/PySolFC/html-src/./gen-html.py", line 19, in <module>
    import pysollib.games  # noqa: E402,F402,I100,I202
  File "/home/jonathan/PySolFC/pysollib/games/__init__.py", line 23, in <module>
    from . import acesandkings  # noqa: F401
  File "/home/jonathan/PySolFC/pysollib/games/acesandkings.py", line 24, in <module>
    from pysollib.game import Game
  File "/home/jonathan/PySolFC/pysollib/game/__init__.py", line 30, in <module>
    import attr
ModuleNotFoundError: No module named 'attr'
gmake: *** [Makefile:36: rules] Error 1

```

---

### Post by heroquestelf on 2022-04-26
Here is my cpan:tidyall results.

```

Test Summary Report
-------------------
t/waitpid-conflict.t    (Wstat: 0 Tests: 2 Failed: 0)
  TODO passed:   1-2
t/waitpid-waitonechild.t (Wstat: 0 Tests: 3 Failed: 0)
  TODO passed:   1-3
Files=12, Tests=28, 70 wallclock secs ( 0.07 usr  0.02 sys +  1.89 cusr  0.63 csys =  2.61 CPU)
Result: PASS
  YANICK/Parallel-ForkManager-2.02.tar.gz
  /usr/bin/make test -- OK
Running make install for YANICK/Parallel-ForkManager-2.02.tar.gz
Manifying 2 pod documents
Appending installation info to /usr/local/lib/x86_64-linux-gnu/perl/5.34.0/perllocal.pod
  YANICK/Parallel-ForkManager-2.02.tar.gz
  /usr/bin/make install  -- OK

```

Here is my cpan Plugin flake8 results

```

Test Summary Report
-------------------
t/waitpid-conflict.t    (Wstat: 0 Tests: 2 Failed: 0)
  TODO passed:   1-2
t/waitpid-waitonechild.t (Wstat: 0 Tests: 3 Failed: 0)
  TODO passed:   1-3
Files=12, Tests=28, 70 wallclock secs ( 0.06 usr  0.03 sys +  1.88 cusr  0.56 csys =  2.53 CPU)
Result: PASS
  YANICK/Parallel-ForkManager-2.02.tar.gz
  /usr/bin/make test -- OK
Running make install for YANICK/Parallel-ForkManager-2.02.tar.gz
Manifying 2 pod documents
Installing /usr/local/share/perl/5.34.0/Parallel/ForkManager.pm
Installing /usr/local/share/perl/5.34.0/Parallel/ForkManager/Child.pm
Installing /usr/local/man/man3/Parallel::ForkManager.3pm
Installing /usr/local/man/man3/Parallel::ForkManager::Child.3pm
Appending installation info to /usr/local/lib/x86_64-linux-gnu/perl/5.34.0/perllocal.pod
  YANICK/Parallel-ForkManager-2.02.tar.gz
  /usr/bin/make install  -- OK
  SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
  Has already been unwrapped into directory /root/.cpan/build/Code-TidyAll-Plugin-Flake8-0.4.0-0
  SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
  Has already been prepared
Running Build for S/SH/SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
Building Code-TidyAll-Plugin-Flake8
  SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
  ./Build -- OK
Running Build test for SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
t/00-compile.t .. ok   
All tests successful.
Files=1, Tests=1,  0 wallclock secs ( 0.02 usr  0.00 sys +  0.18 cusr  0.03 csys =  0.23 CPU)
Result: PASS
  SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
  ./Build test -- OK
Running Build install for SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
Building Code-TidyAll-Plugin-Flake8
Installing /usr/local/share/perl/5.34.0/Code/TidyAll/Plugin/Flake8.pm
Installing /usr/local/man/man3/Code::TidyAll::Plugin::Flake8.3pm
  SHLOMIF/Code-TidyAll-Plugin-Flake8-0.4.0.tar.gz
  ./Build install  -- OK

```

And here is the final test

```

~$ cpan Test::TrailingSpace
Loading internal logger. Log::Log4perl recommended for better logging

CPAN.pm requires configuration, but most of it can be done automatically.
If you answer 'no' below, you will enter an interactive dialog for each
configuration option instead.

Would you like to configure as much as possible automatically? [yes] 

Warning: You do not have write permission for Perl library directories.

To install modules, you need to configure a local Perl library directory or
escalate your privileges.  CPAN can help you by bootstrapping the local::lib
module or by configuring itself to use 'sudo' (if available).  You may also
resolve this problem manually if you need to customize your setup.

What approach do you want?  (Choose 'local::lib', 'sudo' or 'manual')
 [local::lib] sudo
Fetching with LWP:
http://www.cpan.org/authors/01mailrc.txt.gz
Reading '/home/jonathan/.cpan/sources/authors/01mailrc.txt.gz'
............................................................................DONE
Fetching with LWP:
http://www.cpan.org/modules/02packages.details.txt.gz
Reading '/home/jonathan/.cpan/sources/modules/02packages.details.txt.gz'
  Database was generated on Tue, 26 Apr 2022 13:55:39 GMT
.............
  New CPAN.pm version (v2.34) available.
  [Currently running version is v2.28]
  You might want to try
    install CPAN
    reload cpan
  to both upgrade CPAN.pm and run the new version without leaving
  the current session.


...............................................................DONE
Fetching with LWP:
http://www.cpan.org/modules/03modlist.data.gz
Reading '/home/jonathan/.cpan/sources/modules/03modlist.data.gz'
DONE
Writing /home/jonathan/.cpan/Metadata
Running install for module 'Test::TrailingSpace'
Fetching with LWP:
http://www.cpan.org/authors/id/S/SH/SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
Fetching with LWP:
http://www.cpan.org/authors/id/S/SH/SHLOMIF/CHECKSUMS
Checksum for /home/jonathan/.cpan/sources/authors/id/S/SH/SHLOMIF/Test-TrailingSpace-0.0601.tar.gz ok
'YAML' not installed, will not store persistent state
Configuring S/SH/SHLOMIF/Test-TrailingSpace-0.0601.tar.gz with Build.PL
Checking prerequisites...
  requires:
    !  File::Find::Object::Rule is not installed
  test_requires:
    !  File::TreeCreate is not installed

ERRORS/WARNINGS FOUND IN PREREQUISITES.  You may wish to install the versions
of the modules indicated above before proceeding with this installation

Created MYMETA.yml and MYMETA.json
Creating new 'Build' script for 'Test-TrailingSpace' version '0.0601'
  SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
  /usr/bin/perl Build.PL --installdirs site -- OK
Running Build for S/SH/SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
---- Unsatisfied dependencies detected during ----
---- SHLOMIF/Test-TrailingSpace-0.0601.tar.gz ----
    File::Find::Object::Rule [requires]
    File::TreeCreate [build_requires]
Running install for module 'File::Find::Object::Rule'
Fetching with LWP:
http://www.cpan.org/authors/id/S/SH/SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
Checksum for /home/jonathan/.cpan/sources/authors/id/S/SH/SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz ok
Configuring S/SH/SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz with Build.PL
Checking prerequisites...
  requires:
    !  File::Find::Object is not installed
  test_requires:
    !  File::TreeCreate is not installed

ERRORS/WARNINGS FOUND IN PREREQUISITES.  You may wish to install the versions
of the modules indicated above before proceeding with this installation

Created MYMETA.yml and MYMETA.json
Creating new 'Build' script for 'File-Find-Object-Rule' version '0.0313'
  SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
  /usr/bin/perl Build.PL --installdirs site -- OK
Running Build for S/SH/SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
----   Unsatisfied dependencies detected during  ----
---- SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz ----
    File::Find::Object [requires]
    File::TreeCreate [build_requires]
Running install for module 'File::Find::Object'
Fetching with LWP:
http://www.cpan.org/authors/id/S/SH/SHLOMIF/File-Find-Object-0.3.6.tar.gz
Checksum for /home/jonathan/.cpan/sources/authors/id/S/SH/SHLOMIF/File-Find-Object-0.3.6.tar.gz ok
Configuring S/SH/SHLOMIF/File-Find-Object-0.3.6.tar.gz with Build.PL
Checking prerequisites...
  test_requires:
    !  File::TreeCreate is not installed

ERRORS/WARNINGS FOUND IN PREREQUISITES.  You may wish to install the versions
of the modules indicated above before proceeding with this installation

Created MYMETA.yml and MYMETA.json
Creating new 'Build' script for 'File-Find-Object' version '0.3.6'
  SHLOMIF/File-Find-Object-0.3.6.tar.gz
  /usr/bin/perl Build.PL --installdirs site -- OK
Running Build for S/SH/SHLOMIF/File-Find-Object-0.3.6.tar.gz
---- Unsatisfied dependencies detected during ----
----   SHLOMIF/File-Find-Object-0.3.6.tar.gz  ----
    File::TreeCreate [build_requires]
Running install for module 'File::TreeCreate'
Fetching with LWP:
http://www.cpan.org/authors/id/S/SH/SHLOMIF/File-TreeCreate-0.0.1.tar.gz
Checksum for /home/jonathan/.cpan/sources/authors/id/S/SH/SHLOMIF/File-TreeCreate-0.0.1.tar.gz ok
Configuring S/SH/SHLOMIF/File-TreeCreate-0.0.1.tar.gz with Build.PL
Created MYMETA.yml and MYMETA.json
Creating new 'Build' script for 'File-TreeCreate' version '0.0.1'
  SHLOMIF/File-TreeCreate-0.0.1.tar.gz
  /usr/bin/perl Build.PL --installdirs site -- OK
Running Build for S/SH/SHLOMIF/File-TreeCreate-0.0.1.tar.gz
Building File-TreeCreate
  SHLOMIF/File-TreeCreate-0.0.1.tar.gz
  ./Build -- OK
Running Build test for SHLOMIF/File-TreeCreate-0.0.1.tar.gz
t/00-compile.t ... ok   
t/tree-create.t .. ok     
All tests successful.
Files=2, Tests=23,  0 wallclock secs ( 0.02 usr  0.00 sys +  0.18 cusr  0.03 csys =  0.23 CPU)
Result: PASS
  SHLOMIF/File-TreeCreate-0.0.1.tar.gz
  ./Build test -- OK
Running Build install for SHLOMIF/File-TreeCreate-0.0.1.tar.gz
[sudo] password for jonathan: 
Building File-TreeCreate
Installing /usr/local/share/perl/5.34.0/File/TreeCreate.pm
Installing /usr/local/man/man3/File::TreeCreate.3pm
  SHLOMIF/File-TreeCreate-0.0.1.tar.gz
  sudo ./Build install  -- OK
  SHLOMIF/File-Find-Object-0.3.6.tar.gz
  Has already been unwrapped into directory /home/jonathan/.cpan/build/File-Find-Object-0.3.6-0
  SHLOMIF/File-Find-Object-0.3.6.tar.gz
  Has already been prepared
Running Build for S/SH/SHLOMIF/File-Find-Object-0.3.6.tar.gz
Building File-Find-Object
  SHLOMIF/File-Find-Object-0.3.6.tar.gz
  ./Build -- OK
Running Build test for SHLOMIF/File-Find-Object-0.3.6.tar.gz
t/00-compile.t ........ ok   
t/01ffo.t ............. ok   
t/02tree-create.t ..... ok     
t/03traverse.t ........ ok     
t/04destroy.t ......... ok   
t/05prune.t ........... ok   
t/06trailing-slash.t .. ok   
All tests successful.
Files=7, Tests=83,  1 wallclock secs ( 0.04 usr  0.02 sys +  0.63 cusr  0.07 csys =  0.76 CPU)
Result: PASS
  SHLOMIF/File-Find-Object-0.3.6.tar.gz
  ./Build test -- OK
Running Build install for SHLOMIF/File-Find-Object-0.3.6.tar.gz
Building File-Find-Object
Installing /usr/local/share/perl/5.34.0/File/Find/Object.pm
Installing /usr/local/share/perl/5.34.0/File/Find/Object/PathComp.pm
Installing /usr/local/share/perl/5.34.0/File/Find/Object/Base.pm
Installing /usr/local/share/perl/5.34.0/File/Find/Object/Result.pm
Installing /usr/local/man/man3/File::Find::Object::Base.3pm
Installing /usr/local/man/man3/File::Find::Object::PathComp.3pm
Installing /usr/local/man/man3/File::Find::Object.3pm
Installing /usr/local/man/man3/File::Find::Object::Result.3pm
  SHLOMIF/File-Find-Object-0.3.6.tar.gz
  sudo ./Build install  -- OK
  SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
  Has already been unwrapped into directory /home/jonathan/.cpan/build/File-Find-Object-Rule-0.0313-0
  SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
  Has already been prepared
Running Build for S/SH/SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
Building File-Find-Object-Rule
  SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
  ./Build -- OK
Running Build test for SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
t/00-compile.t .............. ok   
t/File-Find-Rule.t .......... ok     
t/findorule.t ............... ok   
t/release-trailing-space.t .. skipped: these tests are for release candidate testing
All tests successful.
Files=4, Tests=49,  1 wallclock secs ( 0.03 usr  0.00 sys +  0.51 cusr  0.06 csys =  0.60 CPU)
Result: PASS
  SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
  ./Build test -- OK
Running Build install for SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
Building File-Find-Object-Rule
Installing /usr/local/man/man1/findorule.1p
Installing /usr/local/share/perl/5.34.0/File/Find/Object/Rule.pm
Installing /usr/local/share/perl/5.34.0/File/Find/Object/Rule/Extending.pod
Installing /usr/local/share/perl/5.34.0/File/Find/Object/Rule/Procedural.pod
Installing /usr/local/man/man3/File::Find::Object::Rule::Extending.3pm
Installing /usr/local/man/man3/File::Find::Object::Rule.3pm
Installing /usr/local/man/man3/File::Find::Object::Rule::Procedural.3pm
Installing /usr/local/bin/findorule
  SHLOMIF/File-Find-Object-Rule-0.0313.tar.gz
  sudo ./Build install  -- OK
  SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
  Has already been unwrapped into directory /home/jonathan/.cpan/build/Test-TrailingSpace-0.0601-0
  SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
  Has already been prepared
Running Build for S/SH/SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
Building Test-TrailingSpace
  SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
  ./Build -- OK
Running Build test for SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
t/00-compile.t ... ok   
t/dogfood.t ...... ok   
t/object-test.t .. ok     
All tests successful.
Files=3, Tests=12,  1 wallclock secs ( 0.02 usr  0.01 sys +  0.35 cusr  0.05 csys =  0.43 CPU)
Result: PASS
  SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
  ./Build test -- OK
Running Build install for SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
Building Test-TrailingSpace
Installing /usr/local/share/perl/5.34.0/Test/TrailingSpace.pm
Installing /usr/local/man/man3/Test::TrailingSpace.3pm
  SHLOMIF/Test-TrailingSpace-0.0601.tar.gz
  sudo ./Build install  -- OK

```



And, incidentally, all three cpan tests ran in less than 5 minutes.

---

### Post by Holger_Gehrke on 2022-04-26
> **heroquestelf said:**
> Here is my cpan:tidyall results.

[snip]

Here is my cpan Plugin flake8 results

[snip]

And here is the final test

[snip]

And, incidentally, all three cpan tests ran in less than 5 minutes.

Those aren't test, they are installations of Perl modules which are then used in running test on the python code when you do 'gmake test'. These are purely cosmetic tests, they check for things which have to do with the consistent formatting of the Python source code across all the modules. The important tests which actually are concerned with the program being able to run are ones which don't need Perl or these Perl modules from CPAN (which is why I said not to bother with these).

The time difference could be due to my potato-level system **or** it might have something to do with the fact that I installed them into a personal library (local::lib) which means I probably had to install a few more modules (I don't recall the details, but the output went on for dozens of screens). The advantage of this is that I didn't install a lot of Perl modules I probably won't ever need again system wide. I can just remove the variable definitions from ~/.bashrc and remove ~/perl5 and everything is clean again. Don't ask me what you have to do to get rid of these modules. They are unlikely to cause any harm, but they are not doing any good, either.

Did you install pip3 and and use it to install the Python modules pycotap and pysol_cards ? Your output from 'gmake test' looks a lot like the stuff I got before I installed those two.

Holger

---

