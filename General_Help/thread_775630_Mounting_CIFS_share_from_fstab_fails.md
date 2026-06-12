---
title: "Mounting CIFS share from fstab fails"
date: 2008-04-30
forum: General Help
---

### Post by aliask on 2008-04-30
I've got my lovely new Hardy setup going and it mostly works well except that when I try to mount a samba share using fstab I'm getting the error something to the effect: "Mount error 101 = Network is unreachable".

Startup halts for a couple of minutes while this times out, then proceeds with a normal boot, just without the mount. Running sudo mount -a once the computer is booted and logged in works fine.

It looks like Ubuntu is trying to mount the network share before the network is properly configured, but that's just a guess, because I have no idea of how to alter the order.

---

### Post by wombatworld on 2008-05-15
I'm seeing almost the same thing on my Hardy box (mythbuntu).  I see the "Mount error 101 = Network is unreachable" message, and booting hangs for a while (maybe 30 - 45 seconds), and then finally resumes.  When the boot completes, the cifs shares are mounted and working just fine, so it's not a major problem, but the boot delay is annoying as I power the machine down quite often.  I don't remember having this problem before the upgrade to Hardy.

I agree the most likely explanation is that it's trying to mount the cifs shares before the network initialization is completed.  My machine is quite underpowered (500 MHz P3, 256 MB memory), so I wonder if this is some kind of race condition?  Maybe this is caused by a bug in upstart?

Sorry I don't have any solution for you.  I hope it's some consolation to know you're not alone.

---

### Post by sceo on 2008-05-15
I'm seeing the same thing on my Mythbuntu box... I just performed the upgrade to Hardy, but I'm pretty sure I was having this problem before the upgrade.  I think the upgraded version of Ubuntu is just better about notifying you.

---

### Post by bodhi.zazen on 2008-05-15
I do not have this problem, but I advise you file a bug report :

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by wombatworld on 2008-05-15
> I do not have this problem, but I advise you file a bug report

Good idea.  Actually, there already is a bug report for it:  bug #208770.  But no solution yet.  See:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/208770](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/208770)

---

