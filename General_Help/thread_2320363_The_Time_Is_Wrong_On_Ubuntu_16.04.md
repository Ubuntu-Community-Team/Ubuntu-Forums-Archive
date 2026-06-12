---
title: "The Time Is Wrong On Ubuntu 16.04"
date: 2016-04-13
forum: General Help
---

### Post by Rocky_Bennett on 2016-04-13
Hello All,
The time that is displayed on the top left hand part of the screen is wrong on my system, right now it indicates 11:02 PM on Tuesday when in reality it is 5:02 AM on Wednesday. I went into the settings and checked there and everything looks good, the time is set to automatically update from the Internet and the time zone looks right.  Also I completely updated the system and this still has not changed the time. What could be causing this, it just started yesterday? How can I correct it?

Rocky Bennett

---

### Post by mastablasta on 2016-04-13
are you dual booting with windows?

what does ```
date
``` command show?

---

### Post by grahammechanical on 2016-04-13
What time does the UEFI/BIOS setting utility say? Losing time can be an indication that the Real Time Clock (RTC) battery (CMOS) is not holding a charge and needs replacing. If you start getting messages from the motherboard when you switch on that you need to enter the UEFI/BIOS to set the time & other stuff, then replace that battery.

Regards.

---

### Post by vasa1 on 2016-04-13
Maybe relevant:
[http://ubuntuforums.org/showthread.php?t=2320336&p=13469560#post13469560](http://ubuntuforums.org/showthread.php?t=2320336&p=13469560#post13469560)
and
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566465](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566465)

---

### Post by Rocky_Bennett on 2016-04-13
Yes I am multi-booting with Windows 10, but this problem just started yesterday. I just di the date command;

rocky@rocky-All-Series:~$ date
Wed Apr 13 07:07:50 MDT 2016
rocky@rocky-All-Series:~$ 




which is 3 hours earlier than it is in real life. Like I said, I am multi-booting and this problem has not effected any of my other Linux installations.

I'm still working on it.

---

### Post by Rocky_Bennett on 2016-04-13
> **grahammechanical said:**
> What time does the UEFI/BIOS setting utility say? Losing time can be an indication that the Real Time Clock (RTC) battery (CMOS) is not holding a charge and needs replacing. If you start getting messages from the motherboard when you switch on that you need to enter the UEFI/BIOS to set the time & other stuff, then replace that battery.

Regards.



How do I check the UEFI time?

---

### Post by Impavidus on 2016-04-13
> **Rocky_Bennett said:**
> Hello All,
The time that is displayed on the top left hand part of the screen is wrong on my system, right now it indicates 11:02 PM on Tuesday when in reality it is 5:02 AM on Wednesday. I went into the settings and checked there and everything looks good, the time is set to automatically update from the Internet and the time zone looks right.  Also I completely updated the system and this still has not changed the time. What could be causing this, it just started yesterday? How can I correct it?

Rocky Bennett

