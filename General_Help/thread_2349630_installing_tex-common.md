---
title: "installing tex-common"
date: 2017-01-16
forum: General Help
---

### Post by crouchy89 on 2017-01-16
Hi All,
This appears to be a long-running problem and hopefully somebody will be able to help me sort it out. I am trying to install XeLaTeX and running into issues with tex-common throwing dependency issues. I am running Ubuntu 16.04 LTS

Based on previous posts, I first removed all previous versions tex on my machine. 
```

sudo dpkg --force-all --purge texlive-latex-base-doc
sudo apt-get remove --purge tex-common texlive-*
sudo apt-get autoremove 

```
Based on previous posts I first tried installing tex-common by itself first, and then the remaining tex packages
```

sudo apt-get install tex-common 
sudo apt-get install texlive-xetex 

```

Now this actually makes XeLaTeX work, I can compile documents using TexMaker, but when I run ```
 sudo apt-get upgrade
``` I get a whole list of errors thrown:
```

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
...
 Errors were encountered while processing:
 tex-common
 texlive-latex-base
 tipa
 texlive-latex-recommended
 texlive-pictures
 texlive-latex-extra
 texlive-xetex
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-fonts-recommended
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-extra-doc
 texlive-latex-recommended-doc
 texlive-pictures-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
The version of tex-common installed is 6.04. Most solutions I have seen have simply involved uninstalling and trying again, e.g.:
[http://askubuntu.com/questions/808201/installation-problem-of-texlive-in-xubuntu-16-04-1](http://askubuntu.com/questions/808201/installation-problem-of-texlive-in-xubuntu-16-04-1)
[http://askubuntu.com/questions/744585/apt-get-broken-after-version-update-unmet-dependencies](http://askubuntu.com/questions/744585/apt-get-broken-after-version-update-unmet-dependencies)
[http://askubuntu.com/questions/512848/tex-common-troubleshooting-on-ubuntu-14-04-lts](http://askubuntu.com/questions/512848/tex-common-troubleshooting-on-ubuntu-14-04-lts)


If anybody can give me some pointers it would be, as always, deeply appreciated

---

### Post by #&amp;thj^% on 2017-01-16
You can run apt-get install -f.
From this:
```
dpkg: dependency problems prevent configuration of texlive-latex-base:  texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
```
```
sudo apt install -f
```
Post back any errors.

---

### Post by crouchy89 on 2017-01-16
Thanks. Here is the full (long) return:

```

sudo apt install -f


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tex-common (6.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.PTxy13OE
Please include this file if you report a bug.


Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory


dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
     dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.


dpkg: error processing package texlive-latex-recommended (--coNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                   No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
                                                                                          No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
            nfigure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2015); however:
  Package texlive-latex-recommended is not configured yet.


dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-extra depends on texlive-latex-recommended (>= 2015); however:
  Package texlive-latex-recommended is not configured yet.
 texlive-latex-extra depends on texlive-pictures (>= 2015); however:
  Package texlive-pictures is not configured yet.


dpkg: error processing package texlive-latex-extra (--configure):
 dependency problems - leaving unconfiguNo apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               red
dpkg: dependency problems prevent configuration of texlive-xetex:
 texlive-xetex depends on tipa (>= 2:1.2-2.1); however:
  Package tipa is not configured yet.
 texlive-xetex depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-xetex depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.
 texlive-xetex depends on texlive-latex-extra (>= 2015); however:
  Package texlive-latex-extra is not configured yet.


dpkg: error processing package texlive-xetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-pictures (>= 2015); however:
  Package texlive-pictures is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2015); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.


dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigNo apport report written because MaxReports is reached already
                                                                                                    ured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tex-common
 texlive-latex-base
 tipa
 texlive-latex-recommended
 texlive-pictures
 texlive-latex-extra
 texlive-xetex
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-fonts-recommended
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-extra-doc
 texlive-latex-recommended-doc
 texlive-pictures-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

