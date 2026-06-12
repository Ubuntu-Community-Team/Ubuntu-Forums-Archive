---
title: "Problems with 14.04.5"
date: 2017-03-16
forum: General Help
---

### Post by atrab101 on 2017-03-16
> **Bucky Ball said:**
> Erm, don't you mean to *your* system? Sure, people have issues with any OS, but many of us have been using 16.04 problem free since its release. I'm running it on three machines (until recently four) and not a glitch. ;)

Updated/upgraded two of them last night, rebooted, not an issue, kernel 4.4.0-65-generic, which is the latest. 



I have posted above in this thread about my trouble free experience for more than a year since I installed 14.04.  I am now 14.04.5 and the current HWE path which allows security updates to continue until April 2019.  I did have a a scare yesterday during system offered security updates.  This at the 4.4.0-66 kernel.  The update hung up at the last update which was for Adobe plug-in  (probably not relevant, although Adobe has a less than exemplary reputation).  I waited about 30 minutes and the update process just would not complete.  Perhaps I should not have done it, but I just closed the software updates box.  Then I got a message box saying that the update could not complete and perhaps it was due to a power failure, package conflicts due to previous packages automatically installed that were no longer needed and a few other reasons ( I could have noted all possible reasons listed but just didn't).  It also said that perhaps a "partial upgrade" would resolve the issues with a button to click for this at the bottom of the big message box.  I did not like the sound of that, as I have been doing security updates but no upgrades because I want 14.04 stability at this time.  A "continue" button was also offered, and I selected that.

Now I received another message saying that I would not be able to install or remove packages due I think to the package directory structure being corrupted (or some similar words).  I further said that this might resolved with "sudo apt-get install -f."  I tried that but couldn't get sudo access with my password, as it said the package directory was in use by another application.  A reboot resolved that.  Then I ran the "Sudo apt-get install -f" command.  I got a fairly long list of various things including a few earlier kernel versions that would be removed, saying that the total of removals would be 781 MB and asking if I was sure I wanted to do it.  I crossed my fingers typed "Y" and hit enter.  I did have a 2 day old disk image so really no risk :).  It completed this command, I rebooted, and all was well.  My system worked fine and my Synaptic package manager showed no broken packages.  Today I updated with various security updates and 4.4.0-67 kernel, and everything still appears to be fine.

Sorry to be so boring with all the detail above, but I wanted anyone that may comment to have a good picture of my experience.  I have never before had any issues with the update process. It has never before taken more that a few minutes to complete.  I have read of other people having bad experiences if their upgrade process does not complete due to power failures or hangs, resulting in things broken.  

I think that the upgrade process automatically giving me things that are later not needed and cause problems, then recommending a partial upgrade, or if that choice is not made requiring their removal, is perhaps a loosely defined stability issue.  It seems a risky situation for users without much experience.

It may be that I experienced an update process that did not complete due to a faulty Adobe package and then incorrectly closed the update box after the 30 minute wait.  I am very glad that I stumbled through as a Linux novice and everything is fine.  I did some reading after the fact that indicated "partial upgrades" are risky; I almost selected that system recommended path (as I think many would) but think I might have had to restore my image with that decision.  I also read about another user on these forums that alleged his laptop was bricked with the "sudo apt-get install -f" command.

I am not complaining about the stability of Ubuntu.  It has been by far the best OS ever for me.  I love it, and it has had great stability for me.  The only "possible" exception is this one experience.  But I stumbled through it!:D

A few questions:
1) Should I have done anything other than close the update box after a 30 minute wait?  Maybe if I let it run all night it might have completed?
2) Was it best to avoid the recommended partial upgrade as I did.  Or would that have resulted in the same changes to my system as the path I took.
3) Is there something I should have read as a novice in Ubuntu about the upgrade process that would have prepared me for what I should do if an upgrade hangs during the process and will not complete?

Any response on these questions, as well as insight on why all of a sudden 781MB of packages had to be removed, would be greatly appreciated.

---

### Post by Bucky Ball on 2017-03-16
> **atrab101 said:**
> 

A few questions:
1) Should I have done anything other than close the update box after a 30 minute wait?  Maybe if I let it run all night it might have completed?
2) Was it best to avoid the recommended partial upgrade as I did.  Or would that have resulted in the same changes to my system as the path I took.
3) Is there something I should have read as a novice in Ubuntu about the upgrade process that would have prepared me for what I should do if an upgrade hangs during the process and will not complete?

Any response on these questions, as well as insight on why all of a sudden 781MB of packages had to be removed, would be greatly appreciated.

As with a previous poster on this thread, you're asking for support on a non-support thread in a non-support area of the forum on someone else's thread. If you need support, this is not the place to ask for it. Your own thread is. You will greatly improve your chances of getting it. :)

---

### Post by QIII on 2017-03-16
Moved to its own support post from [https://ubuntuforums.org/showthread.php?t=2354382](https://ubuntuforums.org/showthread.php?t=2354382)

---

### Post by atrab101 on 2017-03-17
> **Bucky Ball said:**
> As with a previous poster on this thread, you're asking for support on a non-support thread in a non-support area of the forum on someone else's thread. If you need support, this is not the place to ask for it. Your own thread is. You will greatly improve your chances of getting it. :)

You are right, of course.  Even though my system is working fine at this time, I feel that I don't understand the update and upgrade processes well enough.  I am looking for general help to avoid possible pitfalls in the future.  Thanks for the guidance!  :oops:

---

