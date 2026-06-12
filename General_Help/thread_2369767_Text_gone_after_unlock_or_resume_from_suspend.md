---
title: "Text gone after unlock or resume from suspend"
date: 2017-08-26
forum: General Help
---

### Post by &amp;KyT$0P# on 2017-08-26
Ever since I upgraded my MacBook Pro 9,1 to Xubuntu 16.04, I've noticed that sometimes when I resume from suspend or unlock the host's screen, the Openbox window titles text would go missing.  Recently I noticed this problem happens only whenever I run VirtualBox VM(s) for a long time.

I tried upgrading from VirtualBox 5.1.18 to VirtualBox 5.1.26 to see if it would resolve the issue.  But it seems to have made the problem worse.  Now, in addition, the text in xfdesktop is gone (leaving only the text shadow), notifications have only little spots of text, and the menus from the XFCE panels have no text at all.

Only rebooting restores back to normal.

Why does this problem happen?  How to stop it without giving up VirtualBox?


(In case it's relevant, I use the Intel graphics.)


Edit: I am quite sure now that this is not VirtualBox related.  I then suspected it was related to use of swap, but I just now saw it with my system using zero swap, so that certainly can't be the only cause.

---

### Post by &amp;KyT$0P# on 2017-09-07
bump

Apparently it's not just the Openbox window titles that disappear.  Everything Openbox, including the Openbox menus and the position/size indicator, is devoid of visible text.

Also, as I move or resize a window, the position/size indicator changes size, as if the text is still there but invisible.  If I move a window off-screen, the minus sign(s) seems to show up (or at least did this time) but all the other text in Openbox remains invisible.

:confused:

---

### Post by &amp;KyT$0P# on 2017-09-27
bump

---

### Post by &amp;KyT$0P# on 2017-09-29
I was forced to upgrade to VirtualBox 5.1.28, and the issue is still there.

I wonder if this is actually not related to VirtualBox.  I suspect it might be related to the use of swap.  I notice that no swap is used when I don't notice this problem.  And just now, just before the problem recurred, I checked and the system was using 3.7 MB of swap.
(In case it's relevant, I use a swapfile.)

Would switching to the HWE kernel or entire HWE stack solve this?

---

### Post by &amp;KyT$0P# on 2017-10-06
Ok, it's not related to either use of swap or VirtualBox.  Just saw the problem again, and I have not even started VirtualBox or any VMs, nor is any swap in use.

Still wondering how likely it is that the HWE kernel or entire HWE stack would solve this?

---

### Post by &amp;KyT$0P# on 2017-10-13
bump

---

### Post by &amp;KyT$0P# on 2017-10-20
bump

---

### Post by &amp;KyT$0P# on 2017-10-30
No one has any idea whether the HWE stack might have any impact on this issue or not?

I realise no one can be certain, unless you have the exact same hardware and exact same problem.  But surely it's known whether some part of the HWE stack would, say, get me a newer driver for my Intel graphics than the default 16.04[.0] stack?

If it would, I would consider it worth a shot.

---

### Post by &amp;KyT$0P# on 2017-11-03
bump

---

### Post by &amp;KyT$0P# on 2017-11-11
bump

---

### Post by &amp;KyT$0P# on 2017-11-19
bump

---

### Post by &amp;KyT$0P# on 2017-12-03
Now this is interesting.  For reasons unrelated to this, I increased the amount of RAM in my computer.  Since then, I have not seen this issue.  Problem solved? :?

(Hope I'm not talking too soon.)

---

### Post by &amp;KyT$0P# on 2017-12-19
> **halogen2 said:**
> (Hope I'm not talking too soon.)
Oops, I did talk too soon.  Today I saw this problem again.

I did put my computer through a fair number of heavy loads, including some inside VirtualBox VMs.  I don't think my RAM was ever close to being all used up, but I could be wrong about that.

---

### Post by &amp;KyT$0P# on 2018-01-27
> **halogen2 said:**
> surely it's known whether some part of the HWE stack would, say, get me a newer driver for my Intel graphics than the default 16.04[.0] stack?
I think the answer is yes -
[xserver-xorg-video-intel version: 2:2.99.917+git20160325-1ubuntu1.2]("https://packages.ubuntu.com/xenial-updates/xserver-xorg-video-intel")
[xserver-xorg-video-intel-hwe-16.04 version: 2:2.99.917+git20170309-0ubuntu1~16.04.1]("https://packages.ubuntu.com/xenial-updates/any/xserver-xorg-video-intel-hwe-16.04")

So, per [this link]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop"), I've switched to the HWE stack with this command -
```
sudo apt-get install linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 xserver-xephyr-hwe-16.04
```
... and will see if it helps.  Fingers crossed.

---

### Post by speartip on 2018-01-28
This issue may be related to a problem that I've been having. I haven't seen it in Xubuntu, but it drove me mad using Linux Mint Cinnamon. It only seems to affect computers with Intel integrated graphics drivers.
Is your issue the same as these?
[https://askubuntu.com/questions/584922/how-do-i-fix-fonts-not-rendering-and-missing-letters](https://askubuntu.com/questions/584922/how-do-i-fix-fonts-not-rendering-and-missing-letters)
[https://superuser.com/questions/1107791/cinnamon-text-icons-disappearing](https://superuser.com/questions/1107791/cinnamon-text-icons-disappearing)
if so I resolved the issue by applying the following:
[https://forums.linuxmint.com/viewtopic.php?t=261905](https://forums.linuxmint.com/viewtopic.php?t=261905)

---

### Post by &amp;KyT$0P# on 2018-01-28
I can't tell if that's quite the same issue or not - in my case, sometimes little tiny pieces of the missing characters do appear, while they're all totally blank in those screenshots.  If I see this problem again I will try your suggested solution.  Thanks speartip!

---

### Post by &amp;KyT$0P# on 2018-06-29
The switch to HWE stack did seem to fix this issue.  And I have not seen it since upgrading to 18.04.

---

