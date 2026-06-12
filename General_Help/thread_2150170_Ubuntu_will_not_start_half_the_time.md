---
title: "Ubuntu will not start half the time?"
date: 2013-05-31
forum: General Help
---

### Post by jacklk on 2013-05-31
Hello,

I installed Xubuntu a couple of days ago, and on that day I decided to install the ATI catalyst driver from the AMD website (due to better performance) for my card. I installed it, but I ran into a common error so decided to uninstall it using it's uninstall script, and now I am using Ubuntu's open source drivers because they are fine for my use. It uninstalled fine, and the open source drivers work, but now, about 50% of the time Ubuntu will not start up. :( What happens is the screen goes black and starts flickering, then goes blue but it never boots up, just stays there flickering. If I try to boot again afterwards then it works. I have tried to reinstall all of the open source graphics drivers, but the same thing happens. It's really strange.

My GPU: ATI Radeon HD 6450

If anyone has any ideas or suggestions please let me know.
Thanks in advance.

---

### Post by dino99 on 2013-05-31
i suppose that a xorg.conf have been previously created, and now disturb the new config. As the kernel directly deal with X, meaning xorg.conf is not required, you'd better to remove it:

sudo rm /etc/X11/xorg.conf*

---

### Post by jacklk on 2013-05-31
Thanks for the suggestion. Everything is working fine without xorg.conf, however removing the file still hasn't resolved the issue. I have restarted serveral times, and the screen still flickers and the computer fails to boot about 50% of the time as usual. 
Any other ideas?

---

### Post by pqwoerituytrueiwoq on 2013-05-31
when you say fails to start do you mean [this](http://i.imgur.com/EG6zyWQ.jpg) (673.08 KB)? if so look [here](http://ubuntuforums.org/showthread.php?t=2141858)

---

### Post by jacklk on 2013-05-31
> **pqwoerituytrueiwoq said:**
> when you say fails to start do you mean [this]("http://i.imgur.com/EG6zyWQ.jpg") (673.08 KB)? if so look [here]("http://ubuntuforums.org/showthread.php?t=2141858")
Nope, that wasn't what I meant; no text shows up on the screen at all. My screen just starts flickering and fails to boot up. I think this may be because the ATI catalyst driver messed up something to do with the open source one, maybe it corrupted a config or something? I tried reinstalling the open source one(s?) with Synaptic but no luck. :(
Anyone?

---

