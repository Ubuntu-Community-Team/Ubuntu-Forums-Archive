---
title: "Question about Ubuntu before using"
date: 2006-12-31
forum: General Help
---

### Post by xShrimp on 2006-12-31
Hey guys, my first time here.

I am planning to try out Ubuntu, but before I do I have some questions.
My current computer is running XP Home SP2, and my questions are:
1. If I install Ubuntu, what will happen to my drivers (video, audio, etc)? Will I need to find drivers for them compatible with Linux?
2. What anti-virus/security application works best with it?
3. Whats the ease of installing and using?

---

### Post by ~LoKe on 2006-12-31
1.  Most drivers are fine out of the box, because they're included.  You **may** want to use a different video driver, but the stock one will work.  As for audio, well, the drivers are fine but you'll need some codecs.

2.  Not required.  Linux variants are still considerably safe and protected against these things.

3.  Very easy.  Step by step GUI installer.

---

### Post by Ziggy72 on 2006-12-31
As a first time user of Ubuntu I assume you will dual boot? If you do, I suggest that you save your MBR before embarking on the dual boot installation - just in case something goes wrong and you need to recover:mrgreen: .

I agree with ~Loke's comments but a firewall is probably a good idea. Firestarter (installed with Synaptic) once you're up and running seems to be well recommended.

---

### Post by ~LoKe on 2007-01-01
> **Ziggy72 said:**
> As a first time user of Ubuntu I assume you will dual boot? If you do, I suggest that you save your MBR before embarking on the dual boot installation - just in case something goes wrong and you need to recover:mrgreen: .

I agree with ~Loke's comments but a firewall is probably a good idea. Firestarter (installed with Synaptic) once you're up and running seems to be well recommended.

Most people in modern time own a router in one form or another.  Anyways, a router is only good if you're expecting intruders who **really** want to get in.  For the average person, it's pretty useless.

---

### Post by meng on 2007-01-01
> **Ziggy72 said:**
> As a first time user of Ubuntu I assume you will dual boot? If you do, I suggest that you save your MBR before embarking on the dual boot installation - just in case something goes wrong and you need to recover:mrgreen: .

I agree with ~Loke's comments but a firewall is probably a good idea. Firestarter (installed with Synaptic) once you're up and running seems to be well recommended.
Doesn't fixmbr utility come on the Windows install disk?

---

### Post by ~LoKe on 2007-01-01
> **meng said:**
> Doesn't fixmbr utility come on the Windows install disk?

Yep.  In addition to that, Ubuntu doesn't ***-rape the MBR, only Windows does that.  Go figure.

---

### Post by mdurham on 2007-01-01
> **Ziggy72 said:**
> As a first time user of Ubuntu I assume you will dual boot? If you do, I suggest that you save your MBR before embarking on the dual boot installation - just in case something goes wrong and you need to recover:mrgreen: .

I agree with ~Loke's comments but a firewall is probably a good idea. Firestarter (installed with Synaptic) once you're up and running seems to be well recommended.

just for reference, Firestarter is NOT a firewall, nor does it 'start' anything. It's a very badly named app.

---

### Post by rovernaut on 2007-01-01
There's Guard dog in the repositories. via Adept or synaptic.
 it needs a little configuring in what you allow access to net

---

### Post by Tux Aubrey on 2007-01-01
If you boot from a live CD, you will have a chance to see what works for you and what doesn't (ie. drivers etc).  I'd recommend trying the live CD for a few days before you commit.  I've never had a real problem myself, but browsing posts here throws up some show-stopper issues for some people.  Read a few basic "How-Tos", especially [_[COLOR="Blue"]psychocats[/COLOR]_]("http://www.psychocats.net/ubuntu/") to help guarantee a pleasant experience.

Oh...welcome!

---

### Post by Sef on 2007-01-01
[QUOTE]just for reference, Firestarter is NOT a firewall, nor does it 'start' anything. It's a very badly named app.
/QUOTE]

Firestarter is the front-end gui for IPTables, a firewall.  It works well.

---

### Post by xShrimp on 2007-01-01
Can someone explain "MBR"? and How do I save it?
Does a dual-boot mean selecting an OS at boot? Then yeah, I'll be dual booting.

BTW, are there any codecs Linux can't support that XP can?

Thanks for all your input

---

### Post by Sef on 2007-01-01
> Can someone explain "MBR"? and How do I save it?

In Ubuntu, MBR is GRUB, which is the boot manager.  It is installed during the installation.  If you dual boot, you will have a choice to boot from either Ubuntu or the other operating system (Usually Windows.)

> Does a dual-boot mean selecting an OS at boot? Then yeah, I'll be dual booting.


Yes, the default is Ubuntu.  You can choose to boot into your other operating system, but using the down arrow button.

> BTW, are there any codecs Linux can't support that XP can?

Anything with DRM (Digital Restricted Management) codecs can't usually be played on Linux.

---

### Post by xmastree on 2007-01-01
> **xShrimp said:**
> Can someone explain "MBR"? and How do I save it?
I wouldn't worry about that jsut now. It's 'Master Boot Record' and will be changed when you install ubuntu.
> Does a dual-boot mean selecting an OS at boot? Then yeah, I'll be dual booting.
Before you do, you'll need to make some free (unformatted) space on the disk for it.
then, the installer wil give you the option to use it, and the dual-bot menu will be set up automatically.

---

