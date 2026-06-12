---
title: "Looking for a linux operating system that will run on a windows XP built in 2003"
date: 2019-11-09
forum: General Help
---

### Post by SUPERFITTER on 2019-11-09
I have an old emachine that was dual booted with windows XP and Ubuntu 12.04.  It still runs, but no updates obviously. I'm looking for a linux operating system that will run on a windows XP built in 2003.  I want to wipe the drive and install a new system.  Is this still possible?

Thank You
Dennis

---

### Post by CatKiller on 2019-11-09
It depends on how old and decrepit it is.

If it's 64 bit, installing a new OS will be fine. Your use of it will largely be limited by the amount of RAM, but it's really websites rather than the OS that pushes that. Gnome won't perform well on slow hardware, but Xfce, LXQt or KDE would be fine if you have enough RAM.

If it's 32 bit then it's not worth bothering with. Get a Raspberry Pi and have a better machine.

---

### Post by TheFu on 2019-11-09
Support for CPUs prior to the i686 was dropped by the kernel a few years ago and Canonical has dropped 32-bit support beginning with 19.10 (I think, but don't quote me).  AMD and Intel i686 CPUs should work with a 32-bit Debian OS, but the lesser known clones from Cirrus and Via that claim to be i686 are missing some required i686 instructions, so those will not work.

+1 for using a Raspberry Pi v3/v4 which will be faster for most common uses of a desktop.  Also, agree on avoiding Gnome3 and going with a light GUI instead.  With any newer hardware, you'll likely need a newer monitor with HDMI, keyboard, and mouse with USB.  A key consideration for any Raspberry Pi is to get a quality power supply. Don't just use any microUSB charger, but get a real pi-ready PSU for the device you'll have.  I think a r-Pi v4 is 2x faster than the v3, so well worth getting.  

It might be better to just get a used Acer C720 chromebook for about $65 if you just need a web/video machine. Just be certain to check that the CPU inside any chromebook has at least 1500 passmarks.  I wiped ChromeOS on my C720 and loaded a lightweight Ubuntu desktop.  Used that for about 3 yrs.  To accomplish that requires some hardware changes, replacing the firmware, swapping the m.2 SSD out, so the comfort and ability to do those things would be needed. These changes break the warranty, if any is left.

---

### Post by tea for one on 2019-11-09
> **SUPERFITTER said:**
> I have an old emachine that was dual booted with windows XP and Ubuntu 12.04.  It still runs, but no updates obviously. I'm looking for a linux operating system that will run on a windows XP built in 2003.  I want to wipe the drive and install a new system.  Is this still possible?

Thank You
Dennis

Have a look at Antix

[http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html#_system_requirements](http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html#_system_requirements)

---

### Post by crip720 on 2019-11-09
Can also try Puppy, Tiny, or Damm Small Linux, they will work with minimum specs that your machine will beat.  Lubuntu/Xubuntu should work also if you go easy, but might only give you a couple more years before dropping 32 bit.

---

### Post by Skaperen on 2019-11-09
for 32-bit, go with Xubuntu 18.04 LTS on anything under 2 Ghz and/or fewer than 4 cores.  boost its RAM if you can.  i've had old machines that were limited to 2 GB of RAM because of 32-bit limitations.  LTS should be supported for 5 years, so you should be able to run it until 2023.  beyond that there should still be something familiar that can, like maybe Debian itself.  beyond that i expect Gentoo and Slackware to support 32-bit for a while.  the embedded distros should be doing 32-bit for years as that market will be using them probably forever.  you can still buy 8-bit CPUs.

---

### Post by SUPERFITTER on 2019-11-09
Thank you all for the help.  I forgot to post the specs: Processor 2Ghz AMD Mobile Athlon 64, 1152 mb Ram, 52.82 Gb Hard drive, x86

---

### Post by Skaperen on 2019-11-09
can you get more RAM for that?

---

### Post by SUPERFITTER on 2019-11-10
no

---

### Post by Impavidus on 2019-11-10
I've still got a very similar computer running Xubuntu 18.04. The processor is 64 bit, but with only 1GB memory I use 32 bit. It helps that it has a somewhat powerful GPU for a computer of that age.

LTS releases of Xubuntu are supported for 3 years. What will happen to this old computer when Xubuntu 18.04 reaches end of life in 2021 I don't know. Probably the recycling centre.

---

### Post by mörgæs on 2019-11-10
With one GB of memory I suggest that you install a 32 bit OS even though your processor is 64 bit capable (ninja'ed by Impavidus). 

Here are some ideas to [mitigate the memory problem]("https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289").

Many options are available ([Debian]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890") is one of them) but stay away from Damn Small Linux as it's an abandoned project.

---

### Post by guiverc on 2019-11-10
I have a couple of equivalent systems (2x t43 thinkpads, a r50p thinkpad, and dell 610; single core pentium M, 1.5gb ram for the one I use most regularly; 1gb ram in the others) and use Lubuntu 18.04 LTS  (equivalent to Xubuntu; in fact most have have Xubuntu (XFCE) desktops installed too so I can use XFCE or LXDE selecting at login.

Mine are x86 (32bit or i686 only) so I cannot boot a amd64 image, and they were used for testing Xubuntu & Lubuntu up until they stopped producing x86 ISOs in Dec 2018 (mid 19.04 cycle).  I'm not familiar (*or don't remember*) the [COLOR=#000000]AMD Mobile Athlon 64[/COLOR] but I'd suggest either Lubuntu or Xubuntu 18.04 LTS letting your preference of GUI let you decide.

If you didn't like either, I'd suggest Ubuntu-MATE 18.04 LTS next, but you're starting to get heavier which means you have less memory/resources for programs.

I'm guessing your cpu could run amd64 (x86_64) however the larger addresses do mean slightly more overhead on your very limited RAM, so I'd be tempted to use x86 images (despite having fewer choices); but I've only used amd64 on boxes with more than 1gb of RAM so the impact may not be noticeable.

---

### Post by Rubi1200 on 2019-11-10
I'm running MX Linux on an old (7 or 8 years ago) Acer netbook with 1GB of RAM and other than being a bit slow to open Firefox the first time everything runs pretty smoothly.

Worth taking a look at in my opinion.

---

### Post by Artim on 2019-11-10
Another vote for [COLOR=#0000cd]**Xubuntu**[/COLOR].  Make it lighter yet by using lightweight applications like Abiword and Gnumeric in place of LibreOffice, etc.

---

### Post by ajgreeny on 2019-11-10
Can I also suggest you have a look at Debian-10 (Buster).

Install it using the Netinstall CD version from [https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-10.1.0-i386-netinst.iso](https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-10.1.0-i386-netinst.iso) and during the install choose to add the LXDE desktop; that will avoid a lot of bloat.

I am currently using it on an old netbook with an Atom-N270 1.6GHz, and only 1G RAM, and unfortunately for Lubuntu, the Debian install is a lot faster.  It's the first time I have ever tried Debian and kept it but the speed advantage over Lubuntu is impossible to ignore.

Debian uses Firefox-ESR which may be fine for you, but if not you can always remove it and either try the standard Firefox version (download the .tar archive and then run it from the executable without installing if that's easier for you) or you can try the low resource browser **epiphany** which is what I am using.

---

### Post by dragonfly41 on 2019-11-10
[FreeBSD]("https://www.freebsd.org/") popped up in a recent article I read (I have not used it).

Actually I  have found the [link to the article]("https://www.quora.com/What-is-a-good-alternative-to-Windows-Apple-and-Linux-Ive-been-using-Windows-since-3-1-but-it-fell-apart-with-8-and-is-getting-worse-MacOS-is-out-of-the-question-and-Linux-seems-complicated-to-operate").

---

### Post by oldrocker99 on 2019-11-10
Also, old memory such as that old deck has can probably be procured cheaply, and I do mean cheap, to make everything run a lot more smoothly. The 3.64 or whatever amount of RAM that a 32-bit CPU can address is a big limitation in these modern days.

And, since the OP has a 64-bit CPU, there's no real reason to not install it that I can see.

Also, a nice lightweight OS is Ubuntu MATE, which is very easy to learn, and very easily configured. Not as ultra-lightweight as Lubuntu, but an old PC with more RAM would handle it very, very well.

---

### Post by SUPERFITTER on 2019-12-21
I found another problem, after trying different distros.  The laptop is so old that it only uses WEP encryption:sad:,  I have WPA2.

---

### Post by ajgreeny on 2019-12-21
A low cost USB wifi adapter may be your only answer to that; don't use WEP as it's far too easy to hack into giving you almost no security.

I will have to leave you to search for the adapter as I've not had a wifi problem for years so therefore have no experience of any USB adapters.

---

### Post by TheFu on 2019-12-21
> **SUPERFITTER said:**
> I found another problem, after trying different distros.  The laptop is so old that it only uses WEP encryption:sad:,  I have WPA2.

Disable the wifi card in the BIOS, then buy a cheap, supported, USB-to-wifi-AC device.

 Provided it has USB2, the speed should be ok.  The hard part is getting a well-supported USB-to-wifi device that does not require hassles to get working. I use wired ethernet with my laptops. Wired is always better than wifi. There are a few threads in these forums about usb-wifi adaptors.

OTOH, I wouldn't spend over $15 trying to make this computer work. Lots of HW issues are likely to start just due to age. The HDD looks really old, for example.

---

### Post by kurt18947 on 2019-12-22
I tend to agree with TheFu. I'm no fan of disposing of functioning hardware but there comes a time where it's possible but impractical to upgrade existing hardware.

---

### Post by guiverc on 2019-12-22
I used IBM Thinkpad T43, dell Latitude 610 & other like systems in testing Lubuntu & Xubuntu up to and including the 19.04 cycle (or Dec 2018 when x86 ISOs were dropped).  The only reason I didn't use older laptops (eg. IBM Thinkpad R50p) was many of them didn't boot thumb-drives and I wasn't willing to write a DVD-RW just for them [to test] every few days.

I'm of the opinion that yes Lubuntu & Xubuntu will run; in fact many other flavors also had a 18.04 LTS release which has supported until 2021-April; but I'd stick with Lubuntu or Xubuntu myself.

Would I want to use it?    Yes in most cases I would, as I still use my thinkpad R50p from 2003 and use it way more than my raspberry pi 2b+.  It very much depends on what I wanted to do with it, as whilst i love the form factor & screen of my r50p (even with ~15min life battery), it's 1GB of memory & single-core CPU means I think about what I do with it (eg. I went and looked and it had 2x vlc loaded, 2x terms & 2x file managers, if I wanted to load a browser I'd probably close the vlc windows first because of it's lack of ram).

Personally if I wanted to stream youtube, I'd probably opt for the dell latitude 610 which has the same processor, RAM but a different video card (i915) that's performs better ... ie. your hardware plays a part in the usefulness of your hardware). The thinkpad's (r50p, t43, t43p) had better video cards (according to sales literature) than the latitude 610 I have (t43's have 1.5gb of ram which is more than r50/d610 too) - however for some tasks the i915 video chipset is the winner for me; because the intel has a better linux driver than amd's radeon.  For most tasks this won't matter, but for some it does make a difference (lack of screen tearing on videos; yes you can stop it - but that has costs that I'm not sure are worth it)

Yes you can. In the Ubuntu family I'd opt for Lubuntu 18.04 LTS or Xubuntu 18.04 LTS.  With ~1GB only of RAM I'd suggest being careful with program choice due to your limited RAM. If you want to have your system supported beyond 2021-April think about Debian (though it has a smaller support community, requires a little more technical knowledge)

FYI: I tested debian buster (10) using the d610, t43 & other x86 boxes too, debian has non-free ISOs which on most hardware performed really well (on par with *Ubuntu); with one video card (two boxes) it made me appreciate how much easier *Ubuntu is.

---

### Post by mörgæs on 2019-12-22
Where do you live? If you live in the countryside where it's unlikely that any black hat will be able to notice your signal then a weak encryption is fine. 

If you want strong encryption: 
Normally it only takes a small Philips screwdriver to swap the wifi card. I have done that on many occasions. 

In addition to better encryption a newer card might also support a faster 802.* protocol.

---

### Post by kurt18947 on 2019-12-22
> **mörgæs said:**
> Where do you live? If you live in the countryside where it's unlikely that any black hat will be able to notice your signal then a weak encryption is fine. 

If you want strong encryption: 
Normally it only takes a small Philips screwdriver to swap the wifi card. I have done that on many occasions. 

In addition to better encryption a newer card might also support a faster 802.* protocol.

One thing to watch out for when swapping notebook wifi components. Thinkpads (and others?) whitelist WiFi adapters. You must use one of the whitelisted adapters. The simplest work-around is a USB device. I've read that the newer Thinkpads don't whitelist but I don't know if that's true. I don't know what other manufacturers, if any, whitelist WiFi hardware.

---

### Post by corradoventu on 2019-12-22
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Ubuntu 14.04 with ESM option will be supported up to April 2022 
Ubuntu 16.04 with ESM option will be supported up to April 2024
ESM option is FREE
[https://ubuntu.com/esm](https://ubuntu.com/esm) [https://ubuntu.com/blog/extended-security-maintenance-ubuntu-14-04-trusty-tahr](https://ubuntu.com/blog/extended-security-maintenance-ubuntu-14-04-trusty-tahr)

---

### Post by TheFu on 2019-12-22
> **corradoventu said:**
> [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Ubuntu 14.04 with ESM option will be supported up to April 2022 
Ubuntu 16.04 with ESM option will be supported up to April 2024
ESM option is FREE
[https://ubuntu.com/esm](https://ubuntu.com/esm) [https://ubuntu.com/blog/extended-security-maintenance-ubuntu-14-04-trusty-tahr](https://ubuntu.com/blog/extended-security-maintenance-ubuntu-14-04-trusty-tahr)

Technically true, but is isn't automatic and logins to Canonical ESM are mandatory.
16.04 Server is supported until 2021 ... May-ish without providing Canonical extra access or data. I don't keep up with Desktop support timeframes, since some are 3 yrs and others are 5.  It is just too confusing to me.

The ESM options are meant for servers.  

Running ```

$ sudo ubuntu-support-status
Support status summary of xxxxxx:

You have 1656 packages (68.0%) supported until April 2021 (Canonical - 5y)
You have 62 packages (2.5%) supported until April 2021 (Community - 5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
**You have 716 packages (29.4%) that are unsupported**

``` 
716 unsupported packages on a "supported" OS.

---

### Post by SeijiSensei on 2019-12-23
For a USB wifi adapter, I recommend [https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY](https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY)

Supports N speeds and works out of the box with Linux. Pretty good range considering its size, too.  The form factor lets you plug it into a USB port and forget it's there.

---

### Post by hk42 on 2019-12-23
I have always thought that WI-FI encryption had nothing to do with hardware but was a 
drivers/software problem.
It may be worth looking in that direction.
But if the hardware is too old or bugged may be no one improved it's drivers.
If recent devices do the encryption themselves this saves processor time so it is good too.

---

### Post by oldrocker99 on 2019-12-23
Ubuntu isn't the only choice. Here are some other very lightweight distros:[https://itsfoss.com/lightweight-linux-beginners](https://itsfoss.com/lightweight-linux-beginners). Also, Manjaro is continuing to supply 32-bit distros:[https://manjaro.org/download/32bit/32bit-xfce/](https://manjaro.org/download/32bit/32bit-xfce/).

---

