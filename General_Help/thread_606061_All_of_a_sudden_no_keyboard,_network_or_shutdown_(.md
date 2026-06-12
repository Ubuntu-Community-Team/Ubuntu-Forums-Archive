---
title: "All of a sudden no keyboard, network or shutdown (but fine @ cli /login/liveCD )"
date: 2007-11-07
forum: General Help
---

### Post by Ubuntiac on 2007-11-07
This one's really got me confused.... I was using my wife's new gutsy machine (specs at the bottom) just fine for quite a few hours. All of a sudden a collection of things (which worked just fine up until now) have all gone strange:

**Keyboard:**
Suddenly the keyboard no longer responds in the os (though the touchpad is fine), although it responds just fine for logging in, at the command line or with a live CD. Also for some reason Fn + F3 (wireless on/off) does seem to work. 

**Network:**
Out of the blue network manager doesn't see my wireless. (which was just working fine)

**Shutdown:**
Also shutdown suddenly doesn't. It just goes to a black screen with the cursor (which still responds). Left alone it sits there forever. If I tap the power button briefly, shutdown seems to continue, but reports:

The "Stopping Avahai mDNS/DNS-SD Deamon avahi-daemon" part of shutdown reports [U]"Failed to kill daemon: Timer Expired [Failed]"
[/U]The "Unmounting local filesystems" fails to unmount / and /home as _"device is busy"_

The system then stops again at the "Will now restart"

Shutdown works fine from a live CD.


**Media:**
Strangely browsing to /media doesn't seem to show *any* devices either alothough kern.log shows the kernal recognising my usb key being plugged in and other than the problems just mentioned Gustsy seems to be humming along just fine.

-fsck doesn't report any problems
-kdm.log doesn't report any problems except the occasional AIGLX error (I'm not using AIGLX or any desktop effects)


Works fine from live CD.


Misc:
Adding noapic
nolapic
acpi=noirq
pci=noirq

to GRUB seems to have no discernable effect. :(






I'll be _very_ greatful for any ideas anyone has...



__________________________________
Specs:

Dell Inspiron 1501
Kubuntu Gutsy 32bit final
AMD 64 x2
ATI (xpress 1100?) was using fglrx, using ati atm
Broadcome wireless of some description (uses BCM43xx)

---

### Post by J-Da 01 on 2007-11-14
I am experiencing the exact same problem!  can anyone help?!?

---

### Post by checho4 on 2007-11-26
I'm also having the same problem with mine.  I just installed Gutsy about 3 days ago and EVERYTHING was fine.  In fact, I was using it earlier today without any problem.  Any help is GREATLY appreciated!

I also have a Dell Inspiron 1501, AMD Turion X2, ATI Xpress 200.

---

### Post by checho4 on 2007-11-26
I think I found the problem, though I don't know WHY it's the problem.  I set kNetworkManager to NOT startup automatically, and then I restarted [using the power button].

Upon logging in, everything worked.  Then, I started kNetworkManager to connect to the internet.  That worked.  I rebooted [via KMenu => Restart] and everything went smoothly.  Could it be a bug in kNetworkManager?

---

### Post by saracen on 2007-11-27
I'm having the exact same problem.  No keyboard, no network, and the timer error.  I'm running Xubuntu. 

It makes my system unusable so any help would be much appreciated.  :confused:

---

### Post by checho4 on 2007-11-28
Well, after messing with it some more, I found that it is my restricted driver for my wireless card.  On my Inspiron 1501, I used the bcm43xx-fwcutter, which would cause network-manager to do something funky.  It would lock up my keyboard and would not let me shut down, stating that " / is busy ".  After removing the restricted driver, everything seems to be working alright again.

I guess I'll just have to go back to the ndiswrapper method until this driver is fixed.

---

### Post by Ubuntiac on 2007-12-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174015](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174015) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				After hours of trawling through similar yet different bugs, I've just filed a bug report at:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174015](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174015)

If you're having this problem, please click the link above and add a comment with your system specs, or at least just confirm the bug as some of you have here..

Thanks!

---

