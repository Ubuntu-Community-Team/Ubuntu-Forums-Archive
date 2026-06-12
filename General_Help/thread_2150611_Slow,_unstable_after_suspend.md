---
title: "Slow, unstable after suspend"
date: 2013-06-01
forum: General Help
---

### Post by Plui on 2013-06-01
I have an SSD as my main drive, when I got it a few months ago, I followed a few threads info about disabling hibernation, swap, etc. A few days ago, I accidentally clicked on Suspend, so I turned it back on, then shut it down normally, and it took much longer than usual, at least two full 5 dot animations, whereas it usually never makes it past the second dot. Didn't think much of it at the time, maybe it needed to get rid of some suspend clutter, but it's been happening ever since. And I'm getting more frequent red screens than usual, I used to only get them once a month if that.

Any ideas what happened? I can't think of any other cause, unless this is just a massive coincidence and my ssd is going (it's a Crucial M4.)

*Running 12.04 LTS,

---

### Post by Plui on 2013-06-03
I should mention that I'm dual booting, and Windows is as speedy as ever. This is quite bizarre.

---

### Post by Plui on 2013-06-05
Bump~

---

### Post by Annadin on 2013-06-05
i had a similar problem after using sleep, mine was my graphics card for some reason, if your using nvidia i would look into it cause it just seems to cause a lot of problems with Ubuntu

---

### Post by Plui on 2013-06-07
> **Annadin said:**
> i had a similar problem after using sleep, mine was my graphics card for some reason, if your using nvidia i would look into it cause it just seems to cause a lot of problems with Ubuntu

You can say that again, I'm using a GTX 670. I had a hell of a time getting rid of tearing when I first installed.

Did you ever resolve your sleep issue? I wonder if reinstalling would help..

---

### Post by Plui on 2013-06-11
*Bump~*

---

### Post by Plui on 2013-06-16
*Bump~*

---

### Post by kurt18947 on 2013-06-17
> **Plui said:**
> *Bump~*

Have you tried installing the Nvidia drivers?  I've had the suspend/resume problem using the open source driver and also older Nvidia drivers - 304 had your problem.  Installing Nvidia current or 310 (or 319 in Ubuntu 13.10 so far) fixes the suspend/resume problem.  My Nvidia card is an older PCI-e 8400GS.  I don't know if newer drivers when used with newer or Optimus cards fix this problem or not.

---

### Post by Plui on 2013-06-17
> **kurt18947 said:**
> Have you tried installing the Nvidia drivers?  I've had the suspend/resume problem using the open source driver and also older Nvidia drivers - 304 had your problem.  Installing Nvidia current or 310 (or 319 in Ubuntu 13.10 so far) fixes the suspend/resume problem.  My Nvidia card is an older PCI-e 8400GS.  I don't know if newer drivers when used with newer or Optimus cards fix this problem or not.

I've been using the "experimental" 310 drivers, it was something I switched to a while ago in an attempt to fix some tearing issues. It's got a big warning that it's a beta, so I don't know if it introduced more problems than it fixed.

I'm using a fairly new card, a GTX 670, if that helps. Also forgot to mention it in my first post but I'm on 12.04 LTS,

---

### Post by kurt18947 on 2013-06-18
> **Plui said:**
> I've been using the "experimental" 310 drivers, it was something I switched to a while ago in an attempt to fix some tearing issues. It's got a big warning that it's a beta, so I don't know if it introduced more problems than it fixed.

I'm using a fairly new card, a GTX 670, if that helps. Also forgot to mention it in my first post but I'm on 12.04 LTS,

It's been some time but I recall 310 experimental having issues.  The 'mainstream' 310 is working fine on my 12.04.  319 experimental on 13.10 is working quite well, it seems.

---

### Post by Plui on 2013-06-18
> **kurt18947 said:**
> It's been some time but I recall 310 experimental having issues.  The 'mainstream' 310 is working fine on my 12.04.  319 experimental on 13.10 is working quite well, it seems.

Mainstream, as in downloaded directly from nvidia?

---

### Post by kurt18947 on 2013-06-18
> **Plui said:**
> Mainstream, as in downloaded directly from nvidia?
No, Software & Updates -> Additional Drivers

---

### Post by Plui on 2013-06-18
> **kurt18947 said:**
> No, Software & Updates -> Additional Drivers

I was on 'version current' before. Is 'current-updates' what I'm looking for? It doesn't specify anywhere what driver version it is.

EDIT: Turns out it was 304.88. Which seems to work alright. Hope this doesn't give me any issues with Steam.

EDIT2: After rebooting again, it didn't actually fix anything. 

[IMG]http://i.imgur.com/F6sbQKw.png[/IMG]

---

### Post by Plui on 2013-06-21
*Bump~*

---

### Post by kurt18947 on 2013-06-22
I just checked my 12.04 install.  From "additional drivers"
> 
NVIDIA accelerated graphics driver (post-release updates) (current version updates)


---

### Post by Plui on 2013-06-22
> **kurt18947 said:**
> I just checked my 12.04 install.  From "additional drivers"

NVIDIA accelerated graphics driver (post-release updates) (current version updates)

That one doesn't show up as 310, at least on my install. In any case, I've tried them all a few times, changing drivers doesn't seem to help.

---

### Post by Plui on 2013-06-24
*Bump~*

---

### Post by Plui on 2013-06-26
*Bump~*

---

### Post by Pluii on 2013-06-27
Well something happened today, I accidentally hit my keyboard while shutting down, and discovered all of this under-the-hood stuff (see below.)

I found a related bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987933) so this may still have something to do with in nvidia.
But my computer has never had a problem shutting down completely, it's just rather slow. And I get red screens.

I don't know what to do. I don't even know how this happened. Everything was okay. My tearing is back, too. This is the worst.

Edit: I should mention, the real kicker: about 1 in 10 times, it shuts down perfectly like it used to.

```
Broadcast message from root@
    (unknown) at 22:32 ...

The system is going down for halt NOW!
Chekcing for running unattended-upgrades:
    acpid: exiting
speech-dispatcher disabled:edit /etc/default/speech-dispatcher
    -Stopping vnStat daemon vnstatd         [ Ok ]
*ASking all remaining processes to terminated...  **#(It seems to hang for several secs right around here)**
*Killing all remaining processes...            [Fail]
nm-dispatcher.action:Caught signal 15, shutting down...
nm-dispatcher.action: Could not get the system bus. Make sure the emssage bus daemon is running! 
Message: Did not receive a reply. Possible causes include: the remote application did not send a reply, 
the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
modem-manager[852]: <info> Caught signal 15, shutting down...

*Deconfiguring netowkr interfaces...                           [ Ok ]
*Deactivating swap #(I thought I disabled this..)          [ Ok ]
umount: /run/lock: not mounted                                 [ Ok ]
* Will now halt...

[ 62.459321] Powder down.

```

---

### Post by Pluii on 2013-06-28
*Bump~*

---

### Post by Pluii on 2013-06-30
*Bump~*

---

### Post by Pluii on 2013-07-01
*Bump~*

---

### Post by Pluii on 2013-07-02
*Bump~*

---

### Post by Pluii on 2013-07-03
*Bump~*

---

### Post by dak0 on 2013-07-03
Why don't you look for help on other forums, looks like this one is dead. ~bump

---

