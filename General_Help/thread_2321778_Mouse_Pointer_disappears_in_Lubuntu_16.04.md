---
title: "Mouse Pointer disappears in Lubuntu 16.04"
date: 2016-04-24
forum: General Help
---

### Post by Reetam on 2016-04-24
I have just upgraded my Lubuntu to 16.04. However after upgradation I am seeing an issue in which my mouse pointer disappears after my screen is locked. The mouse pointer is visible in the lock screen but after I log in my mouse pointer disappears. Could someone please suggest me a solution for this?

---

### Post by PhilGil on 2016-04-24
It's a known issue in Xubuntu and Lubuntu. A fix is in progress, but right now there's only a work-around: [http://ubuntuforums.org/showthread.php?t=2321311&p=13474801&viewfull=1#post13474801](http://ubuntuforums.org/showthread.php?t=2321311&p=13474801&viewfull=1#post13474801)

---

### Post by Reetam on 2016-04-24
Thanks PhilGil

---

### Post by nictu2 on 2016-05-07
Any news of getting this fixed? Had a few updates since I originally installed 16.05 and a kernel update this morning but still experiencing the disappearing mouse pointer.

nictu.

---

### Post by speartip on 2016-07-20
The solution to this issue at present, seems to be adding this graphics ppa & updating the Xorg drivers:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by nisom-voyager on 2016-07-31
I had the same problem when i removed the intel driver xserver-xorg-video-intel it solved the problem for me.

---

### Post by Andrea_Giavenni on 2016-08-10
Having the same bug on Asus Aspire One, decided to rapidly and happily downgrade back to 14.04. But if a release presents such a severe issue (mouse pointer disappearing!!)and there are'nt any fixes  it should be retired back to development!

---

