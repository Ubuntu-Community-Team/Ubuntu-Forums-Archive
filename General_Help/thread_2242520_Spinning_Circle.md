---
title: "Spinning Circle"
date: 2014-09-02
forum: General Help
---

### Post by bigpappajohn1984 on 2014-09-02
I installed Ubuntu had it up and running things were going great.  I did a reboot and now I get the Ubuntu Purple Screen and then it goes to a black screen with a white circle spinning with the dots in the center of the circle going around showing progress.  And it sits on this screen, for hours.  

How do I get around this so that I can use Ubuntu again?

EDIT -----
I am thinking I should just do a fresh install since I hadn't passed any data over to the new install yet.  BUT I don't want to go through set-up only to discover that I am still hung at the circle.

---

### Post by sotiris2 on 2014-09-02
Some more details. You installed ubuntu run it for a bit and on first reboot you got a problem? If so did you make any updates? When you boot if you hold shift (or if you have a dual boot with windows) you will get a menu to select which operating system to boot. It will have an Advanced options for Ubuntu entry. In that you will find possibly multiple ubuntu kernel versions as well as recovery modes. Try first a non-recovery older kernel and if you can't get any to work try a recovery mode as well.

---

### Post by bigpappajohn1984 on 2014-09-02
I tried to install - partial upgrade or partial package or maybe it said broken package, but when I clicked okay It just said it was preparing then the screen disappeared, so I am not sure if that actually took place or not.

When I boot holding shift I see this
```

GNU GRUB version 1.98-1ubuntu13


Ubuntu, with Linux 2.6.32-38- generic
Ubuntu, with Linux 2.6.32-38- generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

```

EDIT --
If I try to boot the recover mode it will hang up showing this message
```

[          8.741025] Console: switching to colour frame buffer device 80x30

```

---

### Post by sotiris2 on 2014-09-02
So you installed your system. It booted okay. It asked for some updates and you let it do them. It told you something about broken packages and since then you can't boot. 

Do you still have the cd/usb you installed from? You can use it to try and fix packages with it. There is a guide [here](https://help.ubuntu.com/community/LiveCdRecovery). The Update failure section is the one for your problem. Some notes however.
You will have to pick "try ubuntu" not install to get to the point you can follow the guide.

Also while the guide says ctrl+alt+f1 I suggest you use ctrl+alt+t (or open terminal from the dash). The reason is that F1 will get you a full screen console with nothing else on it. Ctrl+alt+t will open a console on a window, so you can see the tutorial on firefox (and actually copy and paste the commands to avoid errors) and ask for clarification in the forum at the same time.

Also look at the section finding your root partition especially if this a dual boot system. The commands will probably fail if it's say a windows partition without really damaging it but better to be certain.

Also what is your graphics card?

---

### Post by bigpappajohn1984 on 2014-09-02
Thank you for that information.  I unfortunately do not have the installation CD here with me, but when I get back to it, I will try the guide you linked to. This is a single boot PC running ONLY this Ubuntu installation.

---

### Post by bigpappajohn1984 on 2014-09-02
I set my PC in the BIOS to boot from CD - but it will not boot from my DVD drive.  I get an error of Media Test Failure, check cable - then it boots straight up from the Hard Drive.  No Luck Booting from DVD :(

---

### Post by sotiris2 on 2014-09-02
Are you sure you didn't set it to boot from network? I can't see why it would ask you to check cable. Is this the same dvd you used to install it? 
Your problem can't in any way remove your ability to boot from dvd etc so since you presumably could before (to install ubuntu in the 1st place) you still can. Maybe you made a mistake due to nervousness?

---

### Post by bigpappajohn1984 on 2014-09-02
Yes this is the PC I used to install Ubuntu with.  I just double checked all my options. If I press F12 during Start-Up the Boot Menu lists (in this order) -- if I check the BIOS Boot Order same order of progression.
ODD
USB
LAN
HDD

---

### Post by sotiris2 on 2014-09-02
Maybe the dvd got scratched or something? Can you try making another one? Maybe making a usb one?

---

### Post by bigpappajohn1984 on 2014-09-02
Maybe disc is scratched - I am attempting to use a USB one as we speak and will update as soon as I can.

---

### Post by bigpappajohn1984 on 2014-09-02
Boom!  I (for the 1st time) used a flash drive to install Linux - since I didn't have any data other than install files on the hard drive, I just did a fresh format from the flash drive and flashed [h=2]Ubuntu 14.04.1 LTS[/h]

---

### Post by Elfy on 2014-09-02
Partial upgrades are never a good idea ;)

[https://help.ubuntu.com/community/partialupgrade](https://help.ubuntu.com/community/partialupgrade)

---

### Post by sotiris2 on 2014-09-02
Ah cool I guess.

---