The contents of /tmp/updmap.PTxy13OE:

 
```

updmap [WARNING]: resetting $HOME value (was /home/nick) to root's actual home (/root).
updmap will read the following updmap.cfg files (in precedence order):
  /root/.texmf-config/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap may write changes to the following updmap.cfg file:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"
updmap [ERROR]: The following map file(s) couldn't be found:
updmap [ERROR]:     MinionPro (in /root/.texmf-config/web2c/updmap.cfg)
updmap [ERROR]:     MnSymbol.Map (in /root/.texmf-config/web2c/updmap.cfg)
updmap [ERROR]:     MnSymbol.map (in /root/.texmf-config/web2c/updmap.cfg)
updmap [ERROR]: Did you run mktexlsr?


    You can disable non-existent map entries using the option
      --syncwithtrees.

```

---

### Post by #&amp;thj^% on 2017-01-16
Seems we have some edgy installs:
```
19 not fully installed or removed.
```
Need to think a bit here..as what to offer next.
But lets see for now if this give us another clue..
```
sudo apt dist-upgrade
```
And watch for what is being removed and installed, before proceeding.;)

---

### Post by crouchy89 on 2017-01-16
```

sudo apt-get dist-upgrade

```
gives the same long error output

---

### Post by #&amp;thj^% on 2017-01-16
Thought as much.
Still thinking here:
Lets see all packages that are not in state "installed" or "removed"
```
dpkg --list | grep -ve 'ii\|^rc'
```
Post back the output of the above.

---

### Post by crouchy89 on 2017-01-16
```

dpkg --list | grep -ve 'ii\|^rc'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                                       Architecture Description
+++-==========================================-=============================================-============-================================================================================
iU  prosper                                    1.00.4+cvs.2007.05.01-4                       all          LaTeX class for writing transparencies
iF  tex-common                                 6.04                                          all          common infrastructure for building and installing TeX
iU  texlive-extra-utils                        2015.20160320-1                               all          TeX Live: TeX auxiliary programs
iU  texlive-font-utils                         2015.20160320-1                               all          TeX Live: Graphics and font utilities
iU  texlive-fonts-recommended                  2015.20160320-1                               all          TeX Live: Recommended fonts
iU  texlive-fonts-recommended-doc              2015.20160320-1                               all          TeX Live: Documentation files for texlive-fonts-recommended
iU  texlive-generic-recommended                2015.20160320-1                               all          TeX Live: Generic recommended packages
iU  texlive-latex-base                         2015.20160320-1                               all          TeX Live: LaTeX fundamental packages
iU  texlive-latex-base-doc                     2015.20160320-1                               all          TeX Live: Documentation files for texlive-latex-base
iU  texlive-latex-extra                        2015.20160320-1                               all          TeX Live: LaTeX additional packages
iU  texlive-latex-extra-doc                    2015.20160320-1                               all          TeX Live: Documentation files for texlive-latex-extra
iU  texlive-latex-recommended                  2015.20160320-1                               all          TeX Live: LaTeX recommended packages
iU  texlive-latex-recommended-doc              2015.20160320-1                               all          TeX Live: Documentation files for texlive-latex-recommended
iU  texlive-pictures                           2015.20160320-1                               all          TeX Live: Graphics, pictures, diagrams
iU  texlive-pictures-doc                       2015.20160320-1                               all          TeX Live: Documentation files for texlive-pictures
iU  texlive-pstricks                           2015.20160320-1                               all          TeX Live: PSTricks
iU  texlive-pstricks-doc                       2015.20160320-1                               all          TeX Live: Documentation files for texlive-pstricks
iU  texlive-xetex                              2015.20160320-1                               all          TeX Live: XeTeX and packages
iU  tipa                                       2:1.3-20                                      all          system for processing phonetic symbols in LaTeX

```
Interesting. The 'prosper' package I don't recognize

---

### Post by #&amp;thj^% on 2017-01-16
Yikes!! I can not imagine how this got to such a state.
This is going to take me some time here in how to proceed.
Be back as soon as get something thrown together.
Oh and this "Interesting. The 'prosper' package I don't recognize"
```
apt policy prosper
prosper:
  Installed: 1.00.4+cvs.2007.05.01-4
  Candidate: 1.00.4+cvs.2007.05.01-4
  Version table:
 *** 1.00.4+cvs.2007.05.01-4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status


```

