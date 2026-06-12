---
title: "No sound out of my headphones"
date: 2018-09-05
forum: General Help
---

### Post by lilongueti on 2018-09-05
I decided to bring life back to my old gateway M-6804m with a fresh install of lubuntu 18.4.5,
now its not the first time this always happens when i first install os on this machine but i used to solve it following these steps posted by @Wootyeah over here
[https://ubuntuforums.org/showthread.php?t=1250802](https://ubuntuforums.org/showthread.php?t=1250802)

"5.  I downloaded and installed the latest alsa-driver:
sudo apt-get install alsaconf
sudo apt-get install alsa-base alsa-utils
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")
tar -xjf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
./configure
sudo make
sudo make install 
6.  This didn’t seem to make much of a difference, so I looked around  and tried a script I found here to download and install the latest  snapshot. Again, this first didn’t seem to make much of a difference.  Until I looked at the following list of models:
7.  gedit /usr/src/Alsa-1.0.20/alsa-driver-1.0.20/alsa-kernel/Documentation/HD-Audio-Models.txt
This file reveals the following list of models for STAC9205/9254:

ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron
eapd Keep EAPD on (e.g. Gateway T1616)
auto BIOS setup (default)

Compared to the previous version that shipped with Ubuntu, there are two  new entries, eapd and auto now. The eapd (external amplifier power  down) option looks quite promising, so back to… 
8.  sudo nano /etc/modprobe.d/alsa-base.conf
and added the following line:
options snd-hda-intel model=eapd probe_mask=1 position_fix=1

Restart and success! The headphones finally work properly. If you were  having similar problems and found this blog in the attempt to find a  solution, I hope these steps could help you a bit further in your quest.  I can imagine that other headphone issues could perhaps be solved as  well, with an alsa-upgrade and adjustments to alsa-base.conf."

however since alsa is now obsolete im clueless about how to fix this on 18.4

---

### Post by lilongueti on 2018-09-05
Already found the solution over here [https://ubuntuforums.org/showthread.php?t=1043568](https://ubuntuforums.org/showthread.php?t=1043568)
i just had to add that same line "options snd-hda-intel model=eapd probe_mask=1 position_fix=1" at /etc/modprobe.d/alsa-base.conf

---

### Post by mörgæs on 2018-09-05
Good, please mark the thread solved.

---

