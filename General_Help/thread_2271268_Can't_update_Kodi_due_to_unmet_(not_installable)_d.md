---
title: "Can't update Kodi due to unmet (not installable) dependancy libyajl2 (&gt;= 2.0.4)"
date: 2015-03-28
forum: General Help
---

### Post by bullwinkle2 on 2015-03-28
[B]EDIT: This issue was resolved by a later Kodi update that fixed the problem.  Thanks!
[/B]
I'm running Ubuntu 12.04 LTS and I really don't want to upgrade because this system is actually working the way I want, and every time I have upgraded in the past I have created a bunch of headaches for myself.  That's why I went with a LTS version this time, to put off the pain of an upgrade as long as I possibly can.

Anyway, to get to the problem at hand, update manager notified me that there are updates available for kodi and kodi-bin, but I cannot check the boxes to select them for installation.  I have never seen that happen before so I thought I'd try installing from the terminal.  This is what happened:

> $ sudo apt-get install kodi kodi-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kodi-bin : Depends: libyajl2 (>= 2.0.4) but it is not installable
E: Unable to correct problems, you have held broken packages.

I have no idea what to do to correct this.  Is there anything I can do that won't screw up my system?

The repositories being used for Kodi are the team-xbmc repositories ([http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) precise main) including the sources, if that makes any difference.

I'm basically just a user of Ubuntu, not a coder or anything, so I'm lost on how to deal with this.

---

### Post by TheFu on 2015-03-28
a) make a backup of everything you want to keep so you can put it back. This should be standard.
b) run **sudo apt-get update** - obvious reasons
c) run **sudo apt-get dist-upgrade**  - bring every program up to the current levels and install the latest kernel.

That should do it.  Here's the minimum stuff everyone should do to maintain their Ubuntu systems: [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) - republished by lifehacker.com.

While I don't touch my XBMC/Kodi box weekly, like i patch internet facing servers. I do patch it monthly with those commands to keep it current.  I would warn you that when support for 12.04 ends in 2017, most people will have moved to 14.04 or 16.04 and won't remember the minor issues in the 12.04 ---> next LTS upgrade.  That knowledge is starting to fade now.  I'm an LTS-only guy too - sometimes it is better to do the big update sooner than later.  

A few weeks ago, I had to spend about 14 hrs upgrading an enterprise email server from 10.04 to 14.04. The email system required 7 installations 5 of the same version, just with different binaries for 10, 12, and 14.04 systems.

Wish I could recall the 12.04 to 14.04 update on my XBMC machine - there were a few, tiny issues, but most things "just worked" on my AMD fusion-based mini-ITX box. It was nothing like the first few years where every tweak had to be manually done and a 30 pg how-to was needed to get it working.

---

### Post by bullwinkle2 on 2015-03-28
Please reread the first paragraph of my OP.  I do NOT wish to upgrade to 14.04 at this time.  What's the point of using a LTS version if it's not supported for the full five years?

I will never understand why it is that when you take the trouble to explicitly explain that you don't want to go down a particular path, the first reply you get is invariably to do the thing you just said you don't want to do.  And why this is particularly a problem in Linux-based forums.  I'll bet if I had asked "tell me how to upgrade to 14.04 to fix this problem", the first response would have been "you don't need to do that just to fix this problem, here is all you need to do".  THAT is the response I'd like to see now.

Realistically, the reason I don't want to run 14.04 is because I have an application that I use frequently, that is not available for anything newer than 12.04.

---

### Post by sandyd on 2015-03-29
The commands don't install 14.04. They update your Ubuntu packages to the latest version.

---

### Post by TheFu on 2015-03-29
> **bullwinkle2 said:**
> Please reread the first paragraph of my OP.  I do NOT wish to upgrade to 14.04 at this time.  What's the point of using a LTS version if it's not supported for the full five years?

Realistically, the reason I don't want to run 14.04 is because I have an application that I use frequently, that is not available for anything newer than 12.04.

I understood the OP and provided commands to help. Then I attempted to explain what 'dist-upgrade' does, but that wasn't understood for some reason. "Support" means patches. If you don't actually patch from time to time, you aren't using the support. Those commands will patch, nothing more.

Don't believe me?  **man apt-get**

---

### Post by bullwinkle2 on 2015-03-29
Sorry, I took "c) run **sudo apt-get dist-upgrade**  - bring every program up to the current levels and install the latest kernel." to mean that it would upgrade Ubuntu to 14.04.  However, it appears that the Kodi people have fixed the issue, because when I ran update manager again this morning it allowed me to do the update with no problem.

I just don't like getting lectured when all I am asking for is simple information.  "TheFu", if you had spent more time explaining what **sudo apt-get dist-upgrade** actually does, and less time trying to convince me that I need to do something I had explicitly said I'm not ready to do, we would not have had this confusion.

sandyd, thanks very much for the clarification!

Since my issue is now resolved I will not be following this thread, nor further responding to it.  Thanks.

---

