---
title: "Ubuntu 16.04 stuck after login"
date: 2019-02-16
forum: General Help
---

### Post by rodrigoneon on 2019-02-16
I recently installed Ubuntu 16.04 in a double boot system alongside my windows installation. My computer is an Acer predator Helios 300 laptop with an NVIDIA GeForce GTX 1050 ti graphics card and an Intel i7 processor.

Sometimes, Ubuntu boots normally and I can access the desktop just fine, but most of the time, after I write my password to enter my session, the boot up process fails and my computer is stuck showing my desktop background and the mouse which I can still move around.  I can't open a terminal from this screen and the only solution in order to get out of this loop is forcing the computer to power off and trying again.  

Of course, this is not enough most of the time. It usually takes me a couple of tries before I'm able to use Ubuntu normally.

I have the secure boot settings disabled, but I don't know what else can I do to fix this boot problem.  I'm  a linux beginner and I'm still getting used to the commands.

Any help is appreciated.

---

### Post by Hagar Delest on 2019-02-17
Do you mean 18.04? The 16.04 is almost 3 years old now.

Have you tried on a live USB key first? Have you tried another flavor like Xubuntu?

---

### Post by rodrigoneon on 2019-02-19
I ran into similar issues with ubuntu 18 so I decided to install an earlier version.

Unfortunately, right now I dont have the time to completely re-install ubuntu again (I'm mostly using it for ROS).

Apparently, running ubuntu on recovery mode first somehow bypasses the issue.  But the problem still persists.

---

### Post by monkeybrain20122 on 2019-02-19
> **Hagar Delest said:**
> Do you mean 18.04? The 16.04 is almost 3 years old now.


Yes but still more stable and bug free than 18.04. :)

---

### Post by monkeybrain20122 on 2019-02-19
> **rodrigoneon said:**
> I recently installed Ubuntu 16.04 in a double boot system alongside my windows installation. My computer is an Acer predator Helios 300 laptop with an NVIDIA GeForce GTX 1050 ti graphics card and an Intel i7 processor.


I have the secure boot settings disabled, but I don't know what else can I do to fix this boot problem.  I'm  a linux beginner and I'm still getting used to the commands.

Any help is appreciated.

What if you enable secure boot? I don't use Windows but from posts on this forum if secure boot is enabled for Windows in a dualboot then it has to be enabled for Ubuntu as well in a dualboot apparently but I don't know what would happen if it is disabled (no Windows? No Ubuntu? or something like you experienced?)

---

### Post by rodrigoneon on 2019-02-20
I already tried that.  The error still persists no matter if secure boot is on or off.  The issue seems more likely related to the graphical card I'm using, or so I'm reading.

---

### Post by col48 on 2019-02-20
Would a look at system logs shed light?  Perhaps comparing a login that worked with one that failed?

---

