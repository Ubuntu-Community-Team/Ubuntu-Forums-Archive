---
title: "Lubuntu - Dell Inspiron 11 - 3162 Booting Problem"
date: 2019-12-22
forum: General Help
---

### Post by mansakorawa on 2019-12-22
Hi All,

I've installed Lubuntu (lubuntu-18.04-alternate-i386.iso) in my wife laptop (Dell Inpiron 11 - 3162, 2GB Ram, Celeron(R) N3050 1.60 GHz).
But I can't boot normally. I am using legacy.

First time, black screen with only top right cursor.
Then I use the grub option and edit with "nomodeset", screens turned white. [IMG]https://ibb.co/b51qwdK[/IMG][IMG]https://ibb.co/b51qwdK[/IMG]

Then I use the grub option and chose recovery mode -> repair (dpkg) -> resume boot normally.
Finally, I am inside the OS, but after restart/shutdown, I'm back with the black screen, like the first time.

Also, when I go to set hotkeys in Lubuntu, I can't scroll down, but other apps works well (firefox, leafpad).

Kindly help to solve this, since my wife isn't familiar with computer, so she can use this without the grub options workaround.

Thanks in advance.

---

### Post by guiverc on 2019-12-22
Firstly are there reasons why you chose what you did?
- i386 or 32-bit doesn't have an upgrade path?  n3050 is amd64.
- the alternate installer was intended for machines with less than 700MB of ram.

I suspect your first issue is related to graphics hardware, I would use `sudo lshw -C video` (which uses `sudo` to elevate privileges, `lshw` to list-hardware and "-C video" to limit output to class=video. There are other ways of getting this info, but this one at least I remember.

---

### Post by mansakorawa on 2019-12-22
Hi guiverc,

Thanks for the reply. So what's the ISO you recommend for this laptop? It's safe to use the standard ones?
Is 32 bit better than 64 bit for this laptop?

I just want a lightweight OS that is stable and perform good, since the ram is kinda small, only 2 GB.
It's no issue when using puppy linux or core linux. But since my wife is accustomed to windows, so I want to give her the practical out of the box OS that suits the hardware.

---

### Post by guiverc on 2019-12-22
Firstly I'd suggest downloading Lubuntu from an official site, thus I'd avoid asking google where to get the file from, but go to ubuntu.com and look there, ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)  will send you to the official flavor site.

I'll also state AMD64 is correct, being called that officially (x86_64 is another name) as AMD created the compatible 64-bit bit command set modern processors use for that architecture (intel tried to get the market to use it's incompatible IA64 but the market wanted to use to use x86 compatible .. so both intel & amd use amd64 today).

Ubuntu 18.04 LTS x86 is supported until 2021-April, so if there is any chance you'll want to upgrade to a later OS, such as Lubuntu 20.04 LTS I would opt for x86_64 as it has upgrade paths.  Lubuntu 18.04 was the last release using the LXDE desktop, and LXDE to LXQt upgrades haven't been supported until now, so may not be anyway for 18.04 -> 20.04, but I know it's possible as I release-upgraded this box I'm using to type this - so if upgrade path is to be considered I would say x86_64/amd64 wins hands down.

I have a thinkpad sl510 with only 2gb of RAM, and use x86_64/amd64 on it. Yes I considered i386 (what Debian/Ubuntu still call i686 or 32-bit) as memory addresses are smaller, there is less overhead for some JUMP operands - but that overhead is minimal, and you lose some processor optimization benefits that take away from using slightly less memory. Your usage will dictate which is the greater benefit - but it's pretty much equal in my experience.

---

### Post by mansakorawa on 2019-12-22
Ok guiverc, many thanks for the guidance. Much appreciated. :)

---

### Post by mörgæs on 2019-12-22
If you go for the 64 bit route I recommend a fresh install of Lubuntu 19.10. As explained above 18.04 is based upon LXDE which is a dead-end. Better to get to LXQT from the beginning. 

Also, if your wife is used to Windows' look and feel then I guess that she will be more delighted with the LXQT user interface.

32 bit is not necessarily a bad choice and with 2 GB of memory there are arguments both pro and con. Just remember that you have to change to another 32 bit distro in april 2021 as 18.04 is the last 32 bit release within the Buntu clan.

---

