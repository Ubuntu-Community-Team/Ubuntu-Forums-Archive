---
title: "More than two minutes from boot to log in"
date: 2018-07-03
forum: General Help
---

### Post by tea for one on 2018-07-03
Yesterday July 02, there was a kernel upgrade to 4.15.0-24 and my log in duration is now more than two minutes, previously it was around 20-25 seconds.

I suspect that it is something to do with *plymouth-quit-wait.service*
```

systemd-analyze blame
``` produces the following:-

```
1min 49.283s plymouth-quit-wait.service
         13.332s snapd.seeded.service
         13.077s snapd.service
          5.682s NetworkManager-wait-online.service
          2.350s dev-sda1.device
          2.120s apt-daily-upgrade.service
          1.735s dev-loop10.device
          1.730s dev-loop11.device
          1.717s dev-loop13.device
          1.701s dev-loop12.device
          1.671s dev-loop14.device
          1.604s upower.service
          1.555s dev-loop2.device
          1.554s dev-loop3.device
          1.546s dev-loop8.device
          1.542s dev-loop5.device
          1.537s dev-loop6.device
          1.536s dev-loop1.device
          1.533s dev-loop0.device
          1.531s dev-loop7.device
          1.530s dev-loop4.device
          1.513s dev-loop9.device
          1.204s apt-daily.service

```

It appears that there are a few similar threads today but no immediate solution?

Any ideas?

Thank you

---

