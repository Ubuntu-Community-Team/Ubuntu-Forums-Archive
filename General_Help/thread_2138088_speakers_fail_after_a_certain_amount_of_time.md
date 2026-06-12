---
title: "speakers fail after a certain amount of time"
date: 2013-04-22
forum: General Help
---

### Post by faust99 on 2013-04-22
This problem is giving me more gray hairs....perhaps somebody would be kind enough to advise. I'm using 12.10 on a lenovo x201 laptop.

After booting, I have sound though my laptop speakers. However, after some time (varies; 2minutes-120minutes), the speakers fail (i.e. no more sound through speakers). However, headphone jack continues to work.

The only solution is to reboot, after which the problem occurs again sometime later.

I've tried [position reporting ]("https://wiki.ubuntu.com/Audio/PositionReporting") but to no avail.

Also, adjusting alsamixer settings has no effect. 

Adding ubuntu-audio-dev ppa and running dist-upgrade has no effect.

The most frustrating thing is that I had this problem solved for some time, but it started to occur again two days ago. Unfortunately none of the steps I took back then seem to be working this time around. I remember the last thing I tried (which worked until the other day) were the instructions [here]("http://hanynowsky.wordpress.com/2012/10/17/ubuntu-12-10-quantal-on-dell-xps-15-l502x/):"):

```
sudo add-apt-repository -y ppa:ubuntu-audio-dev/ppa
 sudo apt-get update
 sudo apt-get dist-upgrade
 
 sudo apt-get -y install linux-sound-base alsa-base alsa-utils libasound2
 
 sudo apt-get -y install gdm ubuntu-desktop linux-image-`uname -r`
 
 sudo apt-get -y --reinstall install libasound2 linux-sound-base alsa-base alsa-utils
 
 sudo apt-get -y --reinstall lightdm ubuntu-desktop linux-image-`uname -r`
 
 killall pulseaudio
 
 rm -r ~/.pulse*
 
 sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

However running these commands seems to have no effect anymore. 

Please advise,

---

### Post by Diametric on 2013-04-23
Have you checked log files for any weird hardware failures?  Might also want to post the contents of

```
cat /proc/asound/cards
```

to let folks know what hardware you're using.

Good luck.

---

### Post by faust99 on 2013-04-23
> **Diametric said:**
> Have you checked log files for any weird hardware failures?  Might also want to post the contents of

```
cat /proc/asound/cards
```

to let folks know what hardware you're using.

Good luck.

Thank you. I'm not sure what to look for in the log...

Hardware I'm using is:

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2520000 irq 45
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 6QHT31WW-1.12

---

### Post by Diametric on 2013-04-23
Ok, so from that, it appears the card is supported (the system identifies the driver).  Give this site a glance and it may help:  [http://www.dedoimedo.com/computers/linux-hardware-troubleshooting.html](http://www.dedoimedo.com/computers/linux-hardware-troubleshooting.html)

Keep in mind that some things have changed.  For example, the site mentions /var/log/messages which isn't available in your version - you'll wnt to check /var/log/syslog instead.  I'd begin by grepping for key words from that log.

---

### Post by faust99 on 2013-04-23
> **Diametric said:**
> Ok, so from that, it appears the card is supported (the system identifies the driver).  Give this site a glance and it may help:  [http://www.dedoimedo.com/computers/linux-hardware-troubleshooting.html](http://www.dedoimedo.com/computers/linux-hardware-troubleshooting.html)

Keep in mind that some things have changed.  For example, the site mentions /var/log/messages which isn't available in your version - you'll wnt to check /var/log/syslog instead.  I'd begin by grepping for key words from that log.

Thank you again. That tutorial certainly is interesting and useful. At this point I have a suspicion that it's a software fault because the computer is quite new and a similar issue has not occurred under windoze yet.

Unfortunately an upgrading of ALSA according to [this]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS") has not rectified the issue either.

---

### Post by faust99 on 2013-04-23
An update and flash of the BIOS turned out to be the solution.

---

### Post by Diametric on 2013-04-23
Great!  Glad you got it fixed.  How did you reach that conclusion/resolution?

---

### Post by faust99 on 2013-04-23
> **Diametric said:**
> Great!  Glad you got it fixed.  How did you reach that conclusion/resolution?

I found a bug report in which somebody mentioned that upgrading their bios worked and it reminded me that I reset my BIOS to factory settings a few days ago; which coincided with the beginning of my problem. So I downloaded a BIOS upgrade through windoze and no problem since.

---

