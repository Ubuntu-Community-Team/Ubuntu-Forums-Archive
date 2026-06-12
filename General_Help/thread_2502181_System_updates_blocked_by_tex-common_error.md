---
title: "System updates blocked by tex-common error"
date: 2024-11-04
forum: General Help
---

### Post by jet-bundle on 2024-11-04
I have recently upgraded a system from Lubuntu 22.04 to Lubuntu 24.04.

I used TeX on the system, and have texlive installed. When I log on, I am notified that there are system updates available, but when I click to Install Updates the system attempts to process tex-common, encounters an error, and then stops the update. (See two images attached.)

This seems to be similar to an old problem posted here: [HTML]https://ubuntuforums.org/showthread.php?t=2380321&highlight=tex+live[/HTML]

I followed links in that thread and found some advice on how to deal with the problem, but when I tried it the error persisted. Here's what happened:

```

~$ cd /tmp
/tmp$ apt download tex-common
Get:1 http://archive.ubuntu.com/ubuntu noble/universe amd64 tex-common all 6.18 [32.8 kB]
Fetched 32.8 kB in 0s (286 kB/s)      
/tmp$ dpkg-deb -R tex-common_6.18_all.deb /tmp/fixfolder
/tmp$ sed -i -e 's/--no-error-if-no-engine=luajittex //' /tmp/fixfolder/DEBIAN/postinst
/tmp$ dpkg-deb -b /tmp/fixfolder /tmp/fixed-tex-common.deb
dpkg-deb: building package 'tex-common' in '/tmp/fixed-tex-common.deb'.
/tmp$ sudo dpkg --force-all -r tex-common
[sudo] password for david: 
dpkg: tex-common: dependency problems, but removing anyway as you requested:
 tipa depends on tex-common (>= 6.13).
 texlive-xetex depends on tex-common (>= 6.13).
 texlive-science-doc depends on tex-common (>= 6.13).
 texlive-science depends on tex-common (>= 6.13).
 texlive-publishers-doc depends on tex-common (>= 6.13).
 texlive-publishers depends on tex-common (>= 6.13).
 texlive-pstricks-doc depends on tex-common (>= 6.13).
 texlive-pstricks depends on tex-common (>= 6.13).
 texlive-plain-generic depends on tex-common (>= 6.13).
 texlive-pictures-doc depends on tex-common (>= 6.13).
 texlive-pictures depends on tex-common (>= 6.13).
 texlive-music depends on tex-common (>= 6.13).
 texlive-metapost-doc depends on tex-common (>= 6.13).
 texlive-metapost depends on tex-common (>= 6.13).
 texlive-luatex depends on tex-common (>= 6.13).
 texlive-latex-recommended-doc depends on tex-common (>= 6.13).
 texlive-latex-recommended depends on tex-common (>= 6.13).
 texlive-latex-extra-doc depends on tex-common (>= 6.13).
 texlive-latex-extra depends on tex-common (>= 6.13).
 texlive-latex-base-doc depends on tex-common (>= 6.13).
 texlive-latex-base depends on tex-common (>= 6.13).
 texlive-lang-spanish depends on tex-common (>= 6.13).
 texlive-lang-portuguese depends on tex-common (>= 6.13).
 texlive-lang-polish depends on tex-common (>= 6.13).
 texlive-lang-other depends on tex-common (>= 6.13).
 texlive-lang-korean depends on tex-common (>= 6.13).
 texlive-lang-japanese depends on tex-common (>= 6.13).
 texlive-lang-italian depends on tex-common (>= 6.13).
 texlive-lang-greek depends on tex-common (>= 6.13).
 texlive-lang-german depends on tex-common (>= 6.13).
 texlive-lang-french depends on tex-common (>= 6.13).
 texlive-lang-european depends on tex-common (>= 6.13).
 texlive-lang-english depends on tex-common (>= 6.13).
 texlive-lang-czechslovak depends on tex-common (>= 6.13).
 texlive-lang-cyrillic depends on tex-common (>= 6.13).
 texlive-lang-cjk depends on tex-common (>= 6.13).
 texlive-lang-chinese depends on tex-common (>= 6.13).
 texlive-lang-arabic depends on tex-common (>= 6.13).
 texlive-humanities-doc depends on tex-common (>= 6.13).
 texlive-humanities depends on tex-common (>= 6.13).
 texlive-games depends on tex-common (>= 6.13).
 texlive-formats-extra depends on tex-common (>= 6.13).
 texlive-fonts-recommended-doc depends on tex-common (>= 6.13).
 texlive-fonts-recommended depends on tex-common (>= 6.13).
 texlive-fonts-extra-links depends on tex-common (>= 6.13).
 texlive-fonts-extra-doc depends on tex-common (>= 6.13).
 texlive-fonts-extra depends on tex-common (>= 6.13).
 texlive-font-utils depends on tex-common (>= 6.13).
 texlive-extra-utils depends on tex-common (>= 6.13).
 texlive-binaries depends on tex-common.
 texlive-bibtex-extra depends on tex-common (>= 6.13).
 texlive-base depends on tex-common (>= 6.14).
 texinfo depends on tex-common.
 tex-gyre depends on tex-common (>= 6.13).
 preview-latex-style depends on tex-common (>= 6.13).
 lmodern depends on tex-common (>= 6.13).
 latex-cjk-thai depends on tex-common (>= 6.13).
 latex-cjk-korean depends on tex-common (>= 6.13).
 latex-cjk-japanese-wadalab depends on tex-common (>= 6.13).
 latex-cjk-japanese depends on tex-common (>= 6.13).
 latex-cjk-common depends on tex-common (>= 6.13).
 latex-cjk-chinese-arphic-gkai00mp depends on tex-common (>= 6.13).
 latex-cjk-chinese-arphic-gbsn00lp depends on tex-common (>= 6.13).
 latex-cjk-chinese-arphic-bsmi00lp depends on tex-common (>= 6.13).
 latex-cjk-chinese-arphic-bkai00mp depends on tex-common (>= 6.13).
 latex-cjk-chinese depends on tex-common (>= 6.13).
 feynmf depends on tex-common (>= 6.13).
 context-modules depends on tex-common (>= 6.13).
 context depends on tex-common (>= 6.13).
 cm-super-minimal depends on tex-common (>= 6.13).
 cm-super depends on tex-common (>= 6.13).
 biber depends on tex-common (>= 6.13).
 asymptote depends on tex-common (>= 6.13).

(Reading database ... 631714 files and directories currently installed.)
Removing tex-common (6.18) ...
Processing triggers for man-db (2.12.0-4build2) ...
/tmp$ sudo dpkg -i /tmp/fixed-tex-common.deb
Selecting previously unselected package tex-common.
(Reading database ... 631680 files and directories currently installed.)
Preparing to unpack /tmp/fixed-tex-common.deb ...
Unpacking tex-common (6.18) ...
Setting up tex-common (6.18) ...
Running mktexlsr. This may take some time... done.
Running mtxrun --generate. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building format(s) --all.
        This may take some time... 
fmtutil failed. Output has been stored in
/tmp/fmtutil.dgiQZmC7
Please include this file if you report a bug.

dpkg: error processing package tex-common (--install):
 installed tex-common package post-installation script subprocess returned error exit status 1
Processing triggers for man-db (2.12.0-4build2) ...
Errors were encountered while processing:
 tex-common
/tmp$

```

I'd be grateful for any further advice.

---