### Post by mc4man on 2018-07-03
try this - [https://ubuntuforums.org/showthread.php?t=2395451&p=13780509&viewfull=1#post13780509](https://ubuntuforums.org/showthread.php?t=2395451&p=13780509&viewfull=1#post13780509)
or just use the -23 kernel

---

### Post by tea for one on 2018-07-03
> **mc4man said:**
> try this - [https://ubuntuforums.org/showthread.php?t=2395451&p=13780509&viewfull=1#post13780509](https://ubuntuforums.org/showthread.php?t=2395451&p=13780509&viewfull=1#post13780509)
or just use the -23 kernel

Thank you for your reply.

Approx 4 hours ago, I tried the kernel 4.15.0-23-generic and the boot time was over two minutes.

I just tried it again and the crucial delay was reduced to **7.253s plymouth-quit-wait.service** - remarkable.

I'm going to remove the later kernel 4.15.0-24 and use the 23 kernel for the rest of the day and see if it is a firm solution.

I'll report back tomorrow with my findings.

Kind regards

---

### Post by tea for one on 2018-07-04
I removed the later kernel yesterday and am currently using 4.15.0-23-generic.

I have rebooted more than a dozen times and my boot to log in is now back to normal (between 19 and 22 seconds)

Therefore, I will mark this thread as solved.

Thank you for your help

---

### Post by bodhin2 on 2018-07-04
is there a very easy way to remove it?  i know zip for CLI.  I am glad you got it working.  someone gave me a very long technical process but not going there with my lack of knowledge.

---

### Post by tea for one on 2018-07-04
> **bodhin2 said:**
> is there a very easy way to remove it?  i know zip for CLI.  I am glad you got it working.  someone gave me a very long technical process but not going there with my lack of knowledge.

Yes, synaptic graphical package manager is my weapon of choice.

However, in your own thread [https://ubuntuforums.org/showthread.php?t=2395567](https://ubuntuforums.org/showthread.php?t=2395567) you expressed a reluctance to pursue this?

Do you have synaptic installed?

Can you boot into a previous kernel 4.15.0-23-generic?

Please back up your personal data and I'll slowly walk you through the process.

---

### Post by mc4man on 2018-07-04
If you remove the **latest** kernel packages you'll also remove the metapackages associated with them. This will make upgrading to future kernels a bit more difficult. Ubuntu updates the metapackages which depend on the latest kernel packages. Many times the next kernel package(s) are not updates to previous kernel package(s) so you'll never get notified.
Ex. 
screen 1 - current _updates_ available here, all  kernel ones are the metapackages
screen 2 - looking at linux-image packages note that the current (linux-image-4.15.0-24-generic) does not show any upgrades/updates available. Below it is the newest - (linux-image-4.15.0-25-generic).  It is not an update to previous (current) kernel image

So removing the metapackages could prove problematic for many users in regards to getting proper kernel packages upgraded..

---

### Post by tea for one on 2018-07-04
mc4man - Thank you for the information.

I am having a bit of difficulty understanding the upgrade process of the kernel packages.

As I have removed the packages 4.15.0-24, the implication is that I may _not_ receive notification of future kernel packages?

Therefore should I do the following:-

Re-install the deleted 4.15.0-24 packages (in order to receive upgrade notifications)?
Boot into kernel 4.15.0-23 until new notifications are received?

---

### Post by apeitheo2 on 2018-07-04
As I mentioned in the other thread ([https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)):

```
sudo apt install haveged
sudo systemctl enable haveged
```

This issue only seems to affect kernel 4.15.0-24. getrandom() is called when starting Xorg and for some reason in 4.15.0-24, it hangs for a bit until the entropy is high enough to generate a random number to use as a magic cookie for xauth. Xorg, LightDM, and GDM won't start until xauth is given a random number to use. Any kind of mouse/keyboard input probably raises entropy, which explains why pressing keys or moving the mouse fixes the problem. Haveged generates enough entropy at boot, eliminating the problem.


It's been reported as a bug, so hopefully haveged won't be necessary in future kernels once the bug is fixed.


The previous 4.15.0-23 kernel doesn't have this problem, so booting into that instead would also work.

---

### Post by mc4man on 2018-07-05
> **tea for one said:**
> mc4man - Thank you for the information.

I am having a bit of difficulty understanding the upgrade process of the kernel packages.

As I have removed the packages 4.15.0-24, the implication is that I may _not_ receive notification of future kernel packages?

Therefore should I do the following:-

Re-install the deleted 4.15.0-24 packages (in order to receive upgrade notifications)?
Boot into kernel 4.15.0-23 until new notifications are received?

Just make sure these 3 are installed, they may or may not have been removed.
```
linux-generic linux-headers-generic linux-image-generic
```
(- myself see no issue with 4.15.0-24.26, boots up quickly like previous versions, about 8 sec's from power on to desktop

---

### Post by tea for one on 2018-07-05
> **mc4man said:**
> Just make sure these 3 are installed, they may or may not have been removed.
```
linux-generic linux-headers-generic linux-image-generic
```
(- myself see no issue with 4.15.0-24.26, boots up quickly like previous versions, about 8 sec's from power on to desktop

mc4man - Thank you for the clarification.

The three packages that you mention were indeed removed and I have now re-installed them. 

As a point of interest, there is another interesting forum discussion about the slow boot with kernel 4.15.0-24 with an alternative solution.

[https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13780980#post13780980](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13780980#post13780980)

Thank you for your help

Best wishes

---

### Post by apeitheo2 on 2018-07-05
According to [https://bugs.launchpad.net/ubuntu/+bug/1779827](https://bugs.launchpad.net/ubuntu/+bug/1779827) a fix has been committed, so now we're just waiting for it to be released.

---

### Post by mc4man on 2018-07-05
> **tea for one said:**
> mc4man - Thank you for the clarification.

The three packages that you mention were indeed removed and I have now re-installed them. 

As a point of interest, there is another interesting forum discussion about the slow boot with kernel 4.15.0-24 with an alternative solution.

[https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13780980#post13780980](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13780980#post13780980)

Thank you for your help

Best wishes
The supposed fixed kernels (4.15.0.26.28) are in the proposed repo, you could give it a try or wait a day or two for them to go to main.

---

### Post by tea for one on 2018-07-06
> **apeitheo2 said:**
> According to [https://bugs.launchpad.net/ubuntu/+bug/1779827](https://bugs.launchpad.net/ubuntu/+bug/1779827) a fix has been committed, so now we're just waiting for it to be released.

Thank you

I had a look at launchpad but failed to find this report

Best wishes

---

### Post by tea for one on 2018-07-06
> **mc4man said:**
> The supposed fixed kernels (4.15.0.26.28) are in the proposed repo, you could give it a try or wait a day or two for them to go to main.

Thank you for the update - I'll wait until the new kernels appear in the main repo.

Another piece of info - I use Xubuntu Core on a HP netbook and the troublesome kernel 4.15.0-24 boots normally. 

Ubuntu uses gdm3 to load the display and Xubuntu Core uses lightdm - I wonder if this is pertinent?

Kind regards

---

