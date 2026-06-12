---
title: "Total freeze using Firefox, new install 14.04"
date: 2014-06-06
forum: General Help
---

### Post by Jupiter_Ferris on 2014-06-06
Hi All,

I've replaced an XP installation which was working fine, with Lubuntu 14.04.  I tried Ubuntu first but it ran like a dog.  Lubuntu is fine....

....until I start Firefox (29.0).  Then - total freeze.  Everything is locked, no keyboard, no mouse. Have to power off.

Found a similar report but it was Nvidia/Nouveau drivers - this is Radeon.

I thought I'd try Chromium instead, but that's weird as well, keyboard randomly stops working, only in Chromium. OK in all other apps at the same time, but switch back to Chromium and it doesn't see the key press. That doesn't happen in Firefox.  Firefox just freezes the whole thing.

Don't have to be doing anything special - creating an account here on Ubuntu, it froze halfway through that.  Power off reqd.

Software updater shows no new packages.

PC is an Asus T2, specs attached in the tar.gz along with installed pkgs.  Was planning to give this to my dad to replace his XP machine but until it's stable, it's talking up my desk space.

lsb-release->
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"


uname ->
Linux mrg-desktop 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:02:19 UTC 2014 i686 i686 i686 GNU/Linux

If anyone has any ideas, would be much appreciated.

Cheers

JF.

---

### Post by bapoumba on 2014-06-06
Not sure I can help you with the video stuff, but for chromium input methods, there is an ibus bug : [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)
Workaround : open a terminal and run **ibus exit** (needs to be done again at each new login, there are several ways to make it permanent that I have not tried).

---

### Post by Jupiter_Ferris on 2014-06-07
Thanks for that - it definitely solves the input issue in Chromium.  Unfortunately then causes another after a minute or so - the mouse moves but buttons don't click, and can't tab between open windows although the keyboard works..weird!  If I'm still in the terminal I can reboot though, or, it's power off.

I've just installed Chrome proper, just need something stable!

Ta

---

### Post by bapoumba on 2014-06-07
Well, if the video drivers are playing too, I'm not sure what to suggest. Hopefully someone will come around. Maybe move your thread to Multimedia and Video, if you agree.

---

### Post by dragonfly41 on 2014-06-07
Perhaps try uninstalling flash plugin .. see if the freezes stop .. and then read up on flash freezes in linux Firefox.

---

### Post by Jupiter_Ferris on 2014-06-07
Ok, ta.  Could uninstall flash, don't mind trying, but it'll freeze on websites with no flash.  Worth a pop I guess.  Not sure it's a multimedia and video issue.

I've had Chrome on it all day and it's fine, no problems at all, so maybe that's the way to go.  Just need to handover a working PC, don't want a support headache... Chrome seems to do the job so far...

---

