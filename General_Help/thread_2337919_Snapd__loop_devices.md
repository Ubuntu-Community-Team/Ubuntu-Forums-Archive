---
title: "Snapd  loop devices"
date: 2016-09-22
forum: General Help
---

### Post by expatver on 2016-09-22
Ubuntu 16.04 LTS fully updated , Unity desktop.  

I have asked this question before here, have done a search here and have read a bit on Snapd but my question remains-

Using Gnome disk utility I find 4 virtual disks- they are called "loop devices"..... They are

/var/lib/snapd/snaps/ubuntu-core_352.snap   78 MB

/var/lib/snapd/snaps/ubuntu-core_216.snap  76 MB

/var/lib/snapd/snaps/ubuntu-core_423.snap  79 MB

/var/lib/snapd/snaps/alsa-utils_1.snap            4.6 MB

This may be a dumb question but I ve not been able to find why these loop devices exist.  I use Synaptic package manager or apt to do all updates on this machine. I have never used Snapd.

Anyone else have these, why are they there if one doesnt use Snapd. Can they be deleted without fear of  Armageddon? While I am not out of disk space , I dont think its good system administration  to have something appear as a loop device without knowing what and why and/or simply ignore it. 

Regards

Expat

---

### Post by jpvrlau on 2017-02-21
I have the same questions since I see that the results from a df command reflects this new technology.  I perused around but cannot find anything definitive as to what they provide, why they have been introduced, and what the user needs to know about snaps and loops.  Pardon my ignorance.

$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1912876        0   1912876   0% /dev
tmpfs             386608     6624    379984   2% /run
/dev/sda5      273057176 65856948 193306660  26% /
tmpfs            1933024      416   1932608   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            1933024        0   1933024   0% /sys/fs/cgroup
tmpfs            1933024      688   1932336   1% /var/log
/dev/loop0        117888   117888         0 100% /snap/vlc/4
tmpfs            1933024        0   1933024   0% /var/tmp
tmpfs             524288     1212    523076   1% /tmp
tmpfs            1933024        0   1933024   0% /var/log/apt
/dev/loop3         77952    77952         0 100% /snap/core/1240
/dev/loop2         77952    77952         0 100% /snap/core/1222
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             386608       76    386532   1% /run/user/1000
/dev/loop4         77952    77952         0 100% /snap/core/1264

---