---

### Post by crouchy89 on 2017-01-16
I have the same output. I guess I just didn't notice it among everything else

---

### Post by #&amp;thj^% on 2017-01-17
This is what is interesting:
```
[COLOR=#ff0000]iF  tex-common[/COLOR]                                 6.04                                          all          common infrastructure for building and installing TeX
```
I guess first thing to do is try to see if if can get this installed properly.
This tells me it is not:
```
iF = Half-configured
```
So lets see what happens when we give it a little tug:

```
sudo dpkg --purge --force-depends texlive-lang-other texlive-latex-extra tex-common texlive-fonts-recommended texlive-pictures texlive-metapost
```
And then if no bad errors are hanging us up here:
```
sudo apt-get install -f texlive-lang-other texlive-latex-extra tex-common texlive-fonts-recommended texlive-pictures texlive-metapost
```
And if all goes well do this next:
```
sudo mktexlsr
sudo updmap-sys 

```
Fingers Crossed here:D

---

### Post by crouchy89 on 2017-01-17
Running first line:

```

sudo dpkg --purge --force-depends texlive-lang-other texlive-latex-extra tex-common texlive-fonts-recommended texlive-pictures texlive-metapost


dpkg: warning: ignoring request to remove texlive-lang-other which isn't installed
(Reading database ... 246983 files and directories currently installed.)
Removing texlive-fonts-recommended (2015.20160320-1) ...
Purging configuration files for texlive-fonts-recommended (2015.20160320-1) ...
dpkg: warning: ignoring request to remove texlive-metapost which isn't installed
dpkg: texlive-pictures: dependency problems, but removing anyway as you requested:
 texlive-latex-extra depends on texlive-pictures (>= 2015); however:
  Package texlive-pictures is to be removed.
 texlive-pstricks depends on texlive-pictures (>= 2015).


Removing texlive-pictures (2015.20160320-1) ...
Purging configuration files for texlive-pictures (2015.20160320-1) ...
dpkg: texlive-latex-extra: dependency problems, but removing anyway as you requested:
 texlive-xetex depends on texlive-latex-extra (>= 2015); however:
  Package texlive-latex-extra is to be removed.


Removing texlive-latex-extra (2015.20160320-1) ...
Purging configuration files for texlive-latex-extra (2015.20160320-1) ...
dpkg: tex-common: dependency problems, but removing anyway as you requested:
 fonts-lmodern depends on tex-common (>= 6).
 texlive-latex-base-doc depends on tex-common (>= 6).
 lmodern depends on tex-common (>= 6).
 texlive-latex-base depends on tex-common (>= 6).
 texlive-xetex depends on tex-common (>= 6); however:
  Package tex-common is to be removed.
 texlive-generic-recommended depends on tex-common (>= 6).
 texlive-fonts-recommended-doc depends on tex-common (>= 6).
 texlive-latex-recommended-doc depends on tex-common (>= 6).
 texlive-base depends on tex-common (>= 6).
 texlive-latex-extra-doc depends on tex-common (>= 6).
 texlive-binaries depends on tex-common (>= 6).
 texlive-font-utils depends on tex-common (>= 6).
 fonts-texgyre depends on tex-common (>= 6).
 preview-latex-style depends on tex-common (>= 6).
 tipa depends on tex-common (>= 3); however:
  Package tex-common is to be removed.
 tex-gyre depends on tex-common (>= 6).
 texlive-pstricks-doc depends on tex-common (>= 6).
 prosper depends on t
Removing tex-common (6.04) ...
Purging configuration files for tex-common (6.04) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for doc-base (0.10.7) ...
Processing 2 removed doc-base files...
Registering documents with scrollkeeper...

```

Is it OK to move onto the second line? Thanks

---

### Post by #&amp;thj^% on 2017-01-17
Yep... lets give it go then.

---

### Post by crouchy89 on 2017-01-17
Same problem as before:

