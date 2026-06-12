---
title: "ppa and ubuntu software center"
date: 2016-10-31
forum: General Help
---

### Post by jgw on 2016-10-31
I was wondering.  If I want to install a program there seems to be 2 ways to have at it.  However, if one googles, say, "ubuntu 16.04 install xxx" there is this flood of stuff.  In that stuff there are usually lines to install a ppa.  I have also noticed that ppa's tend to make problems.  My question, however, is pretty simple.  If something is installed, through the ubuntu software center, I think that would mean that the program no longer needs a ppa as its taken care of automatically?

I should also probably mention that I just upgraded to 16.04 on my wife's little eee pc 1005hab and I am having problems.  One of them is that I can have it run the ubuntu software center but, when it comes up, there is only a blank page for where the stuff usually is and it just sits there with the little loading circle spinning and nothing else happening.  So I am considering just installing with the command line thing.  However, if I do that would the program (copyq) automatically get updated just as if it was installed by the ubuntu software center?

I should also mention that the ubuntu software center is, obviously, trying to do something but it looks as if its going to do that forever.  I do have the multiload indicator running and it shows me that the load color is solid although the load itself is only at 2.41 (was over 5.??) but the cpu use is at 92%  The network is doing little or nothing so, I think, this would mean that something is using a LOT of system resources.  When I look at the system monitor it tells me that the software-center is using 43% of the cpu, compiz 18, and about 4 other things runnning 2 to 1% of the cpu thing.  I am, obviously, confused and ignorant on this stuff.  All I really know is that this machine seems to be doing much but I can do just about nothing.  The only programs actually running is the system monitor and the sofware center.

So, this started out just trying to install a program and ended up with a slow system whine - sorry about that, I really do try and keep issues single and specific - apologies....

---

### Post by Dennis N on 2016-10-31
> My question, however, is pretty simple. If something is installed, through the ubuntu software center, I think that would mean that the program no longer needs a ppa as its taken care of automatically?

Basic principle: If you have several software sources for the same package, the update-manager will offer the newest version when it checks for updates, wherever it is found. You can disable any PPAs you don't want to use and rely just on the version in the Ubuntu repositories.

You may want to try Synaptic Package Manager to handle installation of packages if you have problems with Ubuntu Software Center. It is very reliable.

---

### Post by ian-weisser on 2016-10-31
> **jgw said:**
> If something is installed, through the ubuntu software center, I think that would mean that the program no longer needs a ppa as its taken care of automatically?

Almost.
*Software packages* come from *sources*. Sources are important.

PPAs are one set of *sources.* PPAs are provides by individuals or small teams. They are supported by whomever put it out there, not the Ubuntu community. They are considered non-Ubuntu software, even though they use packages. You are the tester. If you run into a problem, you are on your own.

The Ubuntu Repositories are a different set of *sources*. They are supported by Canonical (main) or the Ubuntu Community (universe). They are tested by the Ubuntu Testing Team and patched my the Ubuntu Security Team..

The same software (LibreOffice) can come from either kind of source.
Software Center will see software from all sources that your system know about.

We generally recommend sticking with the Ubuntu Repositories, unless your intent is to help test PPA software.



> **jgw said:**
> So I am considering just installing with the command line thing.  However, if I do that would the program (copyq) automatically get updated just as if it was installed by the ubuntu software center?

Yes.
Software Center and Synaptic and apt and aptitude are all merely front-ends for the same package management system.
Your system does not track nor care which tool you use to install a package.
The package manager will offer to upgrade all installed package for which an upgrade is available.

---

### Post by jgw on 2016-11-01
Thank you for the replies.  

My questions have been answered - I will mark this one as solved.

---

