---
title: "Scratchy Audio in Left Speaker"
date: 2007-08-17
forum: General Help
---

### Post by veagles on 2007-08-17
I have an Intel D945GNT motherboard with the following audio device:
 Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
I get scratchy audio in my left speader when i play music or videos,  I tried different players and output modules but issue remains..

Whats wrong?

---

### Post by dickohead on 2007-08-17
Have you tried other speakers? Maybe try some headphones too.

If you're using 3D audio (Dobly 5.1 etc) you could check to see if your speakers are assigned the correct position. Maybe it's been assigned as a sub-woofer when it's not?

The cable that plugs into your machine could also be faulty, make sure it is firmly plugged in.

Once you've checked the physical posiblities, then start on the software!

:D

---

### Post by veagles on 2007-08-17
My 2.1 Speakers work fine in windows so nothing wrong with the cables,

I have the same issue on headphones too..

---

### Post by Yarbo on 2007-10-31
I have the exact same motherboard, and same issue.

Only on the left channel on and only in linux.

---

### Post by diogeno on 2008-03-01
I have the same Intel motherboard and had the exact same problem.

I tried to fix it when I initially installed Ubuntu 4 months ago. I read the Ubuntu Hda-intel howto, and followed the instructions for building a fresh copy of alsa for hda-intel. This worked, but it didn't last. The audio would sound perfect until I turned off or rebooted the computer. I couldn't figure it out, so I lived with crappy sound until last week when I decided to do something about it. Some forums recommended changing settings to /etc/modprobe.d/ files (alsa-base, options, etc...) but none of those worked... So I decided to completely remove all the modprobe.d sound settings files and re-install alsa. I moved (don't delete) 'alsa-base' and 'sound' out of modprobe.d and then refollowed the Hda-intel howto. Then I ran 'alsaconf'. Then I rebooted.

It worked! And it has continued to work after reboots.

Steps:
1. sudo mkdir ~/backup
2. cd /etc/modprobe.d/
3. sudo mv alsa-base ~/backup
4. sudo mv sound ~/backup
5. Follow the [Ubuntu Hda Howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") instructions. I didn't do any of the codec stuff. Just the top set of instructions to install the 3 alsa components.
6. sudo alsaconf
7. reboot

---

