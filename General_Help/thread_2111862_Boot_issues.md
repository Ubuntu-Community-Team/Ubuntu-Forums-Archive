---
title: "Boot issues"
date: 2013-02-03
forum: General Help
---

### Post by cathy87 on 2013-02-03
Hi everyone,

I've installed Ubuntu alongside OS X yesterday because I fancied it. I didn't expect to get a bunch of trouble doing so, but the whole process seems to have messed up a lot.

I can't boot OS X anymore due to GRUB not recognising an apple wireless keyboard (which is shocking enough already.) I was able to use Ubuntu just fine, but I need OS X for my professional work (freelancer here!)

After some fiddling around with other things like installing Blender and Steam with Team Fortress 2, but after realising neither Blender nor TF2 worked I updated my Nvidia drivers. That required a reboot, and now I can't even get into Ubuntu because it asks me for a login and a password when it boots, in a terminal environment before I get to the OS.

I'm massively frustrated here. Can anyone help me out? What is my login, if I didn't set up one? Choosing nothing as a login doesn't work. 

Cheers,
Cathy

---

### Post by cathy87 on 2013-02-03
Forget it everyone, I found out how to log in. And I'm stuck in a Terminal, can't even use Ubuntu anymore. I'm just going to buy a wired keyboard and try to get rid of everything by booting into OS X. Had so many hopes for this, and now I'm just filled with regret for even trying it. So frustrating.

---

### Post by Schugy on 2013-02-03
GRUB is no OS but a boot loader. Wireless keyboard support should be provided by UEFI/BIOS. If X doesn't start it's an issue of nvidia's binary blob. Maybe nvidia-config helps. No idea why Canonical should do anything about it.

---

### Post by cathy87 on 2013-02-03
Oh, you're right. Nvidia are the ones I have to thank for this mess... haha. Thanks, trying to sort it out in the terminal.
Is there a way to add drivers (in this case for a apple wireless keyboard) to GRUB?

---

