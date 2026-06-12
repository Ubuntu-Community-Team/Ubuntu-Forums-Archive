---
title: "AMD catalyst control center for AMD Radeon HD 6850, Ubuntu 14.04.4 LTS"
date: 2016-02-22
forum: General Help
---

### Post by jaap5 on 2016-02-22
Dear forum,

My Linux skills are unfortunately very limited: I'm good at following instructions, but it's difficult to "think out of the box".

Anyway,
I recently bought a new game on Steam (Firewatch), and as the performance is currently subpar (can't play the game when I get to the "open world"), it was recommended to me to install amd catalyst control center for my AMD Radeon HD 6850 graphical card.
I found a great tutorial ([http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)).
The Trusty installation guide ([http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide)) works as a charm, no errors at all, that is: until I reboot. Then my screen is black, and unresponsive, and the only way back is the "Restart Even If System Utterly Broken" trick (or a hard reboot).
In the recovery mode I then purge the new fglrx installation, and I do get my old settings back.
I've tried numerous ways to install fglrx (from the above guide: both the stable and beta releases, [https://www.youtube.com/watch?v=evqpassbyqA](https://www.youtube.com/watch?v=evqpassbyqA), [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD), etc.).
Unfortunately, nothing works, and I have to purge fglrx every single time to get the old settings back.
I also tried to generate a new /etc/X11/xorg.conf file (as my HD 6850 is apparently "unsupported", but the trick on the wiki claims it could work).
I also tried to force to use of the new xorg.conf.
As I stated previously, it is for me difficult to improvise and come up with an alternative solution. The point by point instructions I found online do not have the required results.
I would greatly appreciate if someone could point me to the correct solution with some helpful suggestions.

Thank you so much!


Specs:
Ubuntu 14.04.4 LTS
Memory 11.7 GiB
Intel Core 17-2670QM CPU@ 2.20GHz x8
Graphics: AMD Radeon HD 6850
OS: 64-bit
DisK 120 GB

---

### Post by QIII on 2016-02-22
Hello!

Are you doing

```
sudo amdconfig --initial
```

after installing and before rebooting?

Is this a laptop or a desktop?  

If a laptop, is it muxed or mux-less hybrid graphics
If a desktop, have you used your BIOS/UEFI menu to set your PCIe GPU as primary?

---

### Post by jaap5 on 2016-02-22
Hi Qlll,

thanks for the help.
I used 
sudo amdconfig --initial -f
But it was not recognized automatically, therefore I edited the device section of xorg.conf to:
Section "Device"
 Identifier "ATI radeon 6850"
 Driver "fglrx"
EndSection

I'm using a laptop (Acer Aspire). How can I check if it is muxed or mux-less hybrid (is there a command)?
According to the wiki listed above, it is probably mux-less. What should be my next step?


Thanks!!

---

### Post by QIII on 2016-02-22
To find out if it it muxed (multiplexed through the Intel graphics) one would need to know the exact model number and possibly serial number to do some research.  There may not be any way to check via any available command.

Unfortunately the OEMs have made sure that muxed systems will work with Windows, but Linux got short shrift.

---

### Post by jaap5 on 2016-02-22
I just found this thread from someone with the same problem (and same settings, I also have an Aspire 8950 with a AMD radeon HD 6850M) [http://askubuntu.com/questions/575659/proprietary-drivers-dont-work-for-my-amd-6850m](http://askubuntu.com/questions/575659/proprietary-drivers-dont-work-for-my-amd-6850m) 
Seems that no solution exists...... :(

---