So the clock is exactly 6 hours late and you're in New Mexico in time zone UTC-6? Sounds like a timezone mixup. What is in the file /etc/default/rcS?```
cat /etc/default/rcS
```It may state **UTC=yes** where on most Windows dual booting machines it should be **UTC=no**.

E: Hmm, I shouldn't click on a thread, pause the computer, watch a race, have dinner, type a reply and then forget the thread could be a couple of posts further on. Yet, I think it's still relevant.

---

### Post by Rocky_Bennett on 2016-04-13
Actually this time that I started up my computer it was approx. 2 and a half hours early. This morning when I turned on the computer it was approx. 5 hours and 20 minutes off. I guess it depends on how long I have been off the computer.

---

### Post by Rocky_Bennett on 2016-04-13
rocky@rocky-All-Series:~$ cat /etc/default/rcS
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
#TMPTIME=0

# spawn sulogin during boot, continue normal boot if not used in 30 seconds
#SULOGIN=no

# do not allow users to log in until the boot has completed
#DELAYLOGIN=no

# be more verbose during the boot process
#VERBOSE=no

# automatically repair filesystems with inconsistencies during boot
#FSCKFIX=no
rocky@rocky-All-Series:~$

---

### Post by Rocky_Bennett on 2016-04-13
I think that this problem is related to Grub.

---

### Post by $yl9pAR%t on 2016-04-13
This works for me:

[http://ubuntuforums.org/showthread.php?t=2319437&p=13466688#post13466688](http://ubuntuforums.org/showthread.php?t=2319437&p=13466688#post13466688)

---

### Post by mastablasta on 2016-04-14
> **Rocky_Bennett said:**
> Yes I am multi-booting with Windows 10, but this problem just started yesterday. I just di the date command;

.

by default Windows and Linux get their time in a different way. mine is contsantly jumping in Windows to another time andhtne getting repaired and then in Linux and then repaired there...

---

### Post by Rocky_Bennett on 2016-04-14
I'm afraid that this problem is so random that you might be correct mastablasta. The time in Ubuntu 16.04 could be anywhere from 35 minutes off up to 14 hours off when I first open it up but none of my other installed Linux systems is experiencing this right now. I think that this problem is related to Grub because the problem began about the same time that I removed a copy of Kubuntu 15.10 from a partition on a different drive. When I did that my entire Grub menu changed and now looks real weird. 

I am exploring all options and I will report back.

---

### Post by Frogs Hair on 2016-04-14
I found a post that suggested re-configuring the Network Time Protocol( ntp ) package. When I ran the command I found  ntp wasn't installed. Since installing ntp the time in Ubuntu and Windows have been syncing properly at boot. 

The time problem started in the last three days and I don't know if the ntp package was removed accidentally  or even if it is supposed to be installed by default.  

[http://ubuntuforums.org/showthread.php?t=2320336](http://ubuntuforums.org/showthread.php?t=2320336)

---

### Post by haplorrhine on 2016-04-14
An apparmor presenter noted that an attacker could still change the time via the browser despite its confinement.

---

### Post by Rocky_Bennett on 2016-04-14
> **Frogs Hair said:**
> I found a post that suggested re-configuring the Network Time Protocol( ntp ) package. When I ran the command I found  ntp wasn't installed. Since installing ntp the time in Ubuntu and Windows have been syncing properly at boot. 

The time problem started in the last three days and I don't if the ntp package was removed accidentally  or even if it is supposed to be installed by default.  

[http://ubuntuforums.org/showthread.php?t=2320336](http://ubuntuforums.org/showthread.php?t=2320336)



Thanks for the link. For some reason an update recently must have removed my NTP package, so I used those links first to install and then to configure the NTP package. The time set instantly to the correct time.

---

### Post by teafx on 2016-04-15
> **Rocky_Bennett said:**
> Thanks for the link. For some reason an update recently must have removed my NTP package, so I used those links first to install and then to configure the NTP package. The time set instantly to the correct time.

I've already had the time go off. You actually don't need to do anything an in some days the time will eventually go back on (I just set it for another time zone to give correct time). Whatever is happening if its this or something else, its not the normal are you dual booting, etc advice. (I actually already have Windows set to use the correct time settings for linux compat for instance and dual booting into 16.04 works until after a specific update).

BTW, I just updated minutes ago and the time is off again and I dual booted before than and the time was correct.

---

### Post by bswarm2 on 2016-04-16
What worked for me on dual boot computers...
Go into the bios and set the time to GMT/UTC, then set via time settings your time zone in each OS, in my case it was -8 for Pacific USA.

---

### Post by gratzie on 2016-04-19
first go to clock settings and change from "Automatically" to "Manually"

then run this commands in terminal:



ntpdate -s ntp.ubuntu.com




sudo dpkg-reconfigure ntp


note: if ntp is not installed you need to run this command in terminal:
sudo apt-get install ntp

good luck!

eugen b

---

### Post by suruchi on 2016-11-24
To set UTC: 
sudo timedatectl set-timezone UTC
This worked for me in Ubuntu 16.04.

---

