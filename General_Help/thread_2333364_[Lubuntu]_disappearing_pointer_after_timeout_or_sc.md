---
title: "[Lubuntu] disappearing pointer after timeout or screensaver"
date: 2016-08-09
forum: General Help
---

### Post by linbu on 2016-08-09
RE:     [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Lubuntu](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Lubuntu)

     very near bottom of page;

Lubuntu-specific Bugs

     Lubuntu Alternate Installer

          "Cursor invisible after timeout and screen-saving (1572640) and possibly (1568604)."


I have encountered this exact problem after accepting the Software Updater offer to upgrade from 14.04 to 16.04 on a Dell d630 laptop. One of my points being that I did not download the .iso image or use either a DVD or USB for the installation.

Another point, rather question is, when will this issue be fixed? I have installed Lubuntu 14.04 on the computers of several of my friends and had every intent of upgrading each of them to Lubuntu 16.04. Now after doing this upgrade myself and finding this "layperson trap" (they would have no idea what to do other than power off the computer)[and no fix even after Lubuntu 16.04.1], I have delayed the upgrade installation for my client friends. There is now less than one year until support is dropped for Lubuntu 14.04.

This should be tagged as a PRIORITY bug, how can you expect to win over new users with a problem such as this?!!!!! And other posts suggest it is an old (2+ years) and known issue. When can it be expected to be fixed please?

Hank

---

### Post by mörgæs on 2016-08-10
Yes, it's sad that Lubuntu had so many problems with Intel graphics in this release. 

I don't recommend upgrades in general but if people want 16.04.1 and they have Nvidia or AMD graphics the process should be easy.

For Intel users I think the best one can do is to stay with 14.04. There is a lot of attention on the bug, and I expect 16.04.2 to be clean when it is released in february.

---

### Post by linbu on 2016-08-10
@morgaes,

Thank you for your kind reply. Please understand my reply is not meant to be disparaging to any individual or person. It is very hot here and I could use the temps you are experiencing presently :-)

@fellow Lubuntu user friends,

Let me be clear, I am devoted to Linux, Ubuntu, and Very Especially LUBUNTU, however Regression is what it is, and to move "up" from an older distro and have "THE MOST BASIC" features broken is absolutely "Unacceptable". Such is the case with this disappearing pointer with Lubuntu 16.04+.

It will be insane and absurd for Lubuntu users to wait until February 2017 for a fix. I don't know how to scream online, but if I did I'd be doing it now!

This is like saying "Thanks for purchasing the new Mercedes XL-2300 'The Safest Vehicle on the Road'. Please be patient with us as we attempt to fix the problem of the left rear tire going flat after 40 kilometers, we expect to have this fixed next year. In the between time please enjoy your ride in the Mercedes XL-2300 three wheeler."

Please understand my sarcasm here. With this problem continuing with Lubuntu or any other Ubuntu flavor distro, the integrity of "Ubuntu" is severly diminished. Ask yourself, would you install this Ubuntu particular OS? Let me re-phrase that. Would you offer to install, or upgrade to this particular Lubuntu on the computer of a dear friend, who has had too many problems with Windows? Are you willing and ready to lose a friend (or Ubuntu/Linux convert) over this "disappearing pointer" problem?

Why is a "disappearing pointer" sitll a problem with Lubuntu 16.04.1 ?!!!!!!

An extremely frustrated Lubuntu/Ubuntu user,

Hank

---

### Post by PaulW2U on 2016-08-10
> **linbu said:**
> Why is a "disappearing pointer" sitll a problem with Lubuntu 16.04.1 ?!!!!!!

An extremely frustrated Lubuntu/Ubuntu user,
The Xubuntu team, a flavour that is also affected by this bug, are very aware of this problem. It has not been forgotten and as far as I can tell from various IRC conversations, is something that is being worked on although you might not see a fix in 16.04 straight away.

---

### Post by linbu on 2016-08-10
@PaulW2U,

Thanks for the kind reply.

You obviously appreciate my concern for the "Ubuntu Integrity" issue raised in the past post.

I'm a layman (older semi-layman :-), I like to convert "OLD" Windows users to Ubuntu/Lubuntu/Linux. Because their computers are in their attic, basement, or a closet, not being used because Windows is broken. Some of these people are fairly old, retired, and perhaps have only a use for "email" or "a browser". Their computers work fine with Linux, I have been able to bring smiles to many many faces by installing Lubuntu on their "broken" systems.

I love Lubuntu for these older computers. It just works!................ Until this pointer problem.

This problem should be HIGH PRIORITY and addressed IMMEDIATLY! (So, I found how to scream online, but not at you !!!!!)

I wish I were younger and able to keep up with all these developments as they take place. However, I remain young enough to thank you for your kind reply.

Hank
PS - I have also enjoyed Xfce (Xubuntu) as my default desktop in my aging career :-)

---

### Post by PaulW2U on 2016-08-12
> **linbu said:**
> This problem should be HIGH PRIORITY and addressed IMMEDIATLY!
Hang on for just a while longer. :)

[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1568604/comments/193](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1568604/comments/193) and
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1568604/comments/194](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1568604/comments/194)

suggest that a fix is imminent. :)

---

### Post by linbu on 2016-08-13
@PaulW2U,

Thanks new friend,

I will indeed "hang on", your efforts on this bug have been outstanding.

Thank you !!!!!

Hank

---

### Post by kurt18947 on 2016-08-13
If this is a bug that I've dealt with in Ubuntu-Gnome, there is a work around. <ctrl><alt>F1 then <ctrl><alt>F7 and the cursor will magically reappear. This needs to be fixed, especially for users like linbu assists and kudos to you, linbu for helping out. This is a neglected group of potential *buntu users.

---

### Post by linbu on 2016-08-13
@kurt18947,

Thanks, I'm glad also to see you watching the progress with this bug.

I was surprised to see in Bug #1568604 "Comment #193" mentioned above, that the Bug is labeled:

urgency=medium

What's with that? I don't know the levels of urgency but certainly this should be the highest. I'm using Linux for almost 20 years now. Had I come across this Bug while testing various CD Distros 10 years ago,.....I'd have dropped it like a hot potato :-)

Thanks to all who are responding and endeavoring to have this fixed !

Hank

---

### Post by PaulW2U on 2016-08-16
Hi again linbu, if you take a look at the most recent comments on bug report [#1568604]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1568604") you'll see that this bug has now been fixed although it may be few days, perhaps more, before you see an update to the **xserver-xorg-video-intel** package as the fix is still being tested and evaluated.

---

### Post by linbu on 2016-08-16
@PaulW2U,

Thanks again, and for keeping me (and others) posted about the progress with this fix. I'll be looking for the update.

Hank

---

### Post by linbu on 2016-09-07
I marked this thread as [SOLVED] on this date, as I have noticed the problem is now corrected. Sorry I can't recall the exact "update" which effected this positive result. Should the problem persist for others, perhaps a moderator can "un-solve" the thread.

Thanks to all who assisted with this bug!

Hank

---

