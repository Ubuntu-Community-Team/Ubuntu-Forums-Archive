---
title: "The #1 Ubuntu Bug - Packages Are Not Current"
date: 2008-05-13
forum: General Help
---

### Post by sb73542 on 2008-05-13
Hello all,

I have a bit of a complaint here... Please note that I am a long-time Ubuntu user, I have been registered here for years and I have used every version of Ubuntu since Warty.  Ubuntu has so many advantages over other distros that I really don't want to switch.  However, I am becoming increasingly frustrated with Ubuntu's packaging policies.  

Basically, Ubuntu does not update their packages until the next version six months later, unless the upgrade is a major security fix.  And even in that case, they have been known to ONLY port the security fix, and leave out any new features.  This is even the case with "universe" repositories, which are supposedly unsupported anyway.  And the backports repos are not a solution either, since they have very restrictive policies for backports, and I personally have never found updates that I need in backports.  It seems to me that they should stop doubting the creators of the software, and simply include the updates, since the creator probably knows better than Ubuntu what the bugs are in his own software.  By reviewing and submitting programs to a long review process, it seems that Ubuntu is just adding another level of complexity to an already complicated system.  The result of all this is that when a major program releases a big update two days after a new version of Ubuntu, the Ubuntu users have to wait six months to get it.  Why should it be necessary to upgrade an entire operating system just to update a program to the next version?

Here's a few examples:

