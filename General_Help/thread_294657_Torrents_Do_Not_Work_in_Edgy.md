---
title: "Torrents Do Not Work in Edgy"
date: 2006-11-06
forum: General Help
---

### Post by alaren on 2006-11-06
Greetings.  I have been running Dapper for a little over a month (first time using Linux since 1997).  It was great; Beryl is fun, my wife even adapted to OpenOffice.  It has been a learning experience but I was able to get everything working as I hoped, mostly thanks to this community.  However, I tried the 6.10 upgrade... the built-in upgrader didn't work very well, so I decided to just do a fresh install.  

Ever since then, torrents hard lock my system.  That is, ANY and ALL torrents, after running for 10-30 seconds, hard lock my system.  This is with a fresh Kubuntu Edgy install using KTorrent, BitTornado, or Azureus.  This is with or without MoBlock installed and running.  Also occurs with a fresh Ubuntu Edgy install using BitTornado or Azureus.  I have tried saving on my EXT3 system partition and on an external USB FAT32 drive.  I have tried different ports.  Torrents worked fine in Dapper.  I have no other downloading problems--apt-get works fine, web works fine, ftp works fine.  Even GAIM works fine.  I am at my wit's end.

Everything else about Edgy I have found quicker and easier than Dapper (well, except the 100% CPU Beryl-Manager bug, but I'm sure that will be resolved soon enough).  But I keep booting back into Windows to download new ISOs of Linux!  I'd rather not go with a different distro (my friends are pushing Fedora on me) because I love the Ubuntu community.  So: 

Help me out!  What should I be checking?  I am an IT professional by trade (actually just quit that to start law school) so I'm not stupid but when it comes to Linux I'm pretty much a newb.  I don't see anyone else having this problem, so how can I find a fix for it myself?  I don't get any error messages at all--after a few seconds of downloading on any torrent, the system hard locks, no keyboard input, no mouse response, nothing.

Thanks in advance!

---

### Post by alaren on 2006-11-08
So I did a bit more digging and came up with similar issues [here]("http://ubuntuforums.org/showthread.php?t=161624") and [here]("http://ubuntuforums.org/showthread.php?t=160025&page=1").  It doesn't look like anyone has a conclusive, final answer--but the trend seems to be that everyone experiencing this issue has wireless cards.  The hard-lock however seems to make debugging difficult... but I don't know much about debugging.

Incidentally, I tried and tried, then I installed Fedora Core 6 which didn't support my wireless card, and now I'm back on Dapper with everything working great.

But it seems like an issue that crops up from time to time and ought to be addressed... I'd love more thoughts (or a fix if someone has found one!) because I'd like to upgrade, but Dapper seems about the best distro available at the moment.

---

### Post by WebDrake on 2006-11-10
> **alaren said:**
> But it seems like an issue that crops up from time to time and ought to be addressed... I'd love more thoughts (or a fix if someone has found one!) because I'd like to upgrade, but Dapper seems about the best distro available at the moment.
I have had a similar experience, although KTorrent didn't freeze things, just slow them down a lot while it was running (particularly the internet).  Though, when I examined the system with "top", it was X.org that was actually taking up the system resources (28% CPU, quite a bit of memory).

I think this has received some attention in the KTorrent community as well.  I'll try to post some links later.

---

### Post by WebDrake on 2006-11-10
There is info on the torrent problem at
[http://ktorrent.org/forum/viewtopic.php?t=966](http://ktorrent.org/forum/viewtopic.php?t=966)

Interestingly, I don't appear to have this issue when I'm running KTorrent over an office network (legitimate torrents only ;) ), but when I'm at home, accessing the net via my (cable-connected) router, it shows up.  Perhaps it's something to do with how Edgy interacts with routers.

---

### Post by alaren on 2006-11-15
Also looks like it is mentioned [here]("http://ubuntuforums.org/showthread.php?t=222050"), again with no solution, and again with wireless internet involved.

Is there some way to report this bug or see if it has been reported?  I would love to upgrade to Edgy, but at the very least I'd like to see this get some attention while Feisty is in development...

---

### Post by claydoh on 2006-11-15
You might be interested in trying out [jdong's svn  ]("http://www.buntudot.org/people/%7Ejdong/ktorrent/svn-edgy/")ktorrent debs, there are some definite improvements.

Just note that these packages are development snapshots and may be unstable, the more recent files may not necessarily be better. than newer ones.

Having said that, I have had better performance using the newest deb in edgy, and there are dapper packages too

---

### Post by alaren on 2006-11-16
Thanks, I may try that once I figure out SVN repos.  However, it really does look like the problem is in how Edgy handles wireless cards, particularly the Realtek 8180 chipset.

Additional information: when I install Dapper, I automatically see a list of wireless networks in my network setup.  In Edgy, I see no list; internet still works when I manually enter SSID and WEP key, but torrents crash my system completely.

So something apparently has changed from Dapper to Edgy with regard to wireless.  Maybe this will help us zero in on the problem?  I simply don't know enough about Linux development to dig much further than this, but I'd love to learn.

---

### Post by claydoh on 2006-11-16
No need for repos, just download one of the deb files, for example:
[http://www.buntudot.org/people/~jdong/ktorrent/svn-edgy/ktorrent_2.1~0dev+svn20061115-1~6.10prevu1_i386.deb](http://www.buntudot.org/people/~jdong/ktorrent/svn-edgy/ktorrent_2.1~0dev+svn20061115-1~6.10prevu1_i386.deb)
and install it manually

the 'svn20061115' part denotes the date it was built

As to wireless, I have yet to move on to wireless hardware so I don't have any experiences in that area yet, and i definitely don't know why torrents cause your lock ups

---

### Post by infogorf on 2006-12-04
Having the same problem as described above, but I am also at newbie. I anyone has any suggestion on how to solve this problem - pleaassse tell me :-)

---

### Post by mighty_scoop on 2007-01-03
Hi all, some days ago i updated my dapper system to edgy ... now i have the same problem as described above (also with wlan) ... is there still no solution ? 

Greetings

mighty_scoop

---

