---
title: "Compromised, and curous over this package"
date: 2007-11-10
forum: General Help
---

### Post by paninero on 2007-11-10
A few months ago, I had a problem, took down my firewall and forgot to put it back up.  As a result I have been compromised on my system, and trying to find out the source and the problems.  Originally there was some problems with one of the gnome libraries had a few connections out to some servers on the internet, on which I ran a Nessus scan and those computers had a number of Trojans installed.

Now digging deeper today, I noticed that a program was listening on port 2208, and I got looking and I did not install this package, and it was installed on October 10th.  And I know I did not install anything in this timeframe, so either it either came in with autoupdate, or a person got inside my computer and installed it with apt-get.

As a side note, when I first realized I had been hacked was when I saw alot of samba shares open, and  that vncserver was installed, which when I use vnc I use tightvnc server, and there was a connection out to China somewhere, so that was my first clue.

I thought originally these packages came in with cups, since they were printer related, but I removed cups and the packaged and when installing cups-server they do not come back in.

i   hplip                        - HP Linux Printing and Imaging System (HPLIP)                                    
i   hplip-dat                  - HP Linux Printing and Imaging - data files

So first of all, I do not have an HP printer.  Second, the date being on October 10th is curious, since that is when I first noticed some problems.

Then after removal, I see these two files are no longer needed, so they must have been brought in at the same time:

python-qt3
python-sip4

Can someone else see if they have these packages, and they are supposed to be there.  Is it possible there is a vulnerability here that people are using to get into other peoples computers, where the culprit is a poisoned update cache?

---

### Post by floke on 2007-11-10
What about checking your apt-get history for Oct 10 - might yield clues as to exactly what was installed?

---

### Post by paninero on 2007-11-11
Yes, it was an upgrade for sure.  So it must have be pre-existing, but I am not sure why I even had it installed.

2007-10-13 15:17:20 upgrade hpijs 2.7.2+1.7.3-0ubuntu1 2.7.2+1.7.3-0ubuntu1.1

---

### Post by 11hjpphty76lkjj on 2007-11-13
hplip and hpijs come pre-installing with ubuntu--regardless of if you have an HP printer or not.  

not sure if that helps..

A

---

