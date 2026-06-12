---
title: "i can't finish installing lubuntu 18.4 on an old toshiba laptop with 512 mb"
date: 2022-07-25
forum: General Help
---

### Post by levideo100 on 2022-07-25
Hello everyone I would like to understand thanks to your help and skills if I can install lubuntu on an old toshiba satellite m40 282 laptop with only 512mb of ram and old generation mechanical hard disk and celeron centrino cpu at 1.86 ghz
I arrived in lubuntu and this version seems to me to be 18.4 after reading that it could be fine for old PCs even with only 512 mb
I hope this is possible.
on the pc in question I had windows xp sp3 with all the problems concerning the lack of windows security support being an operating system no longer supported and the native problems related to the windows architecture, I would like to know from you if I made the correct choice?
yesterday I tried to install lubuntu in its full version by eliminating xp with all the upgrades and selecting the installation of any third-party software, but the computer has installed part of linux without completing the installation after hours.
maybe in the end with these hardware requirements I discover that it is not possible, I would not like to waste too much time can you help me please?

my pc not advance about personal info ....... ?????
i dont'understand  it ;-((
thank you so much levideo

---

### Post by ajgreeny on 2022-07-25
Lubuntu 18.04 has been EOL (end of life) for over a year now so there is little point in trying to install it; you will not be able to add any new packages to it or carry out updates.

You do not say so, but I wonder if your computer is a 32bit machine in which case there is no Ubuntu family OS available to you.

Give us as much info on the hardware as you can, such  as the make of machine and what OS it currently runs, and we may be able to help you more but I have to warn you that you may have to move to another distro more suitable for such low spec hardware. Ubuntu and all its buntu relatives have possibly moved on and away from you and the machine you have.

---

### Post by Impavidus on 2022-07-25
Lubuntu 18.04 is no longer supported. The parts it has in common with Ubuntu 18.04 are still supported (until april next year) and the repositories are still available, so it's not as bad as completely unsupported, but it's better to avoid it. Nine months from now, Ubuntu 18.04 will change to extended security maintenance, for which you could sign up, but it comes with some limitations. I understood that one of the limitations may be that many packages will only be supported as a snap version, which means higher memory requirements, so that's not an option for you. Anyway, even if you can run an operating system on 512MB of memory, you'll be severely limited in the applications you can run. A text editor will be no problem, a word processor is harder and a web browser will be a bad experience.

Getting some more life out of that computer as a server may be a good idea, if you could use a server. Otherwise, there comes a day when the best use is recycling.

---

### Post by guiverc on 2022-07-25
Lubuntu 18.04 LTS is *end of life* as already stated - refer [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

That being said; I still have a ibm thinkpad t43 which has it installed.  I write about it on the Lubuntu discourse, with some clues on checking the support status for your install to see if you're happy with the system.

The default Lubuntu installer is `ubiquity` which needs your machine to have >700MB of RAM to have a chance of working as it states in the documentation; I prefer thinking of that as 768MB, but either way your 512MB is less than the minimum so the installer failing is expected (*the documentation warns of that*,* why the alternate ISO existed*)

As you gave no specifics as to which ISO you used (Lubuntu 18.04 was available with 6 ISOs, and only 1 had a chance of working on a machine with 512MB) I cannot comment further, but I'd check which you tried to use, and whether or not it was the one suggested for machines as little RAM as yours has.  The ISO in question wasn't a *live* ISO, just the debian installer, so it was less powerful - but that's why it worked with less RAM. There were things it couldn't do, just do that setup before hand using an easier ISO, then use the Lubuntu 18.04 ISO for your machine for the actual install only.

Every machine I used in testing Lubuntu (*and other Ubuntu flavors*) I also used for QA-testing [*non-free usually*] Debian ISOs, which are likely what I'd consider if I was still installing a 32-bit system.  I still use a few (*32-bit on occasion*), and all but one have Debian on them (*it's what the current t43 with Lubuntu 18.04 will get*).  

In most cases Debian & Lubuntu were ~*equal* (*in my QA-testing of Lubuntu (LXDE & LXQt) releases and Debian 8/9/10/11*), with only a single machine that performed better with Lubuntu, a machine I'd love to know why Debian performed so badly, but it was so underpowered I wasn't willing to fight with it to work out why Lubuntu performed better.  FYI:  I mention this, as that machine I gave up on had 1GB of RAM, and your 512MB machine reminds me of it, and using it was ***no fun***!.  Sure I could make it usable, but i'd install a server system on it, and use only a light WM maybe, but what you were going to use the machine for would really dictate how I'd use it.  Either way I'd probably build the system myself, as Lubuntu is created for machines with more grunt than yours appears to have (*modern web browsers assume >512MB of RAM so that's not a viable option; I'd likely use w3m/lynx but even they can be annoying for some web sites*).

---

