---
title: "installing kubuntu on second partition from ubuntu"
date: 2008-06-25
forum: General Help
---

### Post by 2cute4u on 2008-06-25
OK I have a few empty but already formatted ext3 partition on my hard disk.  I'd like to do a clean install of kubuntu on one of them.   Rather than downloading the and burning the LiveCD,  is there a way that I could get just get synaptic, aptitude or at-get. to install kubuntu-desktop to that partition?

---

### Post by logos34 on 2008-06-25
> **2cute4u said:**
> is there a way that I could get just get synaptic, aptitude or at-get. to install kubuntu-desktop to that partition?

yeah, the kubuntu-desktop is a metapackage that installs on the same partition...You just logout and login to the kubuntu session.

sudo apt-get install kubuntu-desktop

---

### Post by 2cute4u on 2008-06-25
> **logos34 said:**
> yeah, the kubuntu-desktop is a metapackage that installs on the same partition...You just logout and login to the kubuntu session.

sudo apt-get install kubuntu-desktop

I don't want to install it on the same partition, as ubuntu, I already know how to do that.   The idea is to have a clean install of Kubuntu with no GTK apps or libraries, on one partition, and not put any QT apps or libraries on my ubuntu partition

---

### Post by logos34 on 2008-06-25
what about the [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD")? still have to burn a cd, but it least it only takes a few minutes to dl.  Install the base package, then apt get k desktop

---

### Post by 2cute4u on 2008-06-25
> **logos34 said:**
> what about the [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD")? still have to burn a cd, but it least it only takes a few minutes to dl.  Install the base package, then apt get k desktop

I'm trying to do it without having to burn a CD. I don't care about the time, it will take just as long to do a net install as to download a CD.

---

### Post by logos34 on 2008-06-25
> **2cute4u said:**
> it will take just as long to do a net install as to download a CD.

no, a lot less time because you will only install the base + kubuntu-desktop (you have to download the latter no matter whether via apt-get or whatnot).  

You might try the minimal cd iso (without actually burning cd) with a direct hard disk installation:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Or from usb stick.

good luck

---

### Post by 2cute4u on 2008-06-25
> **logos34 said:**
> no, a lot less time because you will only install the base + kubuntu-desktop (you have to download the latter no matter whether via apt-get or whatnot).  

You might try the minimal cd iso (without actually burning cd) with a direct hard disk installation:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Or from usb stick.

good luck

Yes I could do that but that, but that's still burning a CD image, just to a partition rather than a physical CD.  I don't think I'm making myself clear,  for me  this isn't just about having the end result of a kubuntu partition. Its about solving the question of how to do it, without having to leave  without having to leave the my ubuntu desktop environment.   

To me, it seems to me that standard package tools SHOULD be able to do the installation,  and thats what I want to know how to do. So, while  I really appreciate your effort in anweing my post,  I'm still left with the question of how do i do that.

 The main thing that keeps me from doing it is that I don't know how to tell synaptic, apt get, or aptitude to install  to a different partition.   I've tried to search the forums/web for the answer, but I haven't been able to come up with the right search terms to find the information I'm looking for

---

### Post by logos34 on 2008-06-25
ok, I think I understand you now.

I'm not aware of way to do what you're asking, but hopefully someone with a solution will post and enlighten us both.

---

