---
title: "recent updates casuing sluggishness, video, java problems"
date: 2015-01-22
forum: General Help
---

### Post by jpvrlau on 2015-01-22
After recent updates, 48 hours prior to Jan 22 11AM,  I am experiencing general sluggishness.  Particularly noticing  difficuly viewing videos and doing searches from any brower.  Searches using Firefox respond with the following message:  "This page requires JavaScript. Get the non-JS version here".     I recall that the last update (from the updater) was from oracle  and it took forever to run when trying to unzip the package (details view).   It was listing completion status percentage wise on a line-by-line basis and took around 2 hours.    **** My 2 week old clone  does not have any  such issues. *****  What is going on?  Anyone else?   THANKS!    GIVEN: Ubuntu 14.04 Trusty  Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28  UTC 2015 (Ubuntu 3.13.0-45.74-generic 3.13.11-ckt13) Memory 3.7 Gib, Intel Core i5, CPU 650@3.20GHz x 4, Graphics Intel Ironlake Desktop, 64 bit

---

### Post by lisati on 2015-01-23
*Thread moved to **General Help**.*
Forum Feedback and Help is for reporting technical problems with the website here (i.e. broken features), or asking questions pertaining to forum features.

---

### Post by jpvrlau on 2015-01-23
Apparently problems were related to the Jan 21 updates.  The oracle/java components of the updates changed things up for Firefox primarily.  Javascript was enabled using "about:config" from the browser.  Then I turned to the java tester website  and worked it until I got it to list java-1.8.  I am assuming the primary fix was running "sudo update-alternatives --config java" which allowed me to use java-8-oracle in auto mode status.  This case may be peculiar to my Ubuntu and Firefox but I am reluctant to run updates on my earlier cloned drive for the time being.  Any comments, corrections or additional info are appreciated.

---

### Post by QIII on 2015-01-23
Hello!

How did you install Oracle Java?

---

### Post by jpvrlau on 2015-01-24
It appeared to me that the updater took the initiative and ran very slow.  I recall a tar/zip file being listed.  It's unpacking crawled listing 2%, 4%, ...  
Below is best I can find from the logs with an attached synaptic attachment.

This is the best I could find from the log files.  
2015-01-19 12:09:16 upgrade libmono-oracle2.0-cil:all 3.12.0-0xamarin2 3.12.0-0xamarin3
2015-01-19 12:09:16 status half-configured libmono-oracle2.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:16 status unpacked libmono-oracle2.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:16 status half-installed libmono-oracle2.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:16 status half-installed libmono-oracle2.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:17 status unpacked libmono-oracle2.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:09:17 status unpacked libmono-oracle2.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:09:17 upgrade libmono-oracle4.0-cil:all 3.12.0-0xamarin2 3.12.0-0xamarin3
2015-01-19 12:09:17 status half-configured libmono-oracle4.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:17 status unpacked libmono-oracle4.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:17 status half-installed libmono-oracle4.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:17 status half-installed libmono-oracle4.0-cil:all 3.12.0-0xamarin2
2015-01-19 12:09:17 status unpacked libmono-oracle4.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:09:17 status unpacked libmono-oracle4.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:11:31 configure libmono-oracle2.0-cil:all 3.12.0-0xamarin3 <none>
2015-01-19 12:11:31 status unpacked libmono-oracle2.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:11:31 status half-configured libmono-oracle2.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:11:31 status installed libmono-oracle2.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:11:32 configure libmono-oracle4.0-cil:all 3.12.0-0xamarin3 <none>
2015-01-19 12:11:32 status unpacked libmono-oracle4.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:11:32 status half-configured libmono-oracle4.0-cil:all 3.12.0-0xamarin3
2015-01-19 12:11:32 status installed libmono-oracle4.0-cil:all 3.12.0-0xamarin3
2015-01-21 19:39:32 upgrade oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1 8u31+8u33arm-1~webupd8~0
2015-01-21 19:39:32 status half-configured oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:32 status unpacked oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:32 status half-installed oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:33 status half-installed oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:33 status half-installed oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:34 status half-installed oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:34 status half-installed oracle-java8-installer:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:34 status unpacked oracle-java8-installer:all 8u31+8u33arm-1~webupd8~0
2015-01-21 19:39:34 status unpacked oracle-java8-installer:all 8u31+8u33arm-1~webupd8~0
2015-01-21 19:39:34 upgrade oracle-java8-set-default:all 8u25+8u6arm-1~webupd8~1 8u31+8u33arm-1~webupd8~0
2015-01-21 19:39:34 status half-configured oracle-java8-set-default:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:34 status unpacked oracle-java8-set-default:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:34 status half-installed oracle-java8-set-default:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:34 status half-installed oracle-java8-set-default:all 8u25+8u6arm-1~webupd8~1
2015-01-21 19:39:35 status unpacked oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0
2015-01-21 19:39:35 status unpacked oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0
2015-01-21 19:40:28 configure oracle-java8-installer:all 8u31+8u33arm-1~webupd8~0 <none>
2015-01-21 19:40:28 status unpacked oracle-java8-installer:all 8u31+8u33arm-1~webupd8~0
2015-01-21 19:40:28 status half-configured oracle-java8-installer:all 8u31+8u33arm-1~webupd8~0
2015-01-21 23:03:16 status installed oracle-java8-installer:all 8u31+8u33arm-1~webupd8~0
2015-01-21 23:03:16 configure oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0 <none>
2015-01-21 23:03:16 status unpacked oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0
2015-01-21 23:03:16 status unpacked oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0
2015-01-21 23:03:16 status unpacked oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0
2015-01-21 23:03:16 status half-configured oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0
2015-01-21 23:03:21 status installed oracle-java8-set-default:all 8u31+8u33arm-1~webupd8~0

---

