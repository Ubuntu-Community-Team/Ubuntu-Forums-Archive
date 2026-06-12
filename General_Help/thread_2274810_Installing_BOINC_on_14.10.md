---
title: "Installing BOINC on 14.10"
date: 2015-04-22
forum: General Help
---

### Post by ranger5 on 2015-04-22
Let me start by saying that I'm absolutely new to Ubuntu and Linux.  I decided to start working my way over from the dark side by setting up two Virtual Box Ubuntu machines, one 14.04 LTS and the other 14.10.  The installations went well and both machines are running quite well.  I installed GNOME Flashback on both because I'm more familiar with how the dark side works and I was looking for something familiar yet different.  Enough about that.

On my host machine I run an application called BOINC from the University of California at Berkeley ([http://boinc.berkeley.edu/download_all.php](http://boinc.berkeley.edu/download_all.php)) and I wanted to run it on the Ubuntu machines.  According to the BOINC website the Recommended version (read this as the stable version) is 7.2.42.  When I installed on the 14.04 machine this is what I got.  When I installed on the 14.10 machine I got version 7.4.8 which turns out to be newer and a bit buggy.  I used the command apt-get install BOINC on both machines, just minutes apart.  There are two components installed, the boinc-client which runs as a daemon (this installed and runs fine on both machines) and boinc-manager which is the GUI to manage and review activity (this is the buggy one in version 7.4.8).

I tried installing the specific version I wanted using apt-get install boinc=7.2.42 to which I was informed that this version was not found.  I then used apt-get policy boinc on the 14.04 machine and found out the version is actually 7.2.42-dfsg-1, but adding this version info to apt-get install did not produce a different result.  The Ubuntu Software Center has the same version.  It seems that either the utopic package repository does not contain the stable release or I am doing something wrong.  I would happily admit my error if someone can help.

---

### Post by ian-weisser on 2015-04-24
Congratulations, you have just discovered how a Linux distro works.

Every six months Ubuntu take a snapshot of the current software available and builds the distro from that snapshot.
Older versions are ignored.
Newer versions are ignored.
There are lots of good historical and limited-resources reasons why Ubuntu (and most other distros) work this way.

But the upshot for you is if you use packages, Application version X will generally only work on the corresponding Ubuntu version X.
"It's buggy" is a good reason to report bugs to upstream application developers, and a good reason to help test new versions so that functioning versions get snapshotted into Ubuntu.

Can you use Application version Y with Ubuntu version X? Sure you can, but you must use older, harder install methods to do so. Those methods have their own learning curves and shortcomings...that led to the package-based system we use today.

You can *try* installing a package from a different Ubuntu repository. You will need to use the command line to do that - it's advanced voodoo. And it might fail - the package may or may not be simply incompatible.

You can try installing the upstream binary (if they provide one) from their website. This is called *installing manually*.

You can try creating your own binary to manually install from the upstream source code. This is called *compiling from source*.

---

### Post by ranger5 on 2015-04-25
14.04 LTS repository has BOINC version 7.2.42 which works fine.  14.10 repository has BOINC version 7.4.8 which does not work correctly and 15.04 repository has BOINC version 7.4.23 which has the same problem.  The problem is with the BOINC Manager application, the BOINC Client application seems to be working correctly.  The BOINC Manager application is used to view what the BOINC Client is doing as well as to set certain program parameters.  When BOINC Manager is in advanced view and the tasks tab is selected, the active task(s) display the percentage of work done on the task(s), how long the task(s) have been running and how much time remains to completion.  This information refreshes at about every 1 second.  At least this is how it is supposed to work.  Also, the official recommended version of BOINC from UC Berkeley is that which is delivered with 14.04 LTS, version 7.2.42.  The versions that are delivered through the 14.10 and 15.04 repositories are identified as [COLOR=#FF0000][FONT=Trebuchet MS]**MAY BE UNSTABLE - USE ONLY FOR TESTING**[/FONT][/COLOR].  Can we have the stable version in the repositories instead of the unstable ones?

---

### Post by ranger5 on 2015-04-25
> **ian-weisser said:**
> Congratulations, you have just discovered how a Linux distro works.

Every six months Ubuntu take a snapshot of the current software available and builds the distro from that snapshot.
Older versions are ignored.
Newer versions are ignored.
There are lots of good historical and limited-resources reasons why Ubuntu (and most other distros) work this way.

But the upshot for you is if you use packages, Application version X will generally only work on the corresponding Ubuntu version X.
"It's buggy" is a good reason to report bugs to upstream application developers, and a good reason to help test new versions so that functioning versions get snapshotted into Ubuntu.

Can you use Application version Y with Ubuntu version X? Sure you can, but you must use older, harder install methods to do so. Those methods have their own learning curves and shortcomings...that led to the package-based system we use today.

You can *try* installing a package from a different Ubuntu repository. You will need to use the command line to do that - it's advanced voodoo. And it might fail - the package may or may not be simply incompatible.

You can try installing the upstream binary (if they provide one) from their website. This is called *installing manually*.

You can try creating your own binary to manually install from the upstream source code. This is called *compiling from source*.



It appears that when the snapshot was taken for 14.10 and subsequently for 15.04, instead of taking the current Recommended version of BOINC they took the current (MAY BE UNSTABLE - USE ONLY FOR TESTING) version.

I tried installing using the advanced voodoo.  It failed.  I tried installing manually (their website recommends against it).  It failed.  I'm not ready to compile my own.  

I went to the BOINC forums and asked for help.  They said that Ubuntu got it all wrong by providing the potentially unstable releases.

I guess if I want fewer frustrations I should go back to Windows?

---

### Post by ian-weisser on 2015-04-25
> **ranger5 said:**
> I tried installing using the advanced voodoo.  It failed.  I tried  installing manually (their website recommends against it).  It failed.   I'm not ready to compile my own.

That's probably why a fairly robust Debian/Ubuntu community of users packages BOINC instead of forcing all users to go through that frustration.
Those packaging volunteers work really hard to make BOINC work for everyone.

Generally, it's a good idea to file a bug report if the software isn't working. The BOINC community cannot help you, or improve the packaging, if they don't know about your problem.
All we can tell you is the boinc-client seems to build properly, install properly, and execute all of it's automated build tests properly. Or it wouldn't be in the Ubuntu repositories.
You can find the bugs that Ubuntu users have reported at [https://bugs.launchpad.net/ubuntu/+source/boinc](https://bugs.launchpad.net/ubuntu/+source/boinc)


> **ranger5 said:**
> It appears that when the snapshot was taken for 14.10 and subsequently for 15.04, instead of taking the current Recommended version of BOINC they took the current (MAY BE UNSTABLE - USE ONLY FOR TESTING) version.

I went to the BOINC forums and asked for help.  They said that Ubuntu  got it all wrong by providing the potentially unstable releases.

Blame of that sort is usually unhelpful. We can go on for days here about the difference between experimental, testing, and stable software, about which type Debian (not Ubuntu) pulls the source for and when, about which gets synced into Ubuntu and when, about how all along the chain are tests and QA and lots of volunteers working hard, about how broken software gets identified and reverted, and about how opinions run strong in many open source projects and how volunteers love to tell you what we think.

None of that will help you get boinc-client working.


If you are running into BOINC bugs that are not already reported, please report them to the bug tracker.
If you are running into BOINC bugs that are already reported, then please click the 'affects me too' link on the bug report, subscribe to the bug, offer to help upstream the bug, and offer to help test solutions when they become available.
If you are running into apt problems trying to install/uninstall boinc packages, please show us a complete terminal output showing what exactly what you did and exactly what error occurred so we can reproduce it.

---

### Post by ian-weisser on 2015-04-26
This seems rather similar to your previous thread: [http://ubuntuforums.org/showthread.php?t=2274810](http://ubuntuforums.org/showthread.php?t=2274810)

Is that missing task detail the only bug?

Have you checked launchpad.net to see if the bug has already been reported?
If so, has anyone Triaged the bug? Or upstreamed the Triaged bug to Debian? Has the Debian maintainer upstreamed the bug to BOINC?
If not, have you reported the bug to launchpad.net to start the process?

Have you contacted the Debian maintainer with the upstream claim (with reference) that Debian is using an inappropriate version?

The process for reporting a package in the Ubuntu repositories with serious problems that require a post-release repackaging is detailed at [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

I'm not trying to smother you with bureaucracy. I navigate these waters regularly. This is how you get software fixed if you're not a developer or authorized uploader.
The volunteers at the various levels (Ubuntu, Debian, BOINC) will need to verify each bug or claim. That may take time - they are volunteers with different lives and different setups.
Their judgement of the severity of the bug may disagree with yours - keep a thick skin.

---

### Post by oldos2er on 2015-04-27
Threads merged. Please don't create more than one thread for the same or similar questions; it's confusing and it dilutes the community's ability to help.

---