```

sudo apt-get install -f texlive-lang-other texlive-latex-extra tex-common texlive-fonts-recommended texlive-pictures texlive-metapost
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-pygments libspreadsheet-parseexcel-perl libtcltk-ruby dot2tex prerex
Recommended packages:
  texlive-metapost-doc feynmf
The following NEW packages will be installed:
  tex-common texlive-fonts-recommended texlive-lang-other texlive-latex-extra texlive-metapost texlive-pictures
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.


...


Setting up tex-common (6.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.BmK3avJY
Please include this file if you report a bug.


Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory


dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.


dpkg: error processing package texlive-latex-recommended (--coNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                        No apport report written because the error message indicates its a followup error from a previous failure.
 
...


 texlive-latex-base
 tipa
 texlive-latex-recommended
 texlive-pictures
 texlive-latex-extra
 texlive-xetex
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-extra-doc
 texlive-latex-recommended-doc
 texlive-pictures-doc
 texlive-pstricks-doc
 texlive-fonts-recommended
 texlive-lang-other
 texlive-metapost
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by #&amp;thj^% on 2017-01-17
What is the output if this:
```
sudo mktexlsr
```
There is a reason that this happens we just have to find why?
Mine shows something like this:
```
sudo updmap-sys
[sudo] password for me: 
updmap [WARNING]: resetting $HOME value (was /home/me) to root's actual home (/root).
updmap will read the following updmap.cfg files (in precedence order):
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap may write changes to the following updmap.cfg file:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"

updmap is creating new map files
using the following configuration:
  LW35 font names                  : URWkb (default)
  prefer outlines                  : true (default)
  texhash enabled                  : true
  download standard fonts (dvips)  : true (default)
  download standard fonts (pdftex) : true (default)
  kanjiEmbed replacement string    : noEmbed (default)
  kanjiVariant replacement string  :  (default)
  create a mapfile for pxdvi       : false (default)

Scanning for LW35 support files  [  3 files]
Scanning for MixedMap entries    [ 14 files]
Scanning for KanjiMap entries    [  0 files]
Scanning for Map entries         [ 31 files]

Generating output for dvipdfmx...
Generating output for ps2pk...
Generating output for dvips...
Generating output for pdftex...

Files generated:
  /var/lib/texmf/fonts/map/dvips/updmap:
       15758 2017-01-17 10:05:09 builtin35.map
       21231 2017-01-17 10:05:09 download35.map
      119982 2017-01-17 10:05:09 psfonts_pk.map
      127803 2017-01-17 10:05:09 psfonts_t1.map
      127798 2017-01-17 10:05:09 ps2pk.map
          14 2017-01-17 10:05:09 psfonts.map -> psfonts_t1.map
  /var/lib/texmf/fonts/map/pdftex/updmap:
      127805 2017-01-17 10:05:09 pdftex_dl14.map
      126140 2017-01-17 10:05:09 pdftex_ndl14.map
          15 2017-01-17 10:05:09 pdftex.map -> pdftex_dl14.map
  /var/lib/texmf/fonts/map/dvipdfmx/updmap:
         281 2017-01-17 10:05:09 kanjix.map

Transcript written on "/var/lib/texmf/web2c/updmap.log".
updmap: Updating ls-R files.


```

---

### Post by crouchy89 on 2017-01-17
Mine looks like this:
```

sudo mktexlsr


mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.

```
and
```

sudo updmap-sys
updmap [WARNING]: resetting $HOME value (was /home/nick) to root's actual home (/root).
updmap will read the following updmap.cfg files (in precedence order):
  /root/.texmf-config/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap may write changes to the following updmap.cfg file:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"
updmap [ERROR]: The following map file(s) couldn't be found:
updmap [ERROR]:     MinionPro (in /root/.texmf-config/web2c/updmap.cfg)
updmap [ERROR]:     MnSymbol.Map (in /root/.texmf-config/web2c/updmap.cfg)
updmap [ERROR]:     MnSymbol.map (in /root/.texmf-config/web2c/updmap.cfg)
updmap [ERROR]: Did you run mktexlsr?


    You can disable non-existent map entries using the option
      --syncwithtrees.