### Post by expatver on 2017-02-21
[COLOR=#000000]jpvrlau[/COLOR]
[COLOR=#000000]Hi. Dont feel bad about asking.  I asked on Sept. 22 2016.  System this is running on is a production system with limited disk space , I have about 338 GB free out of a terrabyte.  I sat around waiting for some of the experts to reply and either they dont know or they dont care. Finally I used Synaptic package manager to delete Snapd.  I caution you about doing something  such as a remove or complete remove unless you are willing to risk  either a lot of work to get the system stable again or reload it. In my case, since i have been running various  distros of both Unix and Linux for a desktop for  30 years (yes AT&T Unix Berkley distro  did crude windowing  on a workstation with  a Motorola 68000 series CPU--my first windowing computer) I will sometimes break things and then manage to fix them.  You can remove Snapd, the snapd login service, and libsnapd-glib1. As I recall (since it was probably Sept. 24th and I did NOT enter it in the system log, but it probably is in  the Synaptic log.....) it was a clean remove and freed up some disk space, got rid of the loops on the HD. If you have Synaptic, remove everything snapd.  If you do not have synaptic  then sudo apt-get update and sudo apt install Synaptic should get you the package manager.  I use either Aptitude, apt or Synaptic  on my system  to make sure dependencies are handled. Aptitude is the most through but can cause problems because it is aggressive,  apt is better from the terminal and Synaptic works well since it has a nice GUI front end.  Hope all of this helps. 

 I am happy to address your question. I dont know how good my advice is, use at your own risk. I am going to comment on this forum at this juncture. We in the Open Source community hope that eventually  more people will start to use Ubuntu and other distros  for desktop, an area Microsoft dominates.  One problem with this is  the OS must be usable by some people who have a problem using a refrigerator or a toaster.  While arguably we are still a bit away from that,  it is damaging when someone comes to  supposedly the authority forum with all of the experts, asks about a latest and greatest improvement in the distro--snapd- and gets ignored for lets see, since September 22nd.  It does not help our Open Source cause at all.  Just do NOT ask about systemd. Ever. 

Regards from Ecuador

Expat[/COLOR]

---

### Post by expatver on 2017-02-21
OK. Here is the Synaptic log from Sept 24th 2016

Commit Log for Sat Sep 24 17:50:33 2016




Removed the following packages:
snap-confine
snapd
ubuntu-core-launcher

------------------------------------------------------------------
I seem to recall having seen snapd in the daily updates for Synaptic recently and yes here it is

 Commit Log for Sun Feb 19 11:42:31 2017




Upgraded the following packages:
snap-confine (2.22.2) to 2.22.3
snapd (2.22.2) to 2.22.3
ubuntu-core-launcher (2.22.2) to 2.22.3
-------------------------------------------------------------------

So here is today just after posting my reply to you

Commit Log for Tue Feb 21 14:16:58 2017




Removed the following packages:
libsnapd-glib1
snapd
snapd-login-service


Upgraded the following packages:
tcpdump (4.7.4-1ubuntu1) to 4.9.0-1ubuntu1~ubuntu16.04.1

-------------------------------------------------------------------
One of the handy things about Synaptic is that if you can boot and Synaptic will run (provided something has not shredded dpkg)  it is an easy way to see what you did when. Since this is a production system though, I keep a separate system log.

Now. Question is why did snapd reinstall an updated package  if I ripped snapd out by the roots, yes? Back on September 24th of 2016? OK. Since right now I am lazy, I decided to find if there was any further snapd lurking after my second unisntall. So I opened a terminal and ran sudo Nautilus and when the file manager opened, I searched for snapd.  I found several folders and a bunch of files, highlighted them all and deleted then (OH!!! GOD!!!! THE HORROR!!!!). I dont recommend this particularly since I dont have any idea of your skill level and determination. Remember the enter key is the most dangerous key on the keyboard. However after removing  all of this gradu, I rebooted the machine...... I shut down and boot in verbose mode to  try to read the rapid text that flashes by and  spot problems. Clean reboot. So far operating normally.  I do NOT recommend that  you do the rip-it-out-by-the-roots removal that I did but.....on tis system it worked and hopefully I wont be bothered  by snapd again. 

Regards

Expat

---

### Post by george_udosen on 2017-05-07
If I may ask, did you not install the Ubuntu snapd service in the first place? I am thinking these start appearing after you, I and others like us installed it...

---

### Post by expatver on 2017-05-07
That is correct.  I did install it as part of a package, nothing that I specifically singled out  and no one said anything about snapd creating what to me look like virtual drives on my hard drive *without asking*. Yes I agreed to the potential  use of disk space in installing the package in the first place but the idea of virtual drives being created without consent, no! The same way that there are various  processess that look at (at least on *TWO* machines with 16LTS that I had)  the contents of the hard drive for Ubuntu store.  Run iotop if you notice  lots of disk activity at startup and trace the  daemons, I think they are called tracers scanning the disk. My investigation revealed they were child processes  of Ubuntu Store. 

This is why I nuked and paved the  Ubuntu drive and installed another distro.  BECAUSE  no one said anything about  either the loop drives, the tracers, the emerging picture of Canonical seemingly trying to get into content providing and *the loss of control and  privacy that can engender* *in an operating environment* (same type of crap caused me to leave the OSX development community a number of years back). Apparently no one in *this* community was willing to talk about what looped drives  meant  (or simply did not know but I have trouble believing that)and what created them. Look at the date of my initial post and  the time involved  with no replies......  I am forced to use Windows 10 on the same machine  dual boot  for work  but my digital life is open Source. I absolutely  have no tolerance for  being burdened  with software and processes  that modify the system  without the modifications being evident and without me at least being informed or ASKED beforehand. I know this is  probably being whiney  and nit picking but Windows does this as a matter of course on the way to the lease model of operating systems- I have wire sharked Windows  and have seen the telemetry that goes back home.  Around the time I made my decision to leave  Ubuntu for another distro someone pointed me to Richard Stallman's article about how Ubuntu purportedly  collects search terms and sends them to Canonical. I did not wireshark Ubuntu to verify this but it cast further doubts on the veracity (for me at least) of continuing to care and feed an OS that called home. I spend a lot of machine time every day and do NOT have the time or inclination to parse code for snooping.  Intent is  almost always  indicated by changes and modifications especially in software. Last time I looked this was my machine and  with that precept I have the right and ultimate  say on what is done with it. With Windows 10 its a constant battle. Not one I am willing to fight with an OpenSource distro that installs  crap I dont want, need or approve of. Too much  like the Redmond crew. 

So if they are putting  virtual drives on my Hd without my  approval, indexing the drive at startup for Ubuntu store, and supposedly sending search terms home to Canonical all without asking if any of it is OK.......then what else is being done without the user being informed.  No more.

---

### Post by expatver on 2017-05-09
[https://linux.slashdot.org/story/17/05/09/1553255/canonical-founder-says-recent-changes-in-ubuntu-were-necessary-to-prepare-the-company-for-an-ipo](https://linux.slashdot.org/story/17/05/09/1553255/canonical-founder-says-recent-changes-in-ubuntu-were-necessary-to-prepare-the-company-for-an-ipo)

in case there was doubt.  So in the effort to get all aspects profitable for an IPO,  the invasiveness of the Ubuntu Store daemons, search term collection and snapd (which incidentally must be installed for the Ubuntu store to function).  And some months  later, this story.  Lets see how the profitability model  works for Ubuntu users concerned with privacy going forward.

---

### Post by QIII on 2017-05-09
I see that you did not bump your posts and simply let them sink to the bottom of the sea.  People will hardly go diving that deep to find buried treasure.  If you did not bump your thread after 12 hours with no response, it is not the fault of the community that you got no answer.  This is a world-wide volunteer community of people with real lives who come here as they have time.  That you got no answer is in no way indicative of any lack of knowledge or desire to assist you.  It is simply an indication that the right people with the right answers did not see it in the brief moments it was at the top of the pile.  As a matter of fact, some very lively discussion has taken place in the development sub-forum with regard to snaps, snapd and the loop devices.

Don't ask about systemd?  Apparently you have missed the discussions about that, too.  Some of them not so happy.

There is no need for the drama.  The sky is not falling.  We went through the FUD with the shopping lens and Canonical did not become Big Brother.  Take a breath and tone it down, please.

---

