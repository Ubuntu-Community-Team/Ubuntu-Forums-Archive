---
title: "How to fix `ubi-timezone failed with exit code 1` error?"
date: 2013-02-04
forum: General Help
---

### Post by mkbolivian1 on 2013-02-04
I'm trying to install Lubuntu 12.10 on a Fujitsu Lifebook C-2220 (Pentium 4 - 2.40GHz, 215MB ram).

I'm installing from a USB drive. I reach the "Where are you?" page, click continue, and get the error ubi-timezone failed with exit code 1.
 Any suggestions?

---

### Post by mkbolivian1 on 2013-02-04
Another attempt, one of a great many, to install yielded this error:
ubiquity.components.partman_commit failed with exit code 1.
what am I doing wrong here?

---

### Post by mkbolivian1 on 2013-02-05
Would installing an older version help? Or would an older version just make it less likely to be compatible? I was able to install puppy linux with very little issue, but for whatever reason lubuntu just isn't working.

---

### Post by mkbolivian1 on 2013-02-05
Ok, I built a new bootable thumb drive with the alternate installer, and tried that, and it hung up after configuring the network. 
Next I tried running a command line install, and it seems to be working so far, fingers crossed.

---

### Post by mkbolivian1 on 2013-02-05
Right, so I got through the command line install, and selected the option to install the lubuntu desktop, the install proceeded smoothly, grub install, etc... I reboot when prompted to do so, and this pops up: 

Ubuntu 12.10 ubuntu tty1

ubuntu login: [   13.808043] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   13.808142] ali mixer 1 creating error.
[   25.192071] ata3: SRST failed (errno=-16)
[   35.204071] ata3: SRST failed (errno=-16)
[   70.248073] ata3: SRST failed (errno=-16)
[   75.276087] ata3: SRST failed (errno=-16)
[   75.287144] ata3: reset failed, giving up

I don't know what any of that means.

---

### Post by dino99 on 2013-02-05
about SRST:
its a hdd issue :
 how is it formated ? (ext3 ?)
 how is the hdd bios set ? (maybe try something else in the bios settings)

about the sound, watch the latest post:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/439156](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/439156)

---

### Post by mkbolivian1 on 2013-02-05
During the command line install I used the "guided" partition option, which I believe either formats as ext3 or 4. Used the whole HD. I'm no sure what you mean about trying a different bios setting, what would I be trying to change in the bios? I'll check that link about the sound out. Thanks!

---

### Post by mkbolivian1 on 2013-02-05
Booted into puppy and checked gparted : 
it is ext4...
/dev/sda1 - ext4 
/dev/sda2 - extended
   /dev/sda5 - linux swap

I am able to see the hd from here. Is there a way I can fix this issue from inside puppy? 
I'm not sure what needs to be done

---

### Post by mkbolivian1 on 2013-02-05
If you want to try and speculate over why this wasn't working, feel free. I ran the install again, using the alternate installer again, and it failed. I thought, what the heck, I'll give it another go. Install ran perfectly, os booted up, everything is peachy. Who knows why... But I'm happy now

---

