---
title: "xubuntu won't play video from internet"
date: 2012-11-11
forum: General Help
---

### Post by markMDW on 2012-11-11
Hi, I have a 10 year old xubuntu (Athlon XP) computer that had been playing video from Youtube, Yahoo etc just fine, now it won't play any video from the internet.  There are no error messages such as "missing codex" etc, just a blank area where the video should appear. Xubuntu Restricted Extras is installed.    I'm guessing a package got inadvertently deleted a while back.  I even clicked the "upgrade to 12.04.1" prompt, let that process for several hours, and now I have the LTS version, but still no video.  

If nothing else works I will just install the system from scratch, and might try lubuntu.

There must be a setting or a missing package.  Can anyone point me in the right direction.?

Thanks for your time

---

### Post by TenPlus1 on 2012-11-11
go into synaptic package manager and install gecko-mediaplayer, this will grab mplayer from the repo's and let you play all sorts of movies...

---

### Post by cwsnyder on 2012-11-11
The symptoms you relate makes it sound as if your browser has decided to block either flash or javascript.  These are usually blocked by a security add-on which is attempting to block malicious code from executing in your browser.  Did you check your add-ins in the browser, and/or using another browser?

---

### Post by Linux_junkie on 2012-11-11
After upgrading to 12.04.1 did you check that Ubuntu-restricted-extras was still installed?  It shouldn't have done but all the media codecs might have been removed.

Also, the problem might be with your ISP blocking downloads if your on a strict data limit package.

---

### Post by markMDW on 2012-11-11
Hi everyone,  I just double checked.  I do have Xubuntu Restricted Extras still installed and I can't watch video on either Firefox or Chromium (the only browsers I have installed).    Also I just install gecko-mediaplayer and Synaptic says that's now installed, but there was a glitch at the very end reporting that not all changes succeeded, and then something about SAMBA4 which I wouldn't have thought would be associated to a mediaplayer in any way.  I didn't think I had that installed. Thanks for everyone's suggestions!

---

### Post by ajgreeny on 2012-11-11
What video card do you have?

The most recent flash version, 11.2 will not work at all on my ATI 9200SE card, and like your system I get no error messages, just a complete lack of flash videos with that version.  If you have the same card you may also have this problem, just like many others.

The only way I could solve it was to use the earlier flash version 11.1.102-63, available from livinglinux, one of our forum members, at [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796")

If you do this you should make sure you use flashblock or noscript as well to overcome any security risk from the older flash version.

---

### Post by markMDW on 2012-11-11
It is an ATI All-in-Wonder with cable input and TV tuner (not sure of model number).  The Video Card no longer works well.  I have a newish LED monitor that has a blue false tint to all colors.  I was actually thinking about getting a new video card.    Thanks for the advice, I'll give this a try.

---

### Post by raydar on 2012-11-16
I had this same problem in Ubuntu 12.04 on a 32-bit machine with an ATI RV280 [Radeon 9200 PRO] where the flash plugin version 11.2 wouldn't work, but reverting to version 11.1 fixed the problem.

I used the Flash-Aid plugin for Firefox to install the 11.1 version of Flash as described and linked to in post #5 in this similar thread:
[http://ubuntuforums.org/showthread.php?p=12358006#post12358006](http://ubuntuforums.org/showthread.php?p=12358006#post12358006)

---

### Post by NikTh on 2012-11-16
> **ajgreeny said:**
> 
The most recent flash version, 11.2 will not work at all on my ATI 9200SE card, and like your system I get no error messages, just a complete lack of flash videos with that version.  If you have the same card you may also have this problem, just like many others.

The only way I could solve it was to use the earlier flash version 11.1.102-63, available from livinglinux, one of our forum members, at [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796")

If you do this you should make sure you use flashblock or noscript as well to overcome any security risk from the older flash version.

+1 from me. This is (almost) common with old hardware. Newer flash player is incompatible.

---