```

I had previously installed the MinionPro font and MnSymbol. Is it that those files are not getting purged and therefore creating issues when trying to re-install?

---

### Post by #&amp;thj^% on 2017-01-17
Yes there it is...I would now go in (with a text editor) and comment them out and then run:
```
sudo apt -f install
```
Now is it happy?

---

### Post by crouchy89 on 2017-01-17
Ah terrific! I think that has done the trick. I now get:

```

sudo updmap-sys
updmap [WARNING]: resetting $HOME value (was /home/nick) to root's actual home (/root).
updmap will read the following updmap.cfg files (in precedence order):
  /root/.texmf-config/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap may write changes to the following updmap.cfg file:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"


updmap is creating new map files
using the following configuration:
  LW35 font names                  : URWkb (default)
  prefer outlines                  : true (default)
  texhash enabled                  : true
  download standard fonts (dvips)  : true (default)
  download standard fonts (pdftex) : true (default)
  kanjiEmbed replacement string    : noEmbed (default)
  kanjiVariant replacement string  :  (default)
  create a mapfile for pxdvi       : false (default)


Scanning for LW35 support files  [  3 files]
Scanning for MixedMap entries    [ 16 files]
Scanning for KanjiMap entries    [  0 files]
Scanning for Map entries         [ 46 files]


Generating output for dvipdfmx...
Generating output for ps2pk...
Generating output for dvips...
Generating output for pdftex...


Files generated:
  /var/lib/texmf/fonts/map/dvips/updmap:
       15758 2017-01-17 13:36:21 builtin35.map
       21231 2017-01-17 13:36:21 download35.map
      130624 2017-01-17 13:36:21 psfonts_pk.map
      139880 2017-01-17 13:36:21 psfonts_t1.map
      139875 2017-01-17 13:36:21 ps2pk.map
          14 2017-01-17 13:36:21 psfonts.map -> psfonts_t1.map
  /var/lib/texmf/fonts/map/pdftex/updmap:
      139882 2017-01-17 13:36:21 pdftex_dl14.map
      138217 2017-01-17 13:36:21 pdftex_ndl14.map
          15 2017-01-17 13:36:21 pdftex.map -> pdftex_dl14.map
  /var/lib/texmf/fonts/map/dvipdfmx/updmap:
         281 2017-01-17 13:36:21 kanjix.map


WARNING: updmap has found mismatched files!


The following files have been generated as listed above,
but will not be found because overriding files exist, listed below.
 builtin35.map: /root/.texmf-var/fonts/map/dvips/updmap/builtin35.map
 download35.map: /root/.texmf-var/fonts/map/dvips/updmap/download35.map
 kanjix.map: /root/.texmf-var/fonts/map/dvipdfmx/updmap/kanjix.map
 pdftex.map: /root/.texmf-var/fonts/map/pdftex/updmap/pdftex.map
 pdftex_dl14.map: /root/.texmf-var/fonts/map/pdftex/updmap/pdftex_dl14.map
 pdftex_ndl14.map: /root/.texmf-var/fonts/map/pdftex/updmap/pdftex_ndl14.map
 ps2pk.map: /root/.texmf-var/fonts/map/dvips/updmap/ps2pk.map
 psfonts.map: /root/.texmf-var/fonts/map/dvips/updmap/psfonts.map
 psfonts_pk.map: /root/.texmf-var/fonts/map/dvips/updmap/psfonts_pk.map
 psfonts_t1.map: /root/.texmf-var/fonts/map/dvips/updmap/psfonts_t1.map
(Run updmap --help for full documentation of updmap.)


Transcript written on "/var/lib/texmf/web2c/updmap.log".
updmap: Updating ls-R files.

```

and

```

sudo apt-get upgrade

```

no longer throws any errors. Thank you for much for walking me through this. Add this one to the bank of troubleshooting files!

---

### Post by #&amp;thj^% on 2017-01-17
Good to hear..Now if you would mark this as Solved so we can add it to help others.:)
Kind Regards

---

### Post by crouchy89 on 2017-01-17
Done. Thanks again

---