**OpenOffice**
[http://packages.ubuntu.com/search?keywords=openoffice.org&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=openoffice.org&searchon=names&exact=1&suite=all&section=all)
*Current Official Version:* 2.4.0
*Gutsy Version:* 2.3.0
*Result:* Gutsy users are missing out on both 2.3.1 and 2.4.0, and have to upgrade their entire system to Hardy just to upgrade their office suite.

**VLC**
[http://packages.ubuntu.com/search?keywords=vlc&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=vlc&searchon=names&exact=1&suite=all&section=all)
*Current Official Version:* 0.8.6g
*Gutsy Version:* 0.8.6c
*Hardy Version:* 0.8.6e
*Result:* Gutsy users miss out entirely on .d .e .f and .g releases.  Hardy users miss out on .f and .g releases, and will have to wait until Intrepid to get a newer version

**Lyx**
[http://packages.ubuntu.com/search?keywords=lyx&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=lyx&searchon=names&exact=1&suite=all&section=all)
*Current Official Version:* 1.5.5
*Gutsy Version:* 1.5.3
*Hardy Version:* 1.5.3
*Result:* Gutsy users miss out on 1.5.4 and 1.5.5.  Hardy users are also stuck on 1.5.3 for no reason, and will have to hope that this gets noticed six months later for Intrepid.

See what I mean?  And if you want, compare these stats with the package listings at [http://rpm.pbone.net/](http://rpm.pbone.net/) , and you will find that Mandriva, SUSE, and Fedora generally have up to date packages within days of a new release from the program creator.

So, the point of this post is to ask: "What is the solution"?  Is anyone working on some big community repository, like PLF for Mandriva or Packman for SUSE?  Or will Ubuntu ever officially address this?  Or am I the only one who has noticed this?

Thanks for the help!

---

### Post by Het Irv on 2008-05-13
btw: That's not the #1 bug... 
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)

You can always get updates from the sites, but I agree that this is a weak point.

---

### Post by sb73542 on 2008-05-13
> **Het Irv said:**
> btw: That's not the #1 bug... 
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)

You can always get updates from the sites, but I agree that this is a weak point.

:) Ha, I knew somebody was going to call me on this one.

---

### Post by Bakon Jarser on 2008-05-13
I can understand why they do this for the LTS releases, they want it to be as stable as possible.  But I think they should definitely do this for the non-LTS releases.  I'd have probably stayed with Gutsy if I knew all of my programs would be updated right when the updates were available.

---

### Post by sb73542 on 2008-05-13
I don't know, the thing is that most of the program updates actually improve stability.

---

### Post by Het Irv on 2008-05-13
Yeah, but you never know if the build will be stable for Ubuntu.  I think it is done mainly because of the work involved in checking each version for stability.

---

### Post by chrisccoulson on 2008-05-13
Please see [this]("https://wiki.ubuntu.com/StableReleaseUpdates") wiki entry to gain an understanding of Ubuntu's update policy for stable releases.

Basically, once a release is stable, packages are only updated for security fixes and major bugs. Packages aren't updated for minor updates or feature enhancements - these go in to the latest development release. This is in order to maintain stability of the stable releases, and is a good policy.

If there are must-have features in a particular package, then you can request to have that package backported, if you can justify it ([https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by sb73542 on 2008-05-13
> **chrisccoulson said:**
> Please see [this]("https://wiki.ubuntu.com/StableReleaseUpdates") wiki entry to gain an understanding of Ubuntu's update policy for stable releases.

Basically, once a release is stable, packages are only updated for security fixes and major bugs. Packages aren't updated for minor updates or feature enhancements - these go in to the latest development release. This is in order to maintain stability of the stable releases, and is a good policy.

If there are must-have features in a particular package, then you can request to have that package backported, if you can justify it ([https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

Thanks for the reply.  I am aware of this policy, which is why I think we need 3rd party repositories that contain current software.

---

### Post by songshu on 2008-05-13
its a matter of choice, its either up to date or its rock stable for years to come.

although Ubuntu is not a 100% strict on the patch only idea it is pretty close.

i must say that some more work could have been done making available backports for LTS releases, dapper had very very little indeed.

the beauty of Linux is that so many volunteers are working very hard to make something for others, the downside is that if you demand that more is being done you would have to share the burden.

i intend to start working on some backports for Hardy myself and hope others join in since i will be sticking with this one for the next 3 years.

what are you waiting for?

---

### Post by sb73542 on 2008-05-13
> **songshu said:**
> 
what are you waiting for?

I am too dumb, and my internet connection is too slow and unreliable to be fiddling around with source package downloads and deb uploads.

I agree that not all parts of the system should be upgraded on a rolling basis.  For example, the Gnome environment, the kernel, CUPS, libstdc++, can generally go six months.  But there is no reason why I should have to wait six months and THEN on top of that upgrade my entire system just to upgrade my office suite or my media player.

---

### Post by AdamWill on 2008-05-13
In the interests of accuracy, contrary to the OP's statement, Mandriva (and, to my knowledge, other major stable-release based distros like OpenSUSE and Fedora) does not do version upgrades in official update repositories as a matter of course. The rationale for this is longstanding and well-established: new versions of applications often introduce behaviour changes, incompatibilities with previous releases, and sometimes new bugs. As the purpose of a stable release is to be *stable*, we (and Ubuntu, SUSE etc etc etc) do not introduce version upgrades as official updates.

The packages you are finding via a pbone search are most likely in Mandriva Cooker, the development distribution. In much the same way, you could find the latest versions of most applications in Ubuntu's current development version.

Mandriva does have an official and quite widely-used (both by developers and by users) set of /backports repositories, where version upgrades that are commonly requested are provided, without official support. From what I can tell, Ubuntu's backports project is less populated and less widely used, and most backports tend to be done through PPAs.

---

### Post by sb73542 on 2008-05-13
> **AdamWill said:**
> In the interests of accuracy, contrary to the OP's statement, Mandriva (and, to my knowledge, other major stable-release based distros like OpenSUSE and Fedora) does not do version upgrades in official update repositories as a matter of course. The rationale for this is longstanding and well-established: new versions of applications often introduce behaviour changes, incompatibilities with previous releases, and sometimes new bugs. As the purpose of a stable release is to be *stable*, we (and Ubuntu, SUSE etc etc etc) do not introduce version upgrades as official updates.

The packages you are finding via a pbone search are most likely in Mandriva Cooker, the development distribution. In much the same way, you could find the latest versions of most applications in Ubuntu's current development version.

Mandriva does have an official and quite widely-used (both by developers and by users) set of /backports repositories, where version upgrades that are commonly requested are provided, without official support. From what I can tell, Ubuntu's backports project is less populated and less widely used, and most backports tend to be done through PPAs.

Well, if PPAs are the answer, then I wish there was an easy way for normal users to generate current packages from a web interface.

---

