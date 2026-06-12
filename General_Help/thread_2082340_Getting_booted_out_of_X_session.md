---
title: "Getting booted out of X session?"
date: 2012-11-09
forum: General Help
---

### Post by irishetalon007 on 2012-11-09
Hello!

Ubuntu 12.04 here.

Only recently did the following start:

During certain operations, and for no obvious reason at all, I get booted straight to my login screen! Something with Xorg or my nvidia drivers is screwing up I think, because it doesn't happen when I disable my proprietary Nvidia drivers (this is not an allowable long-term solution).

The event is repeatable. For instance, it will happen indefinitely if I try to open a skype IM window (but skype call windows work fine!)

if anyboyd has any idea how to track down the problem, please let me know!

I've attached an output of lshw

---

### Post by danielbauwens on 2012-11-09
I had the same problem, and then removed unnecessary packages via terminal. After that it booted fine.

```
sudo apt-get remove
``` 

It shows the stuff it wants to remove so you can check it.

Daniel

---

### Post by irishetalon007 on 2012-11-10
Do you mean "autoremove"?

---

### Post by 2F4U on 2012-11-10
As it seems to be a repeatable problem, you can look into the system log file (/var/log/syslog) directly after you are booted back into the desktop. Hopefully it gives some hint on what happened.

---

### Post by irishetalon007 on 2012-11-11
Here is the output of syslog that coincides with the exact moment I get booted to login screen:

Nov 11 00:03:32 unknown gnome-session[2622]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Nov 11 00:03:32 unknown acpid: client 1363[0:0] has disconnected
Nov 11 00:03:32 unknown acpid: client 1363[0:0] has disconnected
Nov 11 00:03:32 unknown acpid: client connected from 4272[0:0]
Nov 11 00:03:32 unknown acpid: 1 client rule loaded
Nov 11 00:03:32 unknown kernel: [  824.833093] NVRM: GPU at 0000:01:00: GPU-477f58a7-a62a-7514-8660-497337992205

---

### Post by 2F4U on 2012-11-11
I found some other bug reports for different Linux distributions which sound very similar to your problem. 

[https://bugs.launchpad.net/linuxmint/+bug/1022338](https://bugs.launchpad.net/linuxmint/+bug/1022338)
[http://forum.linuxmint.com/viewtopic.php?f=59&t=106911&start=0](http://forum.linuxmint.com/viewtopic.php?f=59&t=106911&start=0)

Both problems seem to point to the nVidia driver as the source of the problem.

---

### Post by irishetalon007 on 2012-11-11
Wow. Where can I learn those forum-searching skills? :P

Although neither of those was the direct answer, they led me to it.

I'm not entirely sure what fixed it, but here's the steps I took.

sudo apt-cache showpkg xserver-common
sudo apt-get install xserver-common=`version below current version`
sudo apt-get reboot
boot into recovery console, root terminal
mount -o remount,rw /   %this command makes drive writable
apt-get update
apt-get build-dep ubuntu-desktop
reboot
reinstall nvidia drivers
reboot
done! (For now....I'll give it a few days before marking the thread as solved to ensure it actually worked)

---

### Post by irishetalon007 on 2012-11-11
> **irishetalon007 said:**
> Wow. Where can I learn those forum-searching skills? :P

Although neither of those was the direct answer, they led me to it.

I'm not entirely sure what fixed it, but here's the steps I took.

sudo apt-cache showpkg xserver-common
sudo apt-get install xserver-common=`version below current version`
sudo apt-get reboot
boot into recovery console, root terminal
mount -o remount,rw /   %this command makes drive writable
apt-get update
apt-get build-dep ubuntu-desktop
reboot
reinstall nvidia drivers
reboot
done! (For now....I'll give it a few days before marking the thread as solved to ensure it actually worked)

JUST KIDDING! still busted

---

### Post by irishetalon007 on 2012-11-14
I'm closing the thread, as it's related to an open bug in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/999191](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/999191)

---

