---
title: "Fresh Install 16.04 over old partition data fails due failure config package manager"
date: 2017-09-01
forum: General Help
---

### Post by gbambo on 2017-09-01
After 4 consecutive failed attempts to install presently posted alpha of 17.04 server, I took advice to install 16.04 LTS.

Result even worse. Unable to complete installation at all.

I thereby cannot post suggested diagnostics. What is going on? 40 years experience. It's not me that the problem.

Specifications
i7-950 Bloomfiield quad hyperthreading 3.05ghz
2tb (1,836gb) Sata3 x 2 Enterprise-grade
     HGST HUS724020ALA640
48gb DDR3-1600 run @ 1066 in 3 ch mode
Mobo = MSI A7522IMT v8.14b8  110912 <- BIOS vers
     model = MSI X58 Pro (released 2009)
     no UEFI support
1gbps Intel Pro/1000 GT

---

### Post by QIII on 2017-09-01
I have 40 years of experience and I seem to get along just fine with Linux.

Would you please be a little less vague than " Unable to complete installation at all."?  Precious little to work with, that.  What *does* happen?

---

### Post by Geoffrey_Arndt on 2017-09-01
I've read all your posts of past day or so.   Suggest you scale back the type of install to latest LTS (16.03.3) of either Ubuntu Mate or Xubuntu desktop.    Then add server packages if needed.    These DE's don't require 3d hardware acceleration (as does Unity and others using Gnome3 (Mint Cinnamon, etc.).   This will make it much easier to clarify what is causing your less than positive experience.

---

### Post by lisati on 2017-09-01
> **QIII said:**
> I have 40 years of experience and I seem to get along just fine with Linux.
Same here. We can be thankful that we don't have to deal with punched cards, paper tape, or massive hard drives that can hold what would be a miniscule amount of data by today's standards.

---

### Post by gbambo on 2017-09-02
This is a joint response to several answers. I am thankful to be finally getting some feedback!

I stepped back to 16.04. First try the installer failed to complete, stating "failed to configure package manager". I am afraid I did not note which step of installation this happened at.

Next attempt, same image, same burn of same image, same target machine, the install completes, but I can not install a desktop.

As several have suggested installing a desktop on server is harder than installing a server on desktop, I will try that next. 

When I say I don't think my problems are hardware, I suggest one example is keyboard mapping. I told it not to test my keyboard, but rather let me specify it. So how could a hardware problem result in the installation of the wrong keyboard map?

Meanwhile, I don't think this can be entirely about my inexperience, as I have installed Linux dozens of times in the past (using nearly a dozen different distros) and never had these kinds of experiences. In fact, in the past, I have had no trouble with Ubuntu, Kubuntu, or Lubuntu. So I am very confused how my "luck" has been completely transformed and why it only involves one distro.

Is my mistake in thinking installing a desktop should not be highly difficult?? I rarely, if ever, tried that in the past.

---

