---
title: "Tex-common troubleshooting on Ubuntu 14.04 LTS"
date: 2014-08-18
forum: General Help
---

### Post by joeqesi on 2014-08-18
I've posted this on askubuntu.com but I'm not getting many responses so I thought I'd try here instead. I was going to copy the text here but I'm having issues with the formatting, so I'm just going to post the link:

[http://askubuntu.com/questions/512848/tex-common-troubleshooting-on-ubuntu-14-04-lts](http://askubuntu.com/questions/512848/tex-common-troubleshooting-on-ubuntu-14-04-lts)

In summary, during the upgrade from 12.02 to 14.04, tex-common did not install properly and after trying to fix the problem with suggestions from this launchpad thread:

[https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1236951](https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1236951)

And it's just led to more problems.

Would anyone be able to help?

---

### Post by steeldriver on 2014-08-18
so your askubuntu post says

> 
Install texlive following the instructions on [http://tug.org/texlive/](http://tug.org/texlive/) (Installation from dpkg or Ubuntu software centre or synaptic package manager don't work for me.)


What does that mean exactly? what dind't work, and what steps did you take exactly?

---

### Post by joeqesi on 2014-08-18
So I followed the instructions on the [http://tug.org/texlive/quickinstall.html](http://tug.org/texlive/quickinstall.html) page.

The preinstall cleanup consists of removing the previous texlive files:

    rm -rf /usr/local/texlive/2014
    rm -rf ~/.texlive2014

I used this page: [http://tug.org/texlive/acquire-netinstall.html](http://tug.org/texlive/acquire-netinstall.html)
to download texlive as a tar file which I believe I unzipped into my Downloads folder because I didn't really know where I was supposed to put it.

I changed to the download folder and installed it using

    sudo ./install-tl

and then when it asked me to enter command:

    i

After that, I set the paths as I mentioned earlier:

    PATH=/usr/local/texlive/2014/bin/i386-linux:$PATH

    MANPATH=/usr/local/texlive/2014/texmf-dist/doc/man:$MANPATH

    INFOPATH=/usr/local/texlive/2014/texmf-dist/doc/info:$INFOPATH

---

### Post by steeldriver on 2014-08-18
I guess my point is that if you installed texlive from outside of the apt-get / dpkg system, subsequently trying to install tex-common from repositories may have compatibility / version conflicts

If you really need to have the manually-installed texlive, then I'm afraid you will likely need to dive into the failing post-installation script and see if you can figure out what the underlying issue is

Otherwise, I'd suggest backing up and revisitng why you had problems with installation from the standard repo, and trying to fix **that**

---

### Post by Impavidus on 2014-08-18
Maybe cleaning the cache and reinstalling tex-common using apt-get fixes the postinstall script. And you choose well by installing tex manually in /usr/local, which is the directory meant for manual installation.

For me TeX & friends installed from the Ubuntu repositories work fine. On Precise Pangolin I had the problem that many packages were seriously outdated, which I solved by manually installing recent versions of those packages in /usr/local/share/texmf. On Trusty Tahr everything has been updated, so I now longer need those manually installed packages and only use /usr/local/share/texmf for some home-made code. The problem may come back when Trusty gets old and we will be anxiously waiting for X... X... Whatever animal with an X they come up with.

So it would be interesting to know why you can't use the version from the repos.

---

### Post by joeqesi on 2014-08-18
I tried clearing the cache using bleachbit, but when it came to installing tex-common using apt-get I apparently already had the latest version of tex-common,

I decided to try and start again by removing the line I edited into the manpath.config file and running:

sudo apt-get remove --purge tex-common texlive-*

But when I did, I got this output:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'texlive-doc-cs+sk' for regex 'texlive-*'
Note, selecting 'texlive-fonts-recommended' for regex 'texlive-*'
Note, selecting 'texlive-doc-ar' for regex 'texlive-*'
Note, selecting 'texlive-lang-german' for regex 'texlive-*'
Note, selecting 'texlive-music' for regex 'texlive-*'
Note, selecting 'texlive-doc-bg' for regex 'texlive-*'
Note, selecting 'texlive-omega' for regex 'texlive-*'
Note, selecting 'texlive-lang-latvian' for regex 'texlive-*'
Note, selecting 'texlive-doc-de' for regex 'texlive-*'
Note, selecting 'texlive-base-recommended' for regex 'texlive-*'
Note, selecting 'texlive-lang-polish' for regex 'texlive-*'
Note, selecting 'texlive-doc-en' for regex 'texlive-*'
Note, selecting 'texlive-doc-es' for regex 'texlive-*'
Note, selecting 'texlive-latex-extra-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-arabic' for regex 'texlive-*'
Note, selecting 'texlive-doc-fi' for regex 'texlive-*'
Note, selecting 'texlive-doc-fr' for regex 'texlive-*'
Note, selecting 'texlive-lang-croatian' for regex 'texlive-*'
Note, selecting 'texlive-texinfo' for regex 'texlive-*'
Note, selecting 'texlive-publishers' for regex 'texlive-*'
Note, selecting 'texlive-doc-it' for regex 'texlive-*'
Note, selecting 'texlive-formats-extra' for regex 'texlive-*'
Note, selecting 'texlive-doc-ja' for regex 'texlive-*'
Note, selecting 'texlive-humanities' for regex 'texlive-*'
Note, selecting 'texlive-lang-african' for regex 'texlive-*'
Note, selecting 'texlive-pstricks' for regex 'texlive-*'
Note, selecting 'texlive-lang-portuguese' for regex 'texlive-*'
Note, selecting 'texlive-doc-ko' for regex 'texlive-*'
Note, selecting 'texlive-generic-extra' for regex 'texlive-*'
Note, selecting 'texlive-lang-lithuanian' for regex 'texlive-*'
Note, selecting 'texlive-latex3' for regex 'texlive-*'
Note, selecting 'texlive-lang-danish' for regex 'texlive-*'
Note, selecting 'texlive-lang-finnish' for regex 'texlive-*'
Note, selecting 'texlive-doc-mn' for regex 'texlive-*'
Note, selecting 'texlive-context' for regex 'texlive-*'
Note, selecting 'texlive-lang-czechslovak' for regex 'texlive-*'
Note, selecting 'texlive-doc-nl' for regex 'texlive-*'
Note, selecting 'texlive-lang-vietnamese' for regex 'texlive-*'
Note, selecting 'texlive-lang-korean' for regex 'texlive-*'
Note, selecting 'texlive-binaries' for regex 'texlive-*'
Note, selecting 'texlive-doc-pl' for regex 'texlive-*'
Note, selecting 'texlive-doc-pt' for regex 'texlive-*'
Note, selecting 'texlive-lang-cjk' for regex 'texlive-*'
Note, selecting 'texlive-metapost-doc' for regex 'texlive-*'
Note, selecting 'texlive-science' for regex 'texlive-*'
Note, selecting 'texlive-latex-recommended' for regex 'texlive-*'
Note, selecting 'texlive-lang-english' for regex 'texlive-*'
Note, selecting 'texlive-math-extra' for regex 'texlive-*'
Note, selecting 'texlive-lang-latin' for regex 'texlive-*'
Note, selecting 'texlive-doc-rs' for regex 'texlive-*'
Note, selecting 'texlive-doc-ru' for regex 'texlive-*'
Note, selecting 'texlive-doc-si' for regex 'texlive-*'
Note, selecting 'texlive-lang-tibetan' for regex 'texlive-*'
Note, selecting 'texlive-doc-th' for regex 'texlive-*'
Note, selecting 'texlive-doc-tr' for regex 'texlive-*'
Note, selecting 'texlive-lang-greek' for regex 'texlive-*'
Note, selecting 'texlive-doc-uk' for regex 'texlive-*'
Note, selecting 'texlive-doc-vi' for regex 'texlive-*'
Note, selecting 'texlive-font-utils' for regex 'texlive-*'
Note, selecting 'texlive-base' for regex 'texlive-*'
Note, selecting 'texlive-latex-base' for regex 'texlive-*'
Note, selecting 'texlive-humanities-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-indic' for regex 'texlive-*'
Note, selecting 'texlive-games' for regex 'texlive-*'
Note, selecting 'texlive-xetex' for regex 'texlive-*'
Note, selecting 'texlive-lang-cyrillic' for regex 'texlive-*'
Note, selecting 'texlive-doc-zh' for regex 'texlive-*'
Note, selecting 'texlive-bibtex-extra' for regex 'texlive-*'
Note, selecting 'texlive-lang-norwegian' for regex 'texlive-*'
Note, selecting 'texlive-lang-spanish' for regex 'texlive-*'
Note, selecting 'texlive-lang-dutch' for regex 'texlive-*'
Note, selecting 'texlive-luatex' for regex 'texlive-*'
Note, selecting 'texlive-common' for regex 'texlive-*'
Note, selecting 'texlive-fonts-extra' for regex 'texlive-*'
Note, selecting 'texlive-lang-armenian' for regex 'texlive-*'
Note, selecting 'texlive-science-doc' for regex 'texlive-*'
Note, selecting 'texlive-metapost' for regex 'texlive-*'
Note, selecting 'texlive-plain-extra' for regex 'texlive-*'
Note, selecting 'texlive-latex-base-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-hungarian' for regex 'texlive-*'
Note, selecting 'texlive-pstricks-doc' for regex 'texlive-*'
Note, selecting 'texlive-latex-recommended-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-french' for regex 'texlive-*'
Note, selecting 'texlive-publishers-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-swedish' for regex 'texlive-*'
Note, selecting 'texlive-fonts-recommended-doc' for regex 'texlive-*'
Note, selecting 'texlive-generic-recommended' for regex 'texlive-*'
Note, selecting 'texlive-lang-italian' for regex 'texlive-*'
Note, selecting 'texlive-lang-all' for regex 'texlive-*'
Note, selecting 'texlive-base-bin-doc' for regex 'texlive-*'
Note, selecting 'texlive-doc-base' for regex 'texlive-*'
Note, selecting 'texlive-base-bin' for regex 'texlive-*'
Note, selecting 'texlive-fonts-extra-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-mongolian' for regex 'texlive-*'
Note, selecting 'texlive-pictures-doc' for regex 'texlive-*'
Note, selecting 'texlive-lang-chinese' for regex 'texlive-*'
Note, selecting 'texlive-extra-utils' for regex 'texlive-*'
Note, selecting 'texlive-lang-european' for regex 'texlive-*'
Note, selecting 'texlive-full' for regex 'texlive-*'
Note, selecting 'texlive-lang-hebrew' for regex 'texlive-*'
Note, selecting 'texlive-latex-extra' for regex 'texlive-*'
Note, selecting 'texlive-lang-other' for regex 'texlive-*'
Note, selecting 'texlive' for regex 'texlive-*'
Note, selecting 'texlive-lang-arab' for regex 'texlive-*'
Note, selecting 'texlive-lang-japanese' for regex 'texlive-*'
Note, selecting 'texlive-pictures' for regex 'texlive-*'
Package 'texlive-base-bin-doc' is not installed, so not removed
Note, selecting 'texlive-binaries' instead of 'texlive-base-bin'
Package 'texlive-common' is not installed, so not removed
Package 'texlive-lang-arab' is not installed, so not removed
Package 'texlive-doc-base' is not installed, so not removed
Note, selecting 'context' instead of 'texlive-context'
Package 'texlive-base-recommended' is not installed, so not removed
Package 'texlive-texinfo' is not installed, so not removed
Package 'texlive' is not installed, so not removed
Package 'texlive-bibtex-extra' is not installed, so not removed
Package 'texlive-fonts-extra-doc' is not installed, so not removed
Package 'texlive-fonts-recommended' is not installed, so not removed
Package 'texlive-fonts-recommended-doc' is not installed, so not removed
Package 'texlive-humanities-doc' is not installed, so not removed
Package 'texlive-lang-chinese' is not installed, so not removed
Package 'texlive-lang-german' is not installed, so not removed
Package 'texlive-lang-japanese' is not installed, so not removed
Package 'texlive-lang-korean' is not installed, so not removed
Package 'texlive-latex-extra' is not installed, so not removed
Package 'texlive-latex-extra-doc' is not installed, so not removed
Package 'texlive-luatex' is not installed, so not removed
Package 'texlive-math-extra' is not installed, so not removed
Package 'texlive-metapost-doc' is not installed, so not removed
Package 'texlive-publishers-doc' is not installed, so not removed
Package 'texlive-science-doc' is not installed, so not removed
Package 'texlive-doc-ar' is not installed, so not removed
Package 'texlive-doc-bg' is not installed, so not removed
Package 'texlive-doc-cs+sk' is not installed, so not removed
Package 'texlive-doc-de' is not installed, so not removed
Package 'texlive-doc-en' is not installed, so not removed
Package 'texlive-doc-es' is not installed, so not removed
Package 'texlive-doc-fi' is not installed, so not removed
Package 'texlive-doc-fr' is not installed, so not removed
Package 'texlive-doc-it' is not installed, so not removed
Package 'texlive-doc-ja' is not installed, so not removed
Package 'texlive-doc-ko' is not installed, so not removed
Package 'texlive-doc-mn' is not installed, so not removed
Package 'texlive-doc-nl' is not installed, so not removed
Package 'texlive-doc-pl' is not installed, so not removed
Package 'texlive-doc-pt' is not installed, so not removed
Package 'texlive-doc-rs' is not installed, so not removed
Package 'texlive-doc-ru' is not installed, so not removed
Package 'texlive-doc-si' is not installed, so not removed
Package 'texlive-doc-th' is not installed, so not removed
Package 'texlive-doc-tr' is not installed, so not removed
Package 'texlive-doc-uk' is not installed, so not removed
Package 'texlive-doc-vi' is not installed, so not removed
Package 'texlive-doc-zh' is not installed, so not removed
Package 'texlive-fonts-extra' is not installed, so not removed
Package 'texlive-formats-extra' is not installed, so not removed
Package 'texlive-full' is not installed, so not removed
Package 'texlive-games' is not installed, so not removed
Package 'texlive-generic-extra' is not installed, so not removed
Package 'texlive-humanities' is not installed, so not removed
Package 'texlive-lang-african' is not installed, so not removed
Package 'texlive-lang-all' is not installed, so not removed
Package 'texlive-lang-arabic' is not installed, so not removed
Package 'texlive-lang-armenian' is not installed, so not removed
Package 'texlive-lang-cjk' is not installed, so not removed
Package 'texlive-lang-croatian' is not installed, so not removed
Package 'texlive-lang-cyrillic' is not installed, so not removed
Package 'texlive-lang-czechslovak' is not installed, so not removed
Package 'texlive-lang-danish' is not installed, so not removed
Package 'texlive-lang-dutch' is not installed, so not removed
Package 'texlive-lang-english' is not installed, so not removed
Package 'texlive-lang-european' is not installed, so not removed
Package 'texlive-lang-finnish' is not installed, so not removed
Package 'texlive-lang-french' is not installed, so not removed
Package 'texlive-lang-greek' is not installed, so not removed
Package 'texlive-lang-hebrew' is not installed, so not removed
Package 'texlive-lang-hungarian' is not installed, so not removed
Package 'texlive-lang-indic' is not installed, so not removed
Package 'texlive-lang-italian' is not installed, so not removed
Package 'texlive-lang-latin' is not installed, so not removed
Package 'texlive-lang-latvian' is not installed, so not removed
Package 'texlive-lang-lithuanian' is not installed, so not removed
Package 'texlive-lang-mongolian' is not installed, so not removed
Package 'texlive-lang-norwegian' is not installed, so not removed
Package 'texlive-lang-other' is not installed, so not removed
Package 'texlive-lang-polish' is not installed, so not removed
Package 'texlive-lang-portuguese' is not installed, so not removed
Package 'texlive-lang-spanish' is not installed, so not removed
Package 'texlive-lang-swedish' is not installed, so not removed
Package 'texlive-lang-tibetan' is not installed, so not removed
Package 'texlive-lang-vietnamese' is not installed, so not removed
Package 'texlive-latex3' is not installed, so not removed
Package 'texlive-metapost' is not installed, so not removed
Package 'texlive-music' is not installed, so not removed
Package 'texlive-omega' is not installed, so not removed
Package 'texlive-plain-extra' is not installed, so not removed
Package 'texlive-publishers' is not installed, so not removed
Package 'texlive-science' is not installed, so not removed
Package 'texlive-xetex' is not installed, so not removed
The following packages will be REMOVED
  fonts-lmodern* lmodern* prosper* tex-common* texlive-base* texlive-binaries*
  texlive-extra-utils* texlive-font-utils* texlive-generic-recommended*
  texlive-latex-base* texlive-latex-base-doc* texlive-latex-recommended*
  texlive-latex-recommended-doc* texlive-pictures* texlive-pictures-doc*
  texlive-pstricks* texlive-pstricks-doc*
0 to upgrade, 0 to newly install, 17 to remove and 0 not to upgrade.
After this operation, 499 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 225896 files and directories currently installed.)
Removing lmodern (2.004.4-3) ...

update-language failed. Output has been stored in
/tmp/checkrun.wczUI74L
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.lHIOSbxS
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for lmodern (2.004.4-3) ...
Removing fonts-lmodern (2.004.4-3) ...

update-language failed. Output has been stored in
/tmp/checkrun.GybgUsNf
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.u7BXjl8T
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-language failed. Output has been stored in
/tmp/checkrun.ZrIg4owA
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.zO1Tlwvv
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for fonts-lmodern (2.004.4-3) ...
Removing prosper (1.00.4+cvs.2007.05.01-4) ...

update-language failed. Output has been stored in
/tmp/checkrun.T02sV4jh
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.3f7YyUv7
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Running 'mktexlsr /usr/share/texmf /var/lib/texmf'.
This may take some time... done.
Purging configuration files for prosper (1.00.4+cvs.2007.05.01-4) ...
Removing texlive-pstricks-doc (2014.20140717-1) ...

update-language failed. Output has been stored in
/tmp/checkrun.smvByZum
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.COJY2Uyp
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-pstricks-doc (2014.20140717-1) ...
Removing texlive-pstricks (2014.20140717-1) ...

update-language failed. Output has been stored in
/tmp/checkrun.NZPhepuG
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.o3o5HGqQ
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-pstricks (2014.20140717-1) ...
Removing texlive-pictures-doc (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.Sr6I9GaN
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.qBLtbJ3g
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-pictures-doc (2014.20140717-01ubuntu1) ...
Removing texlive-pictures (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.0KsQCCcN
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.Fs1IhuXg
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-pictures (2014.20140717-01ubuntu1) ...
Removing texlive-latex-recommended (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.kTDzaaxF
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.6XlnaAqL
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-latex-recommended (2014.20140717-01ubuntu1) ...
Removing texlive-extra-utils (2014.20140717-1) ...

update-language failed. Output has been stored in
/tmp/checkrun.qqxuPxSe
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.mfHakRZi
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-extra-utils (2014.20140717-1) ...
Removing texlive-font-utils (2014.20140717-1) ...

update-language failed. Output has been stored in
/tmp/checkrun.rJx5TEBL
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.VfQaSzF0
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-font-utils (2014.20140717-1) ...
Removing texlive-generic-recommended (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.ddEqCOhw
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.78TFPfN3
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-generic-recommended (2014.20140717-01ubuntu1) ...
Removing texlive-latex-base (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.B1DowVc2
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.YZU2eZv5
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-latex-base (2014.20140717-01ubuntu1) ...
Removing texlive-latex-base-doc (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.DKAu8hdW
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.oLg8E5Mo
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-latex-base-doc (2014.20140717-01ubuntu1) ...
Removing texlive-latex-recommended-doc (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.spYTMLIB
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.rY23Q7RW
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-latex-recommended-doc (2014.20140717-01ubuntu1) ...
Removing texlive-base (2014.20140717-01ubuntu1) ...

update-language failed. Output has been stored in
/tmp/checkrun.RGFrWBB9
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.


update-fmtutil failed. Output has been stored in
/tmp/checkrun.H707imOO
If tex-common is not configured you can ignore this error message!
Otherwise, please include this file if you report a bug.

Purging configuration files for texlive-base (2014.20140717-01ubuntu1) ...
Removing texlive-binaries (2014.20140528.34243-5) ...
Removing tex-common (5.02) ...
Purging configuration files for tex-common (5.02) ...
Processing triggers for fontconfig (2.11.1-0ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for install-info (5.2.0.dfsg.1-4) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 2 removed doc-base files...
Registering documents with scrollkeeper...

---

### Post by joeqesi on 2014-08-20
So in the end I just got annoyed and backed up my files so I could do a clean reinstall of 14.04. Everything seems to work nicely now.

---

### Post by GoPool on 2014-08-20
> **joeqesi said:**
> So in the end I just got annoyed and backed up my files so I could do a clean reinstall of 14.04. Everything seems to work nicely now.

To get a working copy of Tex (2014 or 2013) installed follow the information on [this page]("http://tplinux.blogspot.com/2014/07/installing-texlive-2014-and-using-latex.html").

---

