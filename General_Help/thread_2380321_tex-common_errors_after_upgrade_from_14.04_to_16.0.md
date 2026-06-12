---
title: "tex-common errors after upgrade from 14.04 to 16.04"
date: 2017-12-15
forum: General Help
---

### Post by greyfaux01 on 2017-12-15
Well i upgraded from 14.04 to 16.04 using do-release-upgrade, everything went fairly smooth, couple packages were broke, but i reinstalled and now their working. Still some xfce panel problems that i'll make another thread for (unless someone can help me with that too in this thread, either way is cool with me). However, when i install a package now, or run a package/install related command, for example sudo apt-get install -f, i get a bunch of tex-common errors. I also get some 'max reports reached' errors in there too.. As per the ubuntu stackexchange, i deleted the files in /var/crash folder, yet still get the 'max reports reached' when i run these 2 (install -f, dpkg --configure a-, or install a package). Not sure if its related to the tex-common errors or not.

After the upgrade i already ran autoremove, if thats relevant at all. I hope i didnt screw myself by deleting old packages that i needed, but no repos seem to be broke. Updates seem to be working, as well as package installations, its just those errors that pop up.

Thanks for any help.

---

### Post by greyfaux01 on 2017-12-15
Heres an example of the error msg's that im having trouble with. In the past, probably after upgrading to 14.04, i had tex-common errors, and i remember it took me a long time to finally fix. Im not sure what exactly i did, or what it means in my particular case, so any help would be appreciated on this matter.

sudo apt-get install -f
```

jonny2@jonny2-OptiPlex-745:~$ sudo apt-get install -f
[sudo] password for jonny2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tex-common (6.04) ...
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
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-base.cfg


Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.fMNPEIqJ
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
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.


dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2015); however:
  Package texlive-latex-recommended is not configured yet.


dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-pictures (>= 2015); however:
  Package texlive-pictures is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2015); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
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
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
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
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base-doc (--configure):
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
 texlive-latex-recommended
 texlive-pictures
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-pictures-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonny2@jonny2-OptiPlex-745:~$ 

```


dpkg --configure -a
```

jonny2@jonny2-OptiPlex-745:~$ sudo dpkg --configure -a
Setting up tex-common (6.04) ...
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
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-base.cfg


Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.fDLROLNs
Please include this file if you report a bug.


Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory


dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.


dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base-doc (--configure):
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
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.


dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-pictures-doc
 prosper
 texlive-pstricks-doc
 texlive-pictures
 texlive-font-utils
 texlive-latex-recommended-doc
 texlive-generic-recommended
 texlive-latex-base
 texlive-latex-base-doc
 texlive-pstricks
 texlive-latex-recommended
 texlive-extra-utils
jonny2@jonny2-OptiPlex-745:~$ 

```

---

### Post by greyfaux01 on 2017-12-19
Please help?

---

### Post by vasa1 on 2017-12-23
Please post the entire outputs of```
sudo apt-get update
``````
sudo apt-get dist-upgrade
```(press "n" at the prompt of the latter command if you're uncomfortable)```
inxi -Fxz
```and```
inxi -r
```if you have *inxi* installed or```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by greyfaux01 on 2017-12-23
sudo apt-get update:
```

jonny2@jonny2-OptiPlex-745:~$ sudo apt-get update
[sudo] password for jonny2: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:4 http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial InRelease        
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease            
Hit:6 http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial InRelease       
Hit:7 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:8 http://archive.canonical.com xenial InRelease                            
Hit:9 http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial InRelease 
Hit:10 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease  
Ign:11 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ InRelease               
Hit:12 http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial InRelease
Hit:13 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease       
Hit:14 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial InRelease
Get:15 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ Release [988 B]
Hit:17 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease
Hit:18 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease          
Hit:19 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial InRelease
Fetched 988 B in 5s (167 B/s) 
Reading package lists... Done
jonny2@jonny2-OptiPlex-745:~$ 

```

sudo apt-get dist-upgrade
```

jonny2@jonny2-OptiPlex-745:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  virtualbox-dkms
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 624 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
jonny2@jonny2-OptiPlex-745:~$ 

```


grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

jonny2@jonny2-OptiPlex-745:~$ inxi -r
The program 'inxi' is currently not installed. You can install it by typing:
sudo apt install inxi
jonny2@jonny2-OptiPlex-745:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security universe
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://archive.canonical.com/ xenial partner
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list:deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/megasync.list:deb https://mega.nz/linux/MEGAsync/xUbuntu_16.04/ ./
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list:deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main #WebUpd8 disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/peterlevi-ppa-precise.list:deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/pipelight-stable-precise.list:deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list:deb http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list:deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
jonny2@jonny2-OptiPlex-745:~$ 

```



Thanks so much for your help. If you want i can always install inxi program, ive never heard of it, but if it can make life easier i'll do it. But if its command line only i'll probably not use it too much on my own.

Not sure this is relevant, but there was an update yesterday i think, through the gui, and i went ahead and did it, and it seemed to have worked, although there were errors at the end. Of course using the gui like a noob it didnt tell me what the errors were, just letting you know theres definately something fishy going on, but things seem to be working still..

Im only able to check the forums once a day or once every few days, but i wont just disappear, so again i appreciate your help, and im not just going to 'ghost' on you and waste your time.

---

### Post by oldos2er on 2017-12-23
Moved to General Help at user's request.

---

### Post by greyfaux01 on 2017-12-25
thanks oldos2er. cool terminal game in your sig too. i just checked it out. i guess i need to learn a few more commands to get into it more. i did realize im in the westernforest though

---

### Post by greyfaux01 on 2018-01-02
bump please.

---

### Post by greyfaux01 on 2018-01-09
bump

---

### Post by Yellow Pasque on 2018-01-09
[https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1514474](https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/1514474)

---

### Post by greyfaux01 on 2018-01-09
Ok thanks Temujin. I read the bug report thread, and followed the instructions posted by the last poster. I ran 'apt-get install -f' since theres no package updates at the moment, and didnt get any error messages this time. So it may have worked.

Its crazy following instructions from people on launchpad because i dont know their reputation or if the fix is a good fix, or will cause problems down the road. But i didnt see any other fixes, and it seemed similar to the previous fix that got a 'thanks flood', so i did it. Honestly, i can understand not wanting a 'thanks flood' in launchpad, but for outside observers, its great because i can judge how well someones fix is.. A lot of people throw out different fixes for the same problem, and usually the one with the most 'thanks', and the one that seems to make the least changes to my system, is the one i go with.

Anyway, thanks again. I'll have to wait till theres an actual update to see if its fixed (unless you already know its fixed, im no pro), but so far with the apt-get install -f it seems good.

---

### Post by greyfaux01 on 2018-01-09
ok just now popped up an update for some linux-headers, not sure if its related to the fix i just did, but i updated it with the gui, and didnt get an error message about tex-common finally.

Thanks for your help with this ubuntu bug.

---

