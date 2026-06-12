---
title: "Ubuntu 17.04 Displays Problem and dpkg"
date: 2017-05-15
forum: General Help
---

### Post by BulgarianBoy on 2017-05-15
Hello I upgraded from 14.04 to 17.04. I have two problems one was my Displays says " Could not get screen information." and my second problem is some packages wouldn't install. I was wondering if there is a way to get them installed after I skipped them?

```
moris@moris-laptop:~$ sudo apt-get dselect-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up tex-common (6.06) ...
Ignoring /etc/texmf/texmf.d/05TeXMF.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/15Plain.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/45TeXinputs.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/55Fonts.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/65BibTeX.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/75DviPS.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/80DVIPDFMx.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/85Misc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/90TeXDoc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/95NonPath.cnf during generation of texmf.cnf, please remove manually!




Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: Please see /usr/share/doc/tex-common/NEWS.Debian.gz
Warning: found file: /etc/texmf/updmap.d/00updmap.cfg
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-base.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-games.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-base.cfg


Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.5lmeFbsc
Please include this file if you report a bug.


Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory


dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-luatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-games:
 texlive-games depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-games (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-luatex
 texlive-games
 texlive-latex-base
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by vasa1 on 2017-05-16
> **BulgarianBoy said:**
> Hello I upgraded from 14.04 to 17.04. I have two problems one was my Displays says " Could not get screen information." and my second problem is some packages wouldn't install. ...
Please ask one question per thread. It is easier for other people to follow. Thanks!

---

