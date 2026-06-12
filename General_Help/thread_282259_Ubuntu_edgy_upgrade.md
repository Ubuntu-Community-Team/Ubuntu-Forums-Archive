---
title: "Ubuntu edgy upgrade"
date: 2006-10-22
forum: General Help
---

### Post by Tobster on 2006-10-22
I thought the new version of Ubuntu was going to be released today.  Has there been a delay?

Thanks

Toby

---

### Post by taurus on 2006-10-22
Edgy RC1 released last Thursday and Edge Elf will be released this coming Thursday!!!

---

### Post by Tobster on 2006-10-22
What the differents is one like a beta and one the offical version?

I love Ubuntu :)

---

### Post by taurus on 2006-10-22
The final release this coming Thursday should be almost identical to the RC that came out last week except probably some minor bugs fix.  If you can't wait until Thursday, then check out the Edgy Elf RC then.  Play around with it for a few days and if you want, do a fresh install when official Edgy come out on Thursday...  ;)

---

### Post by Tobster on 2006-10-22
Thanks...

Really cant wait but im sure i can hold on a few more days :)  Let the good times role....

---

### Post by myname on 2006-10-24
what will the upgrade be like from Dapper to Edge?  A fresh install?

--kp

---

### Post by taurus on 2006-10-24
> **myname said:**
> what will the upgrade be like from Dapper to Edge?  A fresh install?

--kp
Not sure.  Since I have two machines running Dapper right now, one in the office and one at home, I will upgrade one from Dapper to Edgy using dist-ugrade while I'll do a fresh install on the other one.  Then, will see much different they are...  Need to back some stuff first before I do any upgrading or fresh installing just in case!

---

### Post by myname on 2006-10-24
I run Dapper at home, one Ku and one U system, and since these are my first attempts at Linux in quite many years, I was/am unaware of the upgrade path.  I know with windows, it's best to do a fresh install instead of an upgrade.

Thanx.

--k

---

### Post by cmost on 2006-10-24
First of all, it's "Edgy Eft" folks, not "Edgy Elf" as some of you posted.  Secondly, this isn't Windows and the dist-upgrade option typically works flawlessly.  I know some people who have dist-upgraded all the way from Warty without incident.  This isn't to say that problems won't occur in special situations.  Remember, Edgy Eft will be the first version of Ubuntu to come with AIGLX enabled.  People running Dapper with XGL / Compiz (or Beryl) might want to research the forums ahead of time and make notes or print out any special steps needed to re-implement Compiz with AIGLX, or, keep XGL.  Since nVidia has not yet released the final version of their current 9xxx series driver (the one that supports the GLX_EXT_texture_from_pixmap extension) AIGLX will be dog slow unless one uses the beta driver, or XGL (which takes GLX_EXT_texture_from_pixmap values from MESA.)  My advice would be to DO RESEARCH FIRST!  Browse these forums and utilize Google.  You don't want to be caught with your pants down AFTER you've done the upgrade.  The final version of Ubuntu Edgy Eft should be available Thursday, 10/26.  Gentlemen start your engines!!!!  :)

---

### Post by WirelessMike on 2006-10-25
I have to disagree with the statement that the dist-upgrade option typically works flawlessly, unless that is in reference to kernel upgrades, to which I would agree.

I've been installing and upgrading Ubuntu on a variety of custom hardware, as well as consumer-grade pcs such as Dell since Warty Warthog and I have yet to experience a flawless upgrade from final release to final release.  You'll find the forum archives full of upgrade problems.

That being said--  This latest release, Edgy Eft, appears to be documented by devs as having (finally) a fairly painless upgrade from Dapper.  While this is not historically the case, I know development is always trying to improve this particular issue.

See official notes [here]("https://wiki.ubuntu.com/EdgyReleaseNotes") and [here]("https://help.ubuntu.com/community/EdgyUpgrades").

Please note that the instructions for upgrade using "update-manager" is unique to Gnome or multi-desktop installs that include Gnome.  Note also that skipping releases in the upgrade path is NOT recommended, as suggested [here]("https://help.ubuntu.com/community/UpgradeNotes").

---

