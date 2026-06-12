---
title: "Can you run Ubuntu on the Raspberry Pi?"
date: 2018-04-06
forum: General Help
---

### Post by timc00k on 2018-04-06
I know if you go to the Raspberry Pi website, the official OS that are approved included Ubuntu Mate, but not Ubuntu.

Is there not a version of Ubuntu from Ubuntu.com that would work on the Pi, something that would give me the familiar desktop that I am so used to?

Sorry if this sounds like a simplistic question, but I'm not overly familiar as to why Ubuntu Mate works, but not Ubuntu.

Thank you

---

### Post by QIII on 2018-04-06
Ubuntu MATE is an official flavor of Ubuntu.  Just as all the other official *buntus, it is maintained by a community authorized by Canonical.  Ubuntu has an ARMv7 port.  But because of the wide variety of individual peculiarities in ARM processors, organizations like Raspberry Pi have to further modify things for their particular hardware.

Since Canonical does not maintain the images, they are not "official".  But they aren't cheap knock-offs.

I know you can get an "official" server image for ARM from Canonical, but Canonical can't guarantee perfect fitness for any particular hardware.

On my cell right now so it's hard to give you a link, but google "ubuntu server for arm" and you'll find a Canonical page where you can download it.

---

### Post by timc00k on 2018-04-06
> **QIII said:**
> Ubuntu MATE is an official flavor of Ubuntu.  Just as all the other official *buntus, it is maintained by a community authorized by Canonical..

When you say that Mate is authorized by Canonical, what exactly does that mean?  I see various versions of *buntu come and go when developers abandon their projects or no longer are interested.

Canonical has been around for so long that I have faith in their reliability and their assurance to get security updates out.  I'm not so sure about the same level of commitment for *buntus that are downstream of the original Ubuntu.

---

### Post by &amp;wP*!) on 2018-04-06
According to [a German web site]("https://www.elektronik-kompendium.de/sites/raspberry-pi/2011041.htm") or [another one]("https://kofler.info/ubuntu-mate-16-04-raspberry-pi/"), it was chosen for its extremely light-weight setup. The original Ubuntu has too many packages and slow. Lubuntu and Xubuntu are lighter. Ubuntu Mate is much much lighter. Raspberry Pi is not a real PC or laptop, it has very limited resources (CPU speed, RAM etc). That's why it is reasonable that very light Ubuntu distro like MATE was tried.

A lot of websites point that Ubuntu Mate has still a lot of things to configured, be aware of that.

If you hit German websites, use Google translator.

---

### Post by QIII on 2018-04-06
There are lots of Ubuntu derivatives that have come and gone, but they were not officially sanctioned by Canonical.

See [www.ubuntu.com/download/flavor](www.ubuntu.com/download/flavor)

Mythbuntu has, unfortunately, met its demise.

At the bottom of that page is a link to a page that differentiates between official "editions", official flavors and independent derivatives.  Derivatives are not *buntus and should not bill themselves as such.

---

### Post by grahammechanical on 2018-04-06
Ubuntu flavours are developed by volunteers who may or may not be paid for their work. Canonical would not allow developers official status unless there was a reasonable expectation that the developers could maintain the flavour and keep up with the 26 weekly development schedule that canonical follows for Ubuntu. 

Life being what it is, we should not be surprised if some software projects based on volunteer workers fail from time to time.

There are Ubuntu Core images for the Raspberry Pi but do not expect an OS with a graphical desktop like the one on standard Ubuntu. Consider Ubuntu core to be a foundation on which to build your own OS for the device.

[https://developer.ubuntu.com/core/get-started](https://developer.ubuntu.com/core/get-started)



Regards.

---

### Post by HermanAB on 2018-04-07
Well, the trouble is that the gnome desktop system is ridiculously slow and would be unusable on a Pi.  So you are stuck with the simpler desktop offered by raspbian.

---

