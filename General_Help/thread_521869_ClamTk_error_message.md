---
title: "ClamTk error message"
date: 2007-08-09
forum: General Help
---

### Post by mrk112 on 2007-08-09
I've just installed ClamTk 2.32 and ClamAV.. 

I've run freshclam to make sure that I have up-to-date definitions, however everytime I start ClamTk I am presented with the following error:

> Warning: No virus definitions found! If you are sure you have definitions installed, please inform the developer where your definitions are held so the paths can be added.

Does anyone know how to resolve this issue?

Thanks.

---

### Post by mrk112 on 2007-08-10
Anyone?

---

### Post by TomG on 2007-08-11
Have same problem when running ClamTK. Signatures not found but update says it is OK. 

In terminal I tried :
  sudo freshclam -v
and then 
  clamscan

And signatures seem ok :
----------- SCAN SUMMARY -----------
Known viruses: 145181

Could be a ClamTK (GUI) problem. You may try Klamav instead...

---

### Post by jonathan22 on 2007-09-02
I'm having the same problem:  ClamTk can't find signature files.  Here's what I've found so far.
The short version is I believe the problem may be due to a change in ClamAV files (main.cvd is my guess) and that a later version of ClamTk addressed the problem.  I'm not sure whether version 2.32 of ClamTk -- an update which is available in Feisty-backports -- did the trick, however.   (At least I'm still having the issue.)  The current version is 3.01, just released 8/30, isn't available in Ubuntu repositories yet.

A ClamTk readme file dated 6/3/07 noted our problem is due to a change in ClamAV files:

(Start of quote from [http://clamtk.sourceforge.net/README](http://clamtk.sourceforge.net/README))

14. Troubleshooting

* If you are getting an error that ClamTk cannot find your signatures:

  ClamTk is trying to find daily.cvd and main.cvd. Typically these are
  held under /var/lib/clamav or /var/clamav or ... If you are sure these
  files exist, please find their location and send it to me.
  Try one of the following to determine their location:

  1. locate daily.cvd
  2. find /var -name "daily.cvd" -print

  Of course, this all changed, I believe, with the 0.90 series. When I can
  figure out what the rhyme and reason is, I'll make sure it's fixed!

(End of quote)  

ClamTk's current list of version changes indicates that version 2.32 included fixes on this issue:

(Start of quote from [http://clamtk.sourceforge.net/CHANGES](http://clamtk.sourceforge.net/CHANGES))

2.32:
	* Several more fixes, all affecting ClamAV 0.90 users.
	  This will likely be the last 2.* release, barring any major
	  problems.
	  Thanks to Reid T. for his generous time and help! 

(End of quote)

But, as mentioned, I'm still having the issue.  

My ClamAV Ubuntu package is 91.1-1.  Possibly ClamAV changes after .90 are the cause...  The main.cvd file that ClamTk seems to look for isn't in var/lib/clamav.

Wish I had this problem solved, but wanted to pass along what I found so far.

---

### Post by Juraj Cerven on 2008-03-03
Hello,

this post is probably too late, but I've had the same problem a couple of weeks ago and I want to publish the found solution on the web. 

I am using** Ubuntu Gutsy **form the December 2007 as a novice.

After a lot of Googling I have downloaded **libconfig-tiny-perl_2.10-1_all.deb **from official Gutsy repository and **clamtk_3.08-1_all.deb** from the Hardy repository.

This corrected the behavior of ClamTk. If I want to refresh virus signatures, I start Clamtk from console: "sudo clamtk", otherwise I start it from menu.

Best regards
Juraj

---

### Post by marc.m on 2008-04-22
Late, but maybe will help someone in the future.  For Ubuntu 7.10 Gutsy Gibbon a solution can be found here.
[https://answers.launchpad.net/ubuntu/+source/clamtk/+question/25716]("https://answers.launchpad.net/ubuntu/+source/clamtk/+question/25716")

---

