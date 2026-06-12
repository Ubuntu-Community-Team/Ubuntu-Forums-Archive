---
title: "Launched an older version of Firefox"
date: 2019-05-30
forum: General Help
---

### Post by Impavidus on 2019-05-30
I just upgraded Xubuntu 18.10 to 19.04. It all works, with a few minor glitches (as usual), but one weird error. When I try to launch Firefox, it complains that I've launched an older version of Firefox and refuses to load my profile. I can start Firefox with a new profile, but that way I loose all my bookmarks etc. Of course, I'm not really launching an old version. The version of Firefox I got on 19.04 is 67.0, which is the same as I used earlier today on Xubuntu 18.10. Any way to make Firefox load my old profile or put the data from by old profile into the new? The old profile is properly backed up.

---

### Post by Autodave on 2019-05-30
Can you back up your favorites from another install and reinstall them on the new version?

---

### Post by dragonfly41 on 2019-05-30
I'm still on Ubuntu 16.04 but here is a thought.
As a work around on 19.04 perhaps try installing Pale Moon browser (if available in 19.04) and import your old FF profiles?

[https://forum.palemoon.org/viewtopic.php?t=17349](https://forum.palemoon.org/viewtopic.php?t=17349)

---

### Post by PaulW2U on 2019-05-30
> **Impavidus said:**
> It all works, with a few minor glitches (as usual), but one weird error. 
That's a known problem, bug [1830096]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1830096") which is currently being worked on. It seems to be caused by not building Firefox for each of the Ubuntu releases sequentially, i.e. bionic, cosmic and then disco.

---

### Post by Impavidus on 2019-05-31
> **Autodave said:**
> Can you back up your favorites from another install and reinstall them on the new version?I can try to back up my favourites via a spare 18.04 install.

> **PaulW2U said:**
> That's a known problem, bug [1830096]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1830096") which is currently being worked on. It seems to be caused by not building Firefox for each of the Ubuntu releases sequentially, i.e. bionic, cosmic and then disco.Good to know. So it should be fixed as soon as I upgrade Firefox from the repos.

Marking this as solved.

---

### Post by Impavidus on 2019-06-03
I first decided to wait until the fix was in the repos, but that took too long. I just edited the version number in the compatibility.ini of my old profile to be identical to the one in the new profile. It works.

---

### Post by PaulW2U on 2019-06-08
Impavidus, since your last post you should now have received an update to Firefox 67.0.1. Was the update problem free for you?

I ask as although the problem that you reported didn't affect me I'm now seeing bug [1832015]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1832015") which presents a similar error message to the one that you saw but users who haven't just upgraded their Ubuntu version might now be seeing.

---

### Post by Impavidus on 2019-06-08
I got the upgrade and everything works fine. No issues. Of course, that doesn't guarantee the original issue is gone for people who now update to 19.04.

This new bug definately sounds related.

---

### Post by PaulW2U on 2019-06-08
Thanks for your reply Impavidus.

I've abandoned my 18.04 installation with Firefox not starting for now and rebooted into Ubuntu's development version in order to reply here. I've marked bug [1832015]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1832015") as a regression so hopefully the issue will be investigated after the weekend is over.

---

