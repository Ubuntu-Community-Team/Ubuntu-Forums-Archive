---
title: "HDMI+sound on a Gigabyte GA-G33M-S2H"
date: 2007-10-17
forum: General Help
---

### Post by Eklöf on 2007-10-17
Anyone have this card and know if Ubuntu supports sound through the HDMI connection?

Thinking of using this in a HTPC setup running XBMC for linux or MythTV.

---

### Post by romandog on 2007-10-18
I have this board, and it works great--except I'm having trouble with the dvi connection with Gutsy.  The screen is completely blank (Using dvi->hdmi converter).  If you have luck with the HDMI connection, i'll switch to that.  Keep us posted; I'll do the same.

---

### Post by morgwon on 2007-11-17
from my understanding sound through HDMI on motherboards doesn't work quite like consumer products. I think the only way to get sound is to use the onboard sound. I think this is the case in windows as well. I plan on getting this board soon for a mythtv setup so hopefully you guys can make some headway in the meantime.

---

### Post by tecfreak on 2007-11-22
Hello,

the GA-G33M-S2H  ist the best mainboard for a htpc i could find. 

Does anybody know if the g33 chipset and its integrated graphic chip is supported by the current linux kernel or by some 3rd party modules?
So i guess the graphic chip isnt supported by xvmc. Correct me if i am wrong.

Is the Realtek AL889A sound supported by alsa? Couldnt find anything on the alsa website.



PS: sorry 4 my bad english.

---

### Post by tecfreak on 2007-11-22
Strike!

[http://gentoo-wiki.com/HARDWARE_Intel_G33,_Q35,_and_Q33_Chipsets](http://gentoo-wiki.com/HARDWARE_Intel_G33,_Q35,_and_Q33_Chipsets)

---

### Post by hmistry on 2007-11-28
Hi tecfreak,
did you manage to get this working?
If so, how did you get it going?
Thanks

---

### Post by tecfreak on 2007-11-28
I have bought an other Mainboard, the GA-P35-DS3L. The onboard graphic soultion wasnt good enough for my needs.

I think all u need ist a new kernel >2.6.23.1 but i can't help u with that.

Sorry, but you have to get i working yourself.

---

### Post by falstaff on 2008-02-02
Hello,

I have the Gigabyte GA-G33M-S2H and running Ubuntu Hardy on it! HDMI graphics output works like a charm out of the box (in Fulll-HD, 50Hz). Im trying to get Sound over HDMI to work, but no luck so far! Seems to be difficult! At the moment im using s/pdif, and this works with dd and dts!

Anybody any idea to get the sound over hdmi working? Anyway, I'll ke you informed when i get the sound working!

bye
falstaff

---

### Post by falstaff on 2008-02-03
Hello,

I installed today a windows xp installation on this board. Installed all drivers from the motherboard's website (gigabyte.com.tw). On windows xp i can change the sound output to HDMI, witch then works fine (with dts/ac3). The sounddriver for hdmi was *not* bundled with the realteak audio driver! It was part of the graphic driver from intel! The PCI ID is 1095:1392. I didn't found any driver for this device for linux on the web. The device is called "Intel(R) High Definition Audio HDMI"...


Anyone any idea?

Bye
falstaff

---

### Post by falstaff on 2008-02-04
Hello again!

Good news, i brougth sound over hdmi to work! I found the solution on the alsa bugtracking system: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3654"). I downloaded the source of ALSA 1.0.16rc2, patched the source with the patchfile from the bugtracking system (which I also attached here) after unmuting it in alsamixer, its working fine now! I hope it will make it in hardy also, i found a bug about this on launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/160277]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/160277").

bye
falstaff

---

### Post by allram on 2008-06-12
Its working realy good!!!!
Codecs that working, DTS,Dolby Digital , usual PCM,, everything is working,
My way to get this audio working over hdmi with GA-G33M-S2H:
Download this package from alsa homapage:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17rc1.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.17rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.17rc1.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.17rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.17rc1.tar.bz2)

before compile this packages, remove the old ones from your distribution.
then compile and install these packages.

when done you mabe need to reboot the system to load the new alsa modules.
Then you go ahead with the alsaconf command (as root).
Then enter the alsamixer and you will see three IEC... ,, 
The 1st one and second one of IEC.. shoud be marked as unmuted,,,
Now you have enabled the audio over hdmi.
To passthrou audio over hdmi with multimedia programs:
In mplayer you choose hw:0,3 in preference/audio
In audacious you choose hw:0,3
some program locate hdmi to hw:0,2
Generely in the most program to use hdmi port is hw:0,3

This should work.
I use slackware 12.1 and works very well!

---

### Post by allram on 2008-06-18
I have problem to use audio through hdmi on Mythtv.
In mplayer I use "-ao alsa:device=hw=0.3" and that works!
When I use same ("alsa:device=hw=0.3") in mythtv, it happens nothing, dont hear a sound of the tv.
Should I write something else in mythtv?

---

